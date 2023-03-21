# Event unit tests

 * Status: Accepted
 * Deciders: iOS Team
 * Date: 2023-03-08

 ## Context

 With the core tracker structure, we will be able to write key/value event tests correctly.

 ## Decision

 During event testing, it's possible to use the same value across all keys, and the test will still pass as long as the count of key/value matches and the values are included in the sent values. However, this approach may result in incorrect key/value tests passing.

 ✅ test passed
 ```swift 
  trackableServiceTest.assertValues(
     .firebase, ["Homepage",
                 "Support",
                 "Account"]
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

After implementing with MockAssertable protocol, we started to evaluate event related data more efficiently and precisely from mock services under CoreTracker, and allowing us to conduct more accurate event tests using key-value pairs. Thus, we recommend using CoreTracker instead of TrackableServiceTest to obtain precise test results.

 ## Example Usage

 ✅ test passed
 ```swift 
 coreTracker.assertInvokes([
     .delphoi([
         ("event", "mockEvent"),
         ("tv023", "mocktv023"),
         ("tv024", "mocktv024"),
         ("tv027", "mocktv027"),
         ("tv073", "mocktv073"),
         ("tv076", "mocktv076"),
         ("tv139", "mocktv139"),
         ("tv193", "mocktv193")
     ])
 ])
 ```
