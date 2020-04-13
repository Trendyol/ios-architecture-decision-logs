# Every view which has logic inside should(must) have presenter

* Status: accepted
* Deciders: iOS Team
* Date: 2019-07-01

## Context

In Viper architecture, every view controller has its presenter. But when the topic comes to views or cells, they don't have presenter and view contains whole logic. So we wanted to move business logics to presenter & write unit test to presenter

## Decision

If views have business logic, they should(must) have presenter to keep them

## Consequences

Business logic will be separated & writing unit test will be possible
