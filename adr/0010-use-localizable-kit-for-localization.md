# Use LocalizableKit for Localization

* Status:  accepted
* Deciders: iOS Team
* Date: 2020-11-10

## Context

Localizable files have been defined in different ways to date. Therefore, we may need to duplicate text for other modules, or if we add new language support, it will be difficult to read localizable files from many places.

## Decision

Localizable files must be defined in the LocalizableKit. 
If the localizable you define is related to the channel or channel modules, you should use XXLocalizableKit, if related to a Kit, you should use TYCoreUtils.

## Consequences

Localizable files will be defined in the LocalizableKit. Thus, there will be no duplicate texts, it will be easy to add new language support.
