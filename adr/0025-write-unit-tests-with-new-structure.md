# New unit test structure

* Status: accepted
* Deciders: iOS Team
* Date: 2022-06-28

## Context

With the new unit test structure, we will be able to write more assertions with less code.

## Decision

It is required to use the new structure for newly created test classes.
Test class must conform to BaseTestCaseInterface. Mock classes must conform to MockAssertable.
Mocks must be generated like this.

    1- Swift Mock Generator -> Generate stub
    2- Swity -> Generate Mock

## Consequences

  * Pull requests will be rejected if newly created test class does not write with new unit test structure.
  * Tests written with the new test structure will 100% check all mocks.
  * Unit tests run time will be reduced.
