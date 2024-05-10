# Using UserDefault with PropertyWrapper 

* Status: accepted
* Deciders: iOS Team
* Date: 2024-10-05

## Context

In this RFC, we have requested an RFC about using UserDefault PropertyWrapper. With this property wrapper we can set or get the wrapped value and mock the value easily. 
## Decision

By the comments, we have developed this propertyWrapper to use it on two cases. First one is optional and second one consists default value.

1- With optional
```swift 
@UserDefault("key")
var isFirstPage: Bool?
```
2- With default value. Default value only be read when the requested key does not exists on the app.
```swift 
@UserDefault("key")
var isFirstPage: Bool = false
```
