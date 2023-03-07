# Event unit tests

* Status: -
* Deciders: iOS Team
* Date: 2023-03-07

## Context

With the core tracker structure, we will be able to write key/value event tests correctly.

## Decision

During event testing, it's possible to use the same value across all keys, and the test will still pass as long as the count of key/value matches and the values are included in the sent values. However, this approach may result in incorrect key/value tests passing.

✅ test passed
```swift 
 trackableServiceTest.assertValues(
    .firebase, ["Homepage",
                "Support_Click",
                "My Account"]
)
```

✅ test passed
```swift 
 trackableServiceTest.assertValues(
    .firebase, ["Homepage",
                "Homepage",
                "Homepage"]
)
```

After implementing the mockassertable framework, the coretracker began to function correctly, allowing us to conduct more accurate event tests using key-value pairs. Thus, we recommend using coretracker instead of trackableservicetest to obtain precise test results.

## Example Usage

✅ test passed
```swift 
coreTracker.assertInvokes([
    .delphoi([
        ("event", "storeAdvertImpression"),
        ("tv023", "searchResult,elbise"),
        ("tv024", "previousscreentitle"),
        ("tv027", "elbise"),
        ("tv073", "widget.marketing"),
        ("tv076", "widget.marketing"),
        ("tv139", "fullserviceurl-marketing"),
        ("tv193", "links-relativePath")
    ])
])
```
