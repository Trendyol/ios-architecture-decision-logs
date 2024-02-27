# Call super.tearDown At the End of tearDown method.

* Status: accepted
* Deciders: iOS Team
* Date: 2023-27-02

## Context

There were discussions on code reviews about the position of `super.tearDown()`, [Apple's doc](https://developer.apple.com/documentation/xctest/xctestcase/set_up_and_tear_down_state_in_your_tests) reviewed and a decision made since we may want to run the unit tests in parallel in near feature.

## Decision

Call `super.tearDown()` at the end of the `tearDown` method:

```swift 
override func tearDown() {
    mockDefaultsInstance.assertions(name: "mockDefaultsInstance")
    mockDefaultsInstance = nil
    defaults = nil
    super.tearDown()
}
```

