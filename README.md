# Architectural Decision Records (ADR)

This log lists the architectural decisions for Trendyol iOS Project.

<!-- adrlog -- Regenerate the content by using "adr-log -i". You can install it via "npm install -g adr-log" -->

- [ADR-0000](adr/0000-use-xctest-for-unit-test.md) - Using XCTest for unit test instead of Quick/Nimble
- [ADR-0001](adr/0001-every-view-which-has-logic-inside-should(must)-have-presenter.md) - Every view which has logic inside should(must) have presenter
- [ADR-0002](adr/0002-use-view-model-on-necessary-place.md) - If it is necessary to manipulate the DTO models that the UI will use, the ViewModel class needs to be created
- [ADR-0003](adr/0003-dont-use-chain-delegate.md) - Don't Use Chain Delegate
- [ADR-0004](adr/0004-use-mock-generator.md) - Use Mock Generator
- [ADR-0005](adr/0005-inject-ab-config-global-values-toPresenter.md) - Inject AB, Config, Global Values to Presenters
- [ADR-0006](adr/0006-inject-parameters-asArguments-toPresenter.md) - Inject External Parameters as Arguments to Presenters
- [ADR-0007](adr/0007-presenter-casting-as-delegate.md) - Define any delegate on presenter interface to pass
- [ADR-0008](adr/0008-layering-modular-ios-application.md) - Layering Modular iOS Application
- [ADR-0009](adr/0009-layering-modular-ios-application-approach.md) - Layering Modular iOS Application Approach
- [ADR-0010](adr/0010-use-localizable-kit-for-localization.md) - Using Localizable Kit for Localization
- [ADR-0011](adr/0011-name-test-methods.md) - Naming Test Methods
- [ADR-0012](adr/0012-use-networkManager-for-network-requests.md) - Use networkManager for network requests
- [ADR-0013](adr/0013-unit-tests-required.md) - Unit Tests Required
- [ADR-0014](adr/0014-use-CoreTracker-for-trackingEvents.md) - Use coreTracker for tracking events
- [ADR-0015](adr/0015-use-UITestablePageProtocol-for-AccessibilityIdentifiers.md) - Use UITestablePage Interface for setting Accessibility Identifiers
- [ADR-0016](adr/0016-selector-function-unit-test.md) - Write selector function unit test
- [ADR-0017](adr/0017-theme-manager.md) - Theme Manager
- [ADR-0018](adr/0018-use-preferredNavigationBarType.md) - Use preferred navigation bar type
- [ADR-0019](adr/0019-naming-branch-name.md) - Naming branch name
- [ADR-0020](adr/0020-inject-theme-manager-for-common-places.md) - Inject theme manager for common places
- [ADR-0021](adr/0021-testing-only-one-function.md) - Testing only one function for each test case
- [ADR-0022](adr/0022-use-dependency-engine-to-register-and-access-modules.md) - Use Dependency Engine to Register and Access Modules
- [ADR-0023](adr/0023-common-config-name-definitions.md) - Common Config Name Definitions
- [ADR-0024](adr/0024-smoke-tests-maintainance-required.md) - Smoke tests maintenance is required for every PR
- [ADR-0025](adr/0025-write-unit-tests-with-new-structure.md) - Write unit tests with new structure
- [ADR-0026](adr/0026-write-unit-tests-with-core-tracker.md) - Use only CoreTracker for Event unit tests
- [ADR-0027](adr/0027-write-snapshot-tests-for-every-view-controller-and-deeplinks.md) - Write Snapshot Tests for every Deeplinks and View Controllers
- [ADR-0028](adr/0028-automatically-trim-trailing-whitespace.md) - Automatically trim trailing whitespace with Xcode setting
- [ADR-0029](adr/0029-tearDown-position.md) - Call super.tearDown() at the end of tearDown method 
<!-- adrlogstop -->

For new ADRs, please use [TrendyolAdrTemplate.md](TrendyolAdrTemplate.md) as basis.
