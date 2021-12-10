# Use Reflaction For Unit Tests

* Status: accepted
* Deciders: iOS Team
* Date:  2021-11-16

## Context

Testing for invoke or non-invoke in unit tests complicates test classes. We've had disagreements about testing non-invokes.

## Decision

We will use our mock classes with reflection. We will use this structure for non-invoke cases.

## Consequences

Unit tests will become output oriented, more manageable and shorter. For example,

For 'Given' case

<img width="617" alt="image" src="https://user-images.githubusercontent.com/33103753/145541555-9080bd0a-db09-4bb5-9674-8b0e301bfc05.png">

instead of

<img width="753" alt="image" src="https://user-images.githubusercontent.com/33103753/145541535-47883d03-2d7a-4082-96ac-4bfd6ae7156c.png">


*For more detailed information, read the wiki 'iOS Unit Test'.*
