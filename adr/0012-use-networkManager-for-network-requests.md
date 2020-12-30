# Using NetworkManager instead of Fetchable protocol

* Status: accepted
* Deciders: iOS Team
* Date: 2020-12-30

## Context

Our team created NetworkManager for network requests. For consistency we should replace and use NetworkManager instead of Fetchable protocol

## Decision

Every new interactors must use NetworkManager.

## Consequences

* All interactor methods will be in the same format.
* With NetworkManager handling endpoints are easy and simple
