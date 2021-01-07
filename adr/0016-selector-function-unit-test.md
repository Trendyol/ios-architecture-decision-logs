# Private selector function unit test

 * Status: accepted
 * Deciders: iOS team
 * Date: 2021-01-07

 ## Context

 The aim is to cover presenter's private selector's function and increase unit tests coverage results.

 ## Decision

 Selector function should be called inside ```Thread.detachNewThreadSelector``` method.


 ## Consequences
   * Unit tests coverage will be increase.
