# Automatically trim trailing whitespace

* Status: accepted
* Deciders: iOS Team
* Date: 2023-12-05

## Context

Unnecessary diffs and conflict situations in MRIs after automatically created spaces by XCode.

## Decision

It is required to tick a xcode preferences for newly created empty lines of codes
For this, the following steps should be followed.

    1- Top menu bar -> Xcode -> Settings... (Cmd+Ö or ⌘Ö,)
    2- Text Editing -> Editing on tabBar -> While editing
    3- Turn on both "Automatically trim trailing whitespace" and "Including whitespace-only lines".

## Consequences

  * Number of lines of code affected in MRs will decrease.
  * Number of conflicts will decrease for branches that merge late, such as RC-temp branches.
  * After control+I, unnecessary spaces will be automatically cleared in empty lines.
