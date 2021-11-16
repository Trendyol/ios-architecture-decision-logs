# Inject External Parameters as Arguments to Presenters and Routers

* Status: accepted
* Deciders: iOS Team
* Date: 2020-07-21

## Context

We faced a problem while injecting new parameters to presenters' initializer. The list of init params are getting much longer.

## Decision

Each module has it's own `createModule` or `setupModule` static method in its router. If we have 3 or more properties to be injected to any of these methods, we must create `XYZArguments` structure that contains those properties and pass the argument object to router.

We must also inject the same arguments variable to the presenters' initializer and use the variables inside through the arguments object, and not copy each of variables inside arguments to the presenter one by one.

**Note**: Argument object must only include the values to be injected from outer module to initialize the target module (e.g. any kind of `Config/AB flags`, `Managers` and `Helpers` must not be stored inside arguments, and these variables must be injected to the presenters' initializer directly)

## Consequences

Passing as an argument structure will provide us minimum code line changes and avoid pollution of codebase for each modules.
