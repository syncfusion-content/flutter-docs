---
layout: post
title: Tooltips in Syncfusion Flutter maps | Syncfusion
description: This section explains about how to show tooltips and customize its appearance in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Tooltips in maps

This section helps to learn about how to add tooltip in the maps.

# Shape tooltip

You can enable tooltip for a shape. It is used to show an information about the current tapped shape. By default, the shape tooltip text will be based on [shapeDataField] values.

N> You must set `enableShapeTooltip` bool as true.

# Bubble tooltip

It is visibled when tapping on any of the bubbles in maps. It shows the information about the current tapped bubble.By default, the bubble tooltip text will be [primaryValueMapper] data.

N> You must set `enableBubbleTooltip` bool as true.

# Tooltip text customization

You can customize the shape tooltip text by using the [shapeTooltipTextMapper]. The [shapeTooltipTextMapper] will be called each time when you tap on a shape with corresponding index.You can pass the information that needs to be shown in the tooltip.

You can also customize the bubble tooltip as same shape tooltip using [bubbleTooltipTextMapper].

# Tooltip customization

You can customize the tooltip using the [tooltipSettings] which is property of [MapShapeLayer].

In [tooltipSettings], there are customizing properties like [color], [strokeColor], [strokeWidth], and [textStyle].

```dart
SfMaps(
            layers: <MapLayer>[
              MapShapeLayer(
                delegate: MapShapeLayerDelegate(
                  shapeFile: 'assets/europe.json',
                  shapeDataField: 'name',
                  dataCount: _gmtDetails.length,
                  primaryValueMapper: (int index) =>
                      _gmtDetails[index].countryName,
                  bubbleTooltipTextMapper: (int index) =>
                      'Country : ' +
                      _gmtDetails[index].countryName +
                      '\nPopulation : ' +
                      _gmtDetails[index].population.toInt().toString(),
                  bubbleSizeMapper: (index) => _gmtDetails[index].population,
                ),
                showBubbles: true,
                enableShapeTooltip: true,
                enableBubbleTooltip: true,
              ),
            ],
          )
```
```dart
SfMaps(
            layers: <MapLayer>[
              MapShapeLayer(
                delegate: MapShapeLayerDelegate(
                  shapeFile: 'assets/europe.json',
                  shapeDataField: 'name',
                  dataCount: _gmtDetails.length,
                  primaryValueMapper: (int index) =>
                      _gmtDetails[index].countryName,
                  bubbleTooltipTextMapper: (int index) =>
                      'Country : ' +
                      _gmtDetails[index].countryName +
                      '\nPopulation : ' +
                      _gmtDetails[index].population.toInt().toString(),
                  bubbleSizeMapper: (index) => _gmtDetails[index].population,
                ),
                showBubbles: true,
                enableShapeTooltip: true,
                enableBubbleTooltip: true,
              ),
            ],
          )
```