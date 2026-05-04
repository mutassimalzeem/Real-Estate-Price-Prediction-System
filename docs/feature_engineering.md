# Feature Engineering Notes

Feature engineering is the strongest part of this project.

The dataset already contains many columns, but raw columns do not always express the most useful business signals directly.

## Engineered Features

### Total Area

Combines above-ground and basement space into one overall size signal.

Large homes generally sell for higher prices, so this is a strong feature.

### Total Bathroom Count

Combines full and half bathrooms from both basement and main living areas.

Bathrooms are an important quality-of-life feature in property valuation.

### Total Porch Area

Combines different porch-related columns into a single outdoor-space feature.

This makes sparse outdoor features easier for models to interpret.

### House Age

Calculated from year sold and year built.

Older homes may have different valuation patterns compared to newer homes.

### Remodel Age

Calculated from year sold and remodel year.

A recently remodeled older house can be more valuable than its original construction year suggests.

### Binary Feature Flags

The notebook creates flags such as:

- has garage
- has basement
- has fireplace
- has pool

These help models understand presence/absence patterns clearly.

### Quality-Adjusted Area

Combines overall quality and total area.

This captures an important interaction: a large house is not always expensive unless quality is also high.

## Why These Features Matter

Good feature engineering makes the model closer to real-world reasoning.

Instead of asking the model to discover every relationship from raw columns, we give it more meaningful signals that represent how people actually evaluate properties.
