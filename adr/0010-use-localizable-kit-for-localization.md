# Using Localizable Kit for Localization

* Status: accepted
* Deciders: iOS Team
* Date: 2021-12-29

## Context

Localizable files have been defined in different ways to date. Therefore, we may need to duplicate text for other modules, or if we add new language support, it will be difficult to manage localizable files for common kits & modules from many different places within the channels.

## Decision

* Common localization files across the channels modules' should be defined in the associated channel LocalizableKit.
* Localizable files of common kits, modules and components used throughout the application should be defined within itself. It should not be defined in any LocalizableKit.
* Localizable files of channels that only concern their own modules should be defined within their own modules.

## Consequences

Only common texts that need to be shared within channels will be defined in the associated LocalizableKit.
