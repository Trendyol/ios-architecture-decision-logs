# Private selector function unit test

* Status: accepted
* Deciders: iOS team 
* Date: 2021-01-07

## Context

The aim is to cover presenter's private selector's functions and increase unit tests coverage results.

## Decision

Selector function unit test's should be called inside ```Thread.detachNewThreadSelector``` method.

## Consequences

* Unit tests coverage will be increase.
