# Lite Mode Config Usage

* Status: Accepted
* Deciders: iOS Team
* Date: 14.01.2025

## Context
Currently, we add lite configs to TYConfigs.swift file by creating a new struct that conforms to BoolValueConfigurable protocol. There are no customizations in the keys of our lite configs that we add to the config panel. This approach:
- Increases coupling with TYConfigs.swift
- Makes the codebase less organized
- Makes it harder to analyze lite configs across the project
- Lite Mode configs are hard to distinguish from other configs
To simplify configuration management and establish a more sustainable structure, we decided to integrate Lite Mode configurations into the FeatureFlag structure.

## Decision-1
The .liteMode case has been added to the FeatureFlagType enum within the existing @FeatureFlag. Thus, Lite Mode configurations should be defined as @FeatureFlag(type: .liteMode).

### Before
```swift
public struct ProductDetailBasketRecommendationCallEnabled: BoolValueConfigurable {
    public var configName: String { "iOSProductDetailBasketRecommendationCallEnabled" }
    public init() { }
}
```

### After
```swift
@FeatureFlag("configVariableName", type: .liteMode) 
var configVariableName: Bool
```

## Decision-2
We will specify lite configs with LiteMode prefix.

### Before
Config Name:
```swift
iOSProductDetailBasketRecommendationCallEnabled
```

### After
Config Name:
```swift
iOSLiteModeProductDetailBasketRecommendationCallEnabled
```

## Consequences

### Positive
- Reduces coupling by eliminating dependency on TYConfigs.swift
- Provides better code organization
- Enables easier analysis of lite configs using liteconfig-analyzer
- Simplifies the implementation of new lite configs
- Makes the code more maintainable
- Lite Mode configs can be distinguish from other configs easily

### Negative
- Requires migration of existing lite configs
- Team needs to learn new syntax

## Implementation Notes
- The @FeatureFlag property wrapper with .litemode type will handle all the configuration logic internally
- liteconfig-analyzer tool will be able to scan the codebase and identify all lite configs
