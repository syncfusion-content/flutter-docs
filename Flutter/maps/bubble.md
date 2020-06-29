---
layout: post
title: Bubbles in Syncfusion Flutter Maps | Syncfusion
description: This section explains about how show bubbles and customize its appearance in the Flutter maps application.
platform: Flutter
control: SfMaps
documentation: ug
---

# Bubbles in the Flutter Maps

You can add information to shapes such as population density, number of users, and more. Bubbles can be rendered in different colors and sizes based on the data values of their assigned shape.

## Show bubbles

You can show bubbles using the `showBubbles` property in the `MapShapeLayer` and the `bubbleSizeMapper` property of the `MapShapeLayerDelegate` is used to specify size to the bubble.

```dart
List<Model> data;

@override
void initState() {
   super.initState();

   data = <Model>[s
      Model('Asia', 51),
      Model('Africa', 58),
      Model('Europe', 48),
      Model('North America', 41),
      Model('South America', 14),
      Model('Australia', 23),
   ];
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: EdgeInsets.only(left: 15, right: 15),
        child: SfMaps(
          layers: [
            MapShapeLayer(
              delegate: MapShapeLayerDelegate(
                  shapeFile: "assets/world_map.json",
                  shapeDataField: "continent",
                  dataCount: data.length,
                  primaryValueMapper: (int index) => data[index].continent,
                  bubbleSizeMapper: (int index) => data[index].countriesCount
              ),
              showBubbles: true,
            )
          ],
        ),
      ),
   );
}

class Model {
  const Model(this.continent, this.countriesCount);

  final String continent;
  final double countriesCount;
}
```

![Bubble support](images/bubble/default-bubble.png)

## Bubbles customization

You can customize the bubbles using the `minRadius`, `maxRadius`, `color`, `strokeWidth`, and `strokeColor` properties in the `bubbleSettings` property.

N>
* The default value of the `minRadius` property is `10.0`.
* The default value of the `maxRadius` property is `50.0`.
* The default value of the `opacity` property is `0.75`.

```dart
List<Model> data;

@override
void initState() {
    super.initState();

    data = <Model>[
      Model('Asia', 51),
      Model('Africa', 58),
      Model('Europe', 48),
      Model('North America', 41),
      Model('South America', 14),
      Model('Australia', 23),
    ];
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: EdgeInsets.only(left: 15, right: 15),
        child: SfMaps(
          layers: [
            MapShapeLayer(
              delegate: MapShapeLayerDelegate(
                  shapeFile: "assets/world_map.json",
                  shapeDataField: "continent",
                  dataCount: data.length,
                  primaryValueMapper: (int index) => data[index].continent,
                  bubbleSizeMapper: (int index) => data[index].countriesCount,
              ),
              showBubbles: true,
              bubbleSettings: MapBubbleSettings(
                maxRadius: 30,
                minRadius: 15,
                color: Colors.red[200],
                strokeWidth: 2,
                strokeColor: Colors.red[800],
              ),
            )
          ],
        ),
      ),
   );
}

class Model {
  const Model(this.continent, this.countriesCount);

  final String continent;
  final double countriesCount;
}
```

![Bubble customization](images/bubble/bubble-customization.png)

## Bubbles tooltip

You can show tooltip for the bubbles using the `enableBubbleTooltip` property in the `MapShapeLayer`. It is possible to customize the bubble tooltip text using the `bubbleTooltipTextMapper` properties.

```dart
List<Model> data;

  @override
  void initState() {
    super.initState();

    data = <Model>[
      Model('Asia', 51),
      Model('Africa', 58),
      Model('Europe', 48),
      Model('North America', 41),
      Model('South America', 14),
      Model('Australia', 23),
    ];
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: EdgeInsets.only(left: 15, right: 15),
        child: SfMaps(
          layers: [
            MapShapeLayer(
              delegate: MapShapeLayerDelegate(
                  shapeFile: "assets/world_map.json",
                  shapeDataField: "continent",
                  dataCount: data.length,
                  primaryValueMapper: (int index) => data[index].continent,
                  bubbleSizeMapper: (int index) => data[index].countriesCount,
                  bubbleTooltipTextMapper: (int index) => data[index].countriesCount.toStringAsFixed(0) + 'countries',
              ),
              showBubbles: true,
              enableBubbleTooltip: true,
              bubbleSettings: MapBubbleSettings(
                maxRadius: 30,
                minRadius: 15,
                color: Colors.red[200],
                strokeWidth: 2,
                strokeColor: Colors.red[800],
              ),
            ),
          ],
        ),
      ),
   );
}

class Model {
  const Model(this.continent, this.countriesCount);

  final String continent;
  final double countriesCount;
}
```

![Bubble tooltip](images/bubble/bubble-tooltip.png)

## Bubbles palette

You can customize the bubble color based on the value returned from the `bubbleColorValueMapper` property in the `MapShapeLayerDelegate`. You can either return a value or a color from the `bubbleColorValueMapper`.

If `bubbleColorValueMapper` returns a color, then the color will be applied to the bubble from the underlying model straightaway.

If `bubbleColorValueMapper` returns a value other than the color, then you must set the `MapShapeLayer.bubbleColorMappers` property. The value returned from the `bubbleColorValueMapper` will be used for the comparison in the `MapColorMapper.value` or `MapColorMapper.from` and `MapColorMapper.to`. Then, the `MapColorMapper.color` will be applied to the respective bubble.

```dart
 List<Model> data;

  @override
  void initState() {
    super.initState();

    data = <Model>[
      Model('Asia', 51, Colors.red[400]),
      Model('Africa', 58, Colors.green[400]),
      Model('Europe', 48, Colors.blue[400]),
      Model('North America', 41, Colors.purple[400]),
      Model('South America', 14, Colors.yellow[400]),
      Model('Australia', 23, Colors.orange[400]),
    ];
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: EdgeInsets.only(left: 15, right: 15),
        child: SfMaps(
          layers: [
            MapShapeLayer(
              delegate: MapShapeLayerDelegate(
                shapeFile: "assets/world_map.json",
                shapeDataField: "continent",
                dataCount: data.length,
                primaryValueMapper: (int index) => data[index].continent,
                bubbleSizeMapper: (int index) => data[index].countriesCount,
                bubbleColorValueMapper: (int index) => data[index].bubbleColor,
                bubbleTooltipTextMapper: (int index) =>
                data[index].countriesCount.toStringAsFixed(0) + 'countries',
              ),
              showBubbles: true,
              enableBubbleTooltip: true,
              bubbleSettings: MapBubbleSettings(
                maxRadius: 30,
                minRadius: 15,
              ),
            ),
          ],
        ),
      ),
    );
  }
}

class Model {
  const Model(this.continent, this.countriesCount, this.bubbleColor);

  final String continent;
  final double countriesCount;
  final Color bubbleColor;
}
```
![Bubble palette](images/bubble/bubble-palette.png)
