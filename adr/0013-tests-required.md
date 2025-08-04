# Test requirements for code changes and UI flows

* Status: accepted
* Deciders: iOS Team
* Date: 2021-01-04
* Updated: 2025-04-08

## Context

Testing finds problems early in the development cycle and ensures code quality across different layers.

## Decision

Adding tests is required based on the type of change:

### Unit Tests
- Required when changes are made to classes containing business logic (Helper, Manager, Presenter classes)
- Focus on testing logic, data transformation, and business rules

### UI Snapshot Tests  
- Required for UI components and flows that can be controlled with mocks
- Focus on important UI flows and visual consistency
- Use mocks to isolate UI behavior from business logic

### Smoke Tests
- Minimum one smoke test per screen
- Must verify identifier accessibility and basic screen functionality
- Ensure core user journeys are not broken

### Regression Tests
- Required for automating critical live flows that are manually tested
- Focus on end-to-end user scenarios that impact business metrics
- Convert manual test cases into automated regression tests

## Consequences

* Pull requests will be rejected if they don't include appropriate tests based on the change type
* Comprehensive test coverage across unit, UI, smoke, and regression tests will improve overall code quality
* Automated testing will reduce manual testing effort and catch issues earlier
