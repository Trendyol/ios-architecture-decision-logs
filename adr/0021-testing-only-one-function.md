# Testing only one function for each test case

* Status: accepted
* Deciders: iOS Team
* Date: 2021-10-19

## Context

For some of the unit tests, we had to invoke multiple functions on presenters to prepare the state we need to test. E.g. we test `viewWillAppear` here:

```swift
func test_viewWillAppear_InvokesNecessaryMethods() {
        XCTAssertFalse(view.invokedShowLoading)
        XCTAssertFalse(interactor.invokedFetchSellerFollowingStatus)
        
        presenter.handleFetchOrderDetailResult(.success(response))
        presenter.viewWillDisappear()
        presenter.viewWillAppear()
        
        XCTAssertTrue(view.invokedShowLoading)
        XCTAssertTrue(interactor.invokedFetchSellerFollowingStatus)
}
```

This way we could not be sure whether view or interactor mocks invoked during `viewWillAppear`, `viewWillDisappear` or `handleFetchOrderDetailResult`. Also, if anyone move `view.showLoading()` call from `viewWillAppear` to `viewWillDisappear`, this test does not fail even though we have a bug.

## Decision

So it is better to move "preparation calls" above all of the assertions like this:

```swift
func test_viewWillAppear_InvokesNecessaryMethods() {
        presenter.handleFetchOrderDetailResult(.success(response))
        presenter.viewWillDisappear()
        
        XCTAssertFalse(view.invokedShowLoading)
        XCTAssertFalse(interactor.invokedFetchSellerFollowingStatus)
        
        presenter.viewWillAppear()
        
        XCTAssertTrue(view.invokedShowLoading)
        XCTAssertTrue(interactor.invokedFetchSellerFollowingStatus)
}
```
