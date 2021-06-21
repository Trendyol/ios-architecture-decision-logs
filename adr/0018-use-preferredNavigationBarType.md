# Preferred Navigation Bar Types

* Status: accepted
* Deciders: iOS Team
* Date: 2021-06-21

## Context

The aim is to cover doubled or none navigation bar issues with deeplink routings.

## Decision

Should use `BaseViewController` or `TYRootViewController` and manage it there, and override if need your preferred `NavigationBarType`

## Example Usage

`.native` case is directly selected on `BaseViewController`, so if you are inheriting from `BaseVC` and using `native bar`, you don't need to do anything


On `TYRootViewController`, `.none` case is selected directly as override, so if you are inheriting from `TYRootViewController` and you are going to use `TYNavigationBar`, you don't need to do anything.


Although you can get inherit, if you want to use other than usage in inheritance, you need to override

`native >` shows native navigation bar
`none >`hides the native navigation bar
`notDetermined >` Doesn't mess with meat and milk, it doesn't do anything (we use it to select in child controllers)

usage like:

`override var preferredNavigationBarType: NavigationBarType { .native }`


## Consequences

* Duplicated or dissappearing navigation bars will be fixed on deeplink navigations.
