# Inject All External Parameters as Arguments to Presenters and Routers

* Status: accepted
* Deciders: iOS Team
* Date: 2020-07-21

## Context

We faced a problem while injecting new parameters to presenters' initializer. The list of init params are getting much longer.

## Decision

Each module has it's own `createModule` or `setupModule` static method in its router. If we have 3 or more properties to be injected to any of these methods, we should create `XYZArguments` structure that contains those properties and pass the argument object to router.

We should also use the same arguments structure to pass to the initializer of the module's presenter.

## Consequences

Passing as an argument structure will provide us minimum code line changes and avoid pollution of codebase for each modules.
