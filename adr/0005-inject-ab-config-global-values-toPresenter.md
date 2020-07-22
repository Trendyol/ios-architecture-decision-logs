# Inject AB / Config / Global Values to Presenters For Testablity

* Status: accepted
* Deciders: iOS Team
* Date: 2020-07-21

## Context

We faced a problem that missing test cases on some presenters because of not injectable variables like ab tests, config or global values on presenters. So we want to cover all of these missings.

## Decision

We decided to inject this variables to related presenters from their constructors.

## Consequences

Injecting this variables to presenters from their constructors are giving us to more testable presenters. So we can tests all production code cases which is involving business logics.
