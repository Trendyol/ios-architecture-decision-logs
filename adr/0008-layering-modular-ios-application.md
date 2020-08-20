# Layering Modular iOS Application

* Status: accepted
* Deciders: iOS Team
* Date: 2020-08-18

## Context

Our problem was monolith single view app. Our project will grow out of control.
## Decision

We decided splitting it into individual feature modules. This is similar to the micro-service architecture.

## Consequences

We seperate features with their responsibilities. We creates a two type of frameworks: 
1. Kit
2. Module

If one framework contains helper class, entity or localizable strings. We named it to '**Kit**' ex: '**DeeplinkKit**'. On the other hand one framework contains'a View, Viper module and if it is unique we named it '**Module**'. ex: '**ProductDetailModule**'.
