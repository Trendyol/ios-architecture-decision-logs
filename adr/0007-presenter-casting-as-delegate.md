# Presenter Interface Should Conform any Delegate to Use

* Status: accepted
* Deciders: iOS Team
* Date: 2020-08-07

## Context

We faced a problem that different implementations of presenter's conforming delegates

## Decision

We decided to add `var xxxxDelegate { get }` to `xxPresenterInterface` and passing this `presenter`  to any delegate like:  `(delegate: presenter.xxxxDelegate)` instead of  `(delegate: presenter as? xxxDelegate)` or `(delegate: presenter as! xxxDelegate)`

## Consequences

Passing presenters as conformed delegate will provide us to standardisation and good sign of code design.
