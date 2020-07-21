# Usage of SwiftMockGenerator

* Status: accepted
* Deciders: iOS Team
* Date: 2020-07-21

## Context

Since we started to use `XCTest` framework to write unit tests, we faced a problem that is we need to write a lot of mocks manually. However using a mock is almost always a must for every unit test, we were spending too much time to create them. We need either a framework/library or something like an Xcode plugin to create them for us automatically.

## Decision

We found the [Swift Mock Generator](https://github.com/seanhenry/SwiftMockGeneratorForXcode) to solve this specific problem. It is an Xcode plugin and it lets you to create mocks for protocols automatically.

One of the advantages of using a plugin is, it works independently, which means you do not have to import a huge dependency on your project and don't bother about it's maintenance.

It has 4 different options to create the mock, spy, stub, dummy and partial spy. All of these options and also the usage of them have described in the Github page.

## Consequences

Writing mock classes and stubbing mock methods are becoming much less time consuming.