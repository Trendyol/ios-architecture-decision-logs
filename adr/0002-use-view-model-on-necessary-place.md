# If it is necessary to manipulate the DTO models that the UI will use, the ViewModel class needs to be created.

* Status: declined (2020-12-2)
* Deciders: iOS Team
* Date: 2020-03-04

## Context

Our problem was that if we need to manipulate the response we was doing it on DTO object. And that object getting larger. Also if some field changes on response object we need to update the ui's fields. But nothing change on user interface. That's why we need to seperate DTO and UI's Model's from each other.

## Decision

~~If it is necessary to manipulate the DTO models that the UI will use, the ViewModel class needs to be created.~~

## Consequences

  * Much More Clean Code
