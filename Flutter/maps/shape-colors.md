---
layout: post
title: Shape colors in Syncfusion Flutter Maps | Syncfusion
description: This section explains how to apply colors to the shapes based on specific values in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Shape colors in the Flutter Maps

You can categorize the shapes on a map by customizing their color based on the underlying value. It is possible to set the shape color for a specific value or for a range of values.

## Applying colors for the shape

If you return a color from the `shapeColorValueMapper`, then the color will be applied to the respective shape straightaway.

If you return a value of different type other than the color from the `shapeColorValueMapper`, then you must set the `MapShapeLayer.shapeColorMappers` property which is a collection of `MapColorMapper` to apply colors for the respective shapes.

N> You can show legend using the `showLegend` property in the `MapShapeLayer`. The icon color of the legend is applied based on the color returned in the `shapeColorValueMapper` property in the `MapShapeLayerDelegate` and the text will be taken from `primaryValueMapper`. It is possible to customize the legend item's color and text using the `shapeColorMappers` property in the `MapShapeLayerDelegate`.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    data = const <Model>[
      Model('Asia', Color.fromRGBO(60, 120, 255, 0.8)),
      Model('Africa', Color.fromRGBO(51, 102, 255, 0.8)),
      Model('Europe', Color.fromRGBO(0, 57, 230, 0.8)),
      Model('South America', Color.fromRGBO(0, 51, 204, 0.8)),
      Model('Australia', Color.fromRGBO(0, 45, 179, 0.8)),
      Model('North America', Color.fromRGBO(0, 38, 153, 0.8))
    ];
    super.initState();
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
          child: Container(
            height: 350,
            child: Padding(
              padding: EdgeInsets.only(left: 15, right: 15),
              child: SfMaps(
                layers: <MapLayer>[
                  MapShapeLayer(
                    delegate: MapShapeLayerDelegate(
                      shapeFile: 'assets/world_map.json',
                      shapeDataField: 'continent',
                      dataCount: data.length,
                      primaryValueMapper: (index) => data[index].country,
                      shapeColorValueMapper: (index) => data[index].color,
                    ),
                  ),
                ],
              ),
            ),
          )
      ),
  );
}

class Model {
  const Model(this.country, this.color);

  final String country;
  final Color color;
}

{% endhighlight %}
{% endtabs %}

![Shape color](images/shape-colors/shape_color_default.png)

## Equal color mapping

You can apply color to the shape by comparing a value that returns from the `shapeColorValueMapper` with the `MapColorMapper.value`. For the matched values, the `MapColorMapper.color` will be applied to the respective shapes.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    super.initState();

    data = <Model>[
      Model('India', "Low"),
      Model('United States of America', "High"),
      Model('Pakistan', "Low"),
    ];
}

@override
Widget build(BuildContext context) {
    return Scaffold(
        body: Padding(
          padding: EdgeInsets.only(left: 15, right: 15),
          child: SfMaps(
            layers: <MapShapeLayer>[
              MapShapeLayer(
                delegate: MapShapeLayerDelegate(
                    shapeFile: "assets/world_map.json",
                    shapeDataField: "name",
                    dataCount: data.length,
                    primaryValueMapper: (index) {
                      return data[index].country;
                    },
                    shapeColorValueMapper: (index) {
                      return data[index].storage;
                    },
                    shapeColorMappers: [
                      MapColorMapper(value: "Low", color: Colors.red),
                      MapColorMapper(value: "High", color: Colors.green)
                    ]),
              )
            ],
          ),
        ),
    );
  }
}

class Model {
  const Model(this.country, this.storage);

  final String country;
  final String storage;
}

{% endhighlight %}
{% endtabs %}

![Equal color mapping](images/shape-colors/equal_color_mapping.png)

## Range color mapping

You can apply color to the shape if the value returned from `shapeColorValueMapper` falls within the `MapColorMapper.from` and `MapColorMapper.to`. Then, the `MapColorMapper.color` will be applied to the respective shapes.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    super.initState();

    data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
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
                  shapeDataField: "name",
                  dataCount: data.length,
                  primaryValueMapper: (int index) => data[index].country,
                  shapeColorValueMapper: (int index) => data[index].count,
                  shapeColorMappers: [
                    MapColorMapper(from: 0, to: 100, color: Colors.red),
                    MapColorMapper(from: 101, to: 300, color: Colors.green)
                  ]
               ),
            )
          ],
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.count);

  final String country;
  final double count;
}

{% endhighlight %}
{% endtabs %}

![Range color mapping](images/shape-colors/range_color_mapping.png)
