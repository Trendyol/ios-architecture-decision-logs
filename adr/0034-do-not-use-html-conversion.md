#  Prohibiting the Use of HTML Conversion Methods

* Status: Accepted
* Deciders: iOS Team
* Date: 14.02.2025

## Context
In our iOS application, instead of using text structures containing HTML tags from data to create NSAttributedString, we should proceed with plain text structures. However, this approach has several drawbacks:
- Performance overhead: These operations expensive and can cause jank/hangs when executed on the main thread.
- Crash risk: Despite being wrapped with try?, it can still lead to runtime crashes, especially when dealing with malformed HTML or unexpected characters.
- Safer and more efficient alternatives exist: More controlled and lightweight solutions should be preferred. 

## Decision
The convertHtmlAsMutableAttributedString() or any other html conversion methods will no longer be used in the application. For HTML conversion, safer and more efficient solutions should be considered.
