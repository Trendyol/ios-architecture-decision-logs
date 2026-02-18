# Expose Module Functionality Through Interface Targets

* Status: accepted
* Deciders: iOS Team
* Date: 17.02.2026

## Context
We faced a problem that when exposing functionality to other modules, types and protocols were not always placed in the module's Interface target. This forced other modules to directly import the concrete module.

## Decision
When module functionality is intended to be used by other modules, all related types, protocols, and models must be exposed through the owning module's Interface target.

## Consequences
- Unnecessary dependencies between modules are prevented.
- Module boundaries and ownership remain clean.
- Incremental build times are preserved.