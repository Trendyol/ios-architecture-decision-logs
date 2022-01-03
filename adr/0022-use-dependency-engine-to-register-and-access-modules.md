# Use Dependency Engine to Register and Access Modules

* Status: accepted
* Deciders: iOS Team
* Date: 2021-12-30

## Context

We had been struggling with dependencies that break our incremental builds for a while. We were using a standalone dependency manager that manages all of these dependencies, but it was not flexible as we want.

## Decision

We decided to create a brand new `DependencyEngine` to deal with these dependencies all over the app and *register* and *access* these modules by using `DependencyEngine`, and not exposing the explicit types through the protocols.

* `DependencyManager` is deprecated, and must not be used in brand new modules anymore. Also, existing usages should be transitioned.
* `DependencyEngine` must be used to access the modules through the other modules.
* The `arguments` that we use to initiate a module should be placed in `Interface` target of the module.
