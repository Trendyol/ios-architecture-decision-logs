# Handling Service Call Enabled Kill-Switches and Macro Usage

* Status: accepted
* Deciders: iOS Team
* Date: 2026-08-28

## Context

In Trendyol iOS, backend endpoints can be remotely controlled or turned off via remote configuration kill-switches (conventionally formatted as `{BaseUrlKey}_ServiceCallEnabled`).

Previously:
- When an endpoint's kill-switch was disabled, the network layer threw or returned a generic failure (`APIClientError.serviceCallDisabled` / `NewAPIClientError.serviceCallDisabled`).
- Presenters and ViewModels catching errors in generic failure blocks often presented error alerts (e.g., "Bir hata oluştu", generic error popups) to users.
- When backend operations intentionally disabled a non-critical feature (e.g., browsing history slider, top sponsored ads, influencer suggestions), users experienced disruptive error popups instead of a clean, graceful fallback or empty state.
- In macro-generated endpoint configurations (`#baseURLEndpoint` / `#baseURLAPIRequest`), there was no clear standard for documenting when and why an endpoint should opt out of default kill-switch generation.

## Decision

### 1. Opt-in 3-Way Result Pattern (`requestWithServiceCallEnabled`)

We introduce dedicated 3-case enum types that separate intentional service disabling from actual network/system errors:

- **Legacy Network (`NetworkManager` / VIPER)**:
  ```swift
  public enum NetworkRequestResult<Response: Decodable> {
      case success(Response)
      case serviceCallDisabled(configKey: String)
      case failure(APIClientError)
  }
  ```

- **New Network (`NewNetworkClient` / SwiftUI MVVM)**:
  ```swift
  public enum NewNetworkRequestResult<Response: Decodable> {
      case success(Response)
      case serviceCallDisabled(configKey: String)
      case failure(NewAPIClientError)
  }
  ```

When calling an endpoint that may be disabled via remote config and should degrade gracefully without showing error UI, callers must use:
- **Legacy Network**: `networkManager.requestWithServiceCallEnabled(...)`
- **New Network**: `networkClient.requestWithServiceCallEnabled(...)`

### 2. Switch-Case Handling in Presenters and ViewModels

Every callsite using `requestWithServiceCallEnabled` must exhaustively handle all 3 cases:

#### In VIPER Presenters (Legacy Network):
```swift
func handleCategoryTopRankingListResponse(_ result: CategoryTopRankingListResult) {
    view?.hideLoading()
    switch result {
    case .success(let response):
        self.response = response
        view?.reloadCollectionView()
    case .serviceCallDisabled:
        // Graceful degradation: reset state, hide section/loading, DO NOT show alert
        applyServiceCallDisabledEmptyState()
    case .failure(let error):
        // Actual failure: show error alert / toast
        router.showAlert(message: error.message, action: .pop(true))
    }
}
```

#### In SwiftUI ViewModels (New Network):
```swift
@MainActor
func fetchData() async {
    router.showLoading()
    defer { router.hideLoading() }

    switch await networkClient.requestWithServiceCallEnabled(FetchMyDataRequest()) {
    case .success(let response):
        self.items = response.items
    case .serviceCallDisabled:
        // Silent fallback: clear items or set empty state, NO error alert
        self.items = []
    case .failure(let error):
        router.showAlert(message: error.message)
    }
}
```

### 3. Macro Support and Opting Out with `.disabled`

`#baseURLEndpoint` and `#baseURLAPIRequest` macros automatically derive `{BaseUrlKey}_ServiceCallEnabled` for `.config(...)` definitions.

When an endpoint intentionally does NOT need a service call kill-switch (e.g. mandatory core service, composite operation, full service URL, or handled by another parent gate), it must explicitly declare why using `serviceCallEnableSupport: .disabled("<Reason>")`:

#### In `#baseURLEndpoint` (Endpoint enums):
```swift
enum FavoriteEndpointItem: Endpoint {
    case fetchFavoritesTabs
    case addToFavoriteList

    #baseURLEndpoint { (item: Self) in
        switch item {
        case .fetchFavoritesTabs:
            // Generates FavoriteTabsFetchBaseUrl_ServiceCallEnabled
            .config("FavoriteTabsFetchBaseUrl", defaultValue: APIURL.Trendyol.favoriteTabsFetchBaseUrl.baseURL)

        case .addToFavoriteList:
            // Explicitly disables service call check with reason
            .config("FavoriteAddBaseUrl",
                    defaultValue: APIURL.Trendyol.favoriteAddBaseUrl.baseURL,
                    serviceCallEnableSupport: .disabled("FavoriteOperationsCalls"))
        }
    }
}
```

#### In `#baseURLAPIRequest` (NewAPIRequest structs):
```swift
struct FetchCollectableProductsRequest: NewAPIRequest {
    #baseURLAPIRequest {
        .config("CollectionsApiBaseUrlRead",
                defaultValue: APIURL.Trendyol.collectionsBaseUrlReadNew.baseURL,
                serviceCallEnableSupport: .disabled("ViewCollectionsCalls"))
    }
    // ...
}
```

This aligns with the `service_call_config_required` SwiftLint rule, ensuring every endpoint either provides a kill-switch config key or documents its disabled reason.

### 4. Unit Testing Requirements

Presenters and ViewModels handling `requestWithServiceCallEnabled` must include dedicated unit tests verifying that `.serviceCallDisabled` does not trigger error alerts and properly updates view state:

```swift
func test_handleBrowsingHistoryResult_ServiceCallDisabled_DoesNotShowAlertAndHidesSection() {
    invokedNothing()

    presenter.handleBrowsingHistoryResult(.serviceCallDisabled(configKey: "testServiceCallEnabled"))

    // Verify view reloaded or section hidden, and router.showAlert is NOT invoked
    mockView.assertInvokes([.reloadCollectionView])
    invokedNothing(excepts: [mockView])
}
```

## Consequences

### Positive
- **No False-Alarm Alerts**: Users never see error popups when services are intentionally turned off by remote config.
- **Consistent API Pattern**: Both VIPER (UIKit) and MVVM (SwiftUI) share the same 3-case result mental model.
- **Declarative & Enforced**: `#baseURLEndpoint` and `#baseURLAPIRequest` enforce clear ownership of kill-switch keys or explicit `.disabled` reasons.
- **Testable**: Clean separation between `.serviceCallDisabled` and `.failure` enables direct assertions on kill-switch behavior.

### Negative
- Callers requiring graceful degradation must opt in by using `requestWithServiceCallEnabled` instead of standard `request`.
- Existing endpoints catching generic errors need refactoring to prevent error alerts when kill-switched.
