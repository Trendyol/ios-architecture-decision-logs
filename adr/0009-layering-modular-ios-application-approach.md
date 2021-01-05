# Layering Modular iOS Application Approach

* Status: accepted
* Deciders: iOS Team
* Date: 2020-08-18

## Context

Our problem was defining the limit of modules.

## Decision

We decided splitting frameworks with their user flows.

## Consequences

We seperate features with domains. Our modules contains more than one Viper module and they are related with each other. For example ProductDetailModule can contains 'ProductDetailViperModule' and 'ProductDetailReviewViperModule'. If one feature is related with Product Detail we can create that View inside of that module.  
