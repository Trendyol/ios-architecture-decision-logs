# Config Name Definitions

* Status: accepted
* Deciders: iOS Team
* Date: 2022-01-24

## Context

Our common config definitions had unnecessary `EXP_` prefix.

## Decision

We decided not to use `EXP_` prefix when we need to create new common configs 

* Do not add `EXP_` prefix when create new config in stage, prepod and prod configuration panels
* `isLegacyCommonConfig` is deprecated, and must not be used. 
* `isCommonConfig` must be used to define new common config.
