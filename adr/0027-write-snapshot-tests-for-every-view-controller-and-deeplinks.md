# Snapshot Testing for Deeplinks and View Controllers

 * Status: Reviewed
 * Deciders: iOS Team
 * Date: 2023-03-23

 ## Context

 In our iOS project, we have deeplinks to open desired page. However, it's important to ensure that all deeplinks are working as expected to avoid any issues for our users. Also, we have some pages which can not access directly with deeplinks. We need to be sure, this pages UIs' showing as expected. Therefore, we have decided to implement snapshot testing for all deeplinks and all View Controllers in our project.

 ## Decision

 To enforce snapshot testing, we will follow the below guidelines:

 For every view controller and every deeplinks, we will create a separate snapshot test case.
 If any changes are made to the view controller or the deeplinks, the snapshot test case will be updated accordingly.
 We can define Snapshot Tests name with this ruleset: test_snap_Channel_Page()


 ## Consequences
 
 Snapshot testing for deeplinks and View Controllers will increase the overall quality of our app and improve the user experience.
 It will also help us to identify and fix any issues related to deeplinks.
 However, implementing snapshot testing for all deep link URLs will increase the amount of time and effort required for testing.
 It will also require additional resources for maintaining the snapshot test cases.
 Overall, we believe that the benefits of implementing snapshot testing for deeplinks outweigh the additional effort required for testing.

 ## Example Usage

 ```swift 
    func test_snap_Meal_MLBasketProductProductList() {
        setMockScenario(path: "basket", scenario: "test_snap_Meal_MLBasketProductProductList_Basket")
        setupWithDeeplink(deeplink: MLDeeplinks.basket)
        assertSnapshot(matching: prepareScreen(), as: .image)
    }
 ```
