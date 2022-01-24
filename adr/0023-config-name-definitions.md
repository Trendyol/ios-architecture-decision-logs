# Config Name Definitions

* Status: accepted
* Deciders: iOS Team
* Date: 2022-01-24

## Context

Our common config definitions had uneccasry `EXP_` prefix.

## Decision

We decided create new comon configs without `EXP_` prefix.

* Do not add `EXP_` prefix when create new config in stage, prepod and prod configuration panels
* `isLegacyCommonConfig` is deprecated, and must not be used. 
* `isCommonConfig` must be used to define new common config.
