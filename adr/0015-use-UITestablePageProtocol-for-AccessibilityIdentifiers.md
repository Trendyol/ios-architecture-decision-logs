# Use UITestablePage Interface for setting Accessibility Identifiers

 * Status: accepted
 * Deciders: iOS Team
 * Date: 2020-01-05

## Context

Our team created new UITestablePage Interface for setting accessibility Identifiers. For consistency we should replace and use UITestablePage.

## Decision

Every View Controller should conform UITestablePage.

 ## Consequences

 * All accessibility identifiers will be in the same format.
 * With UITestablePage setting accessibility identifier are easy and simple.
