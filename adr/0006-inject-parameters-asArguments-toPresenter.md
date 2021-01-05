# Inject Whole External Parameters as Arguments to Presenters

* Status: accepted
* Deciders: iOS Team
* Date: 2020-07-21

## Context

We faced a problem that adding new parameters to injecting presenters are getting much more longer for each time for all passing class.

## Decision

If we have 3 or more properties, we decided to create `XXArguments` class and inject this properties to this and just passing this arguments class to presenters.

## Consequences

Passing an arguments will provides us to minimum code line changings and avoiding pollution of codes for each modules.
