# ABCultureConfigurable

* Status: Accepted
* Deciders: iOS Team
* Date: 17.12.2024

## Context
We need to define at least three configs for ABTests in each environment. This increases effort and complexity.

## Decision
We will use ABCultureConfigurable, even though ABTests are not culture-based. This way, we will define only one config for each environment.

### Before
We need to create 6 configs for this case

```
iOSMealProductStampViewABEnabled
iOSMealProductStampViewABAsIs
iOSMealProductStampViewABNew
iOSMealProductStampViewABNewV2
iOSMealProductStampViewABNewV3
iOSMealProductStampViewABNewV4
```
### After
```json
{
  "info": [
    {
      "countryCulturePath": "others",
      "value": {
        "enabled": true,
        "abTesting": {
          "asIs": 100,
          "new": 0,
          "newV2": 0,
          "newV3": 0,
          "newV4": 0
        }
      }
    }
  ]
}
```