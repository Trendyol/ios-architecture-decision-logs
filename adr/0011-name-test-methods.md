# Naming Convention for Test Methods

* Status: accepted
* Deciders: iOS Team
* Date: 2020-12-16

## Context

Name the test methods in a convenient form decided by the team.

## Decision

Methods should be named in such a way:  `test_methodToTest_Condition_Result` 
 - If we use default value in create method and define condition in function name it has to be suitable with create function call parameters
    **Preferred**:
   
     ```swift
      func test_methodToTest_ConditionOne_ConditionTwo_Result() {
       reCreate(conditionOne: true, conditionTwo: "title")
       ....

       presenter.methodToTest()
      }
     ```
    **Not Preferred**:
   
    ```swift
      func test_methodToTest_ConditionOne_ConditionTwo_Result() {
       ....

       presenter.methodToTest()
      }
     ```
    
## Consequences

All test methods will have names in the same format.
