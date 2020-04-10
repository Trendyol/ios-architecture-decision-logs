# Using XCTest for unit test instead of Quick/Nimble

* Status: accepted
* Deciders: iOS Team
* Date: 2020-04-07

## Context

Our problem was that using third party library for unittest instead of XCTest. And our unittests were most likely behavioural, we also wanted to change this approach and write unittest directly

## Decision

Every new unittest will be written with XCTest instead of Quick/Nimble

## Consequences

  * Writing unit test for each method instead of a behavioural test is much more convenient & easier
  * Converting Quick/Nimble unit tests to XCTest will be a challange
