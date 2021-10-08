# Theme manager should injected in common places

* Status: accepted
* Deciders: iOS Team
* Date: 2021-10-5

## Context

Each channel should be able to give its own theme to the common views. We need to follow common rules about theme in common places.

## Decision

For common views, theme manager should injected into the associated presenter.

## Consequences

Each channel will be able to use common views with its own theme.
