# Smoke tests maintenance is required for every PR

* Status: accepted
* Deciders: iOS Team
* Date: 2022-06-07

## Context

Smoke tests find UI problems and guard UI test architecture early in the development cycle.

## Decision

Covering all elements inside the smoke tests is required when new element is added or change is made.
Adding smoke tests is required when new page is created.

## Consequences

  * Pull requests will be rejected if does not covered by smoke tests.
  * Updated smoke tests will increase confidence in our pipeline.
  * Regression tests will always have the necessary infrastructure.
