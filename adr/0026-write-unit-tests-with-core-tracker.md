# Event unit tests

* Status: -
* Deciders: iOS Team
* Date: 2023-03-07

## Context

With the core tracker structure, we will be able to write key/value event tests correctly.

## Decision

Even if we type the same value on all keys while checking events, the test can be completed successfully. The important thing is that the count of key/value matches and the values are contained in the sent values. This may cause incorrect key/value tests to be completed successfully.

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

After the mockassertable, coretracker started working correctly for us. For this reason, if we do an event test with key/value using coretracker, we can get accurate results. For more accurate test results, we should use coretracker instead of trackableservicetest.

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
