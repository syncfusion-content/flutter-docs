---
layout: post
title: Legend in Flutter Maps widget | Syncfusion
description: Learn here all about the Legend feature of Syncfusion Flutter Maps (SfMaps) widget to customize its appearance including text, icon and more.
platform: Flutter
control: SfMaps
documentation: ug
---

# Legend in Flutter Maps (SfMaps)

You can provide clear information on the data plotted on the map using legend.

## Shape legend

You can show shape legend by setting the [`MapShapeLayer.legend`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend-class.html) property as `MapLegend(MapElement.shape)`. By default, the legend item's text is rendered based on the value of [`shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/shapeDataField.html) property. The default value of the [`legend`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend-class.html) property is `null` and hence the legend will not be shown by default.

{% tabs %}
{% highlight Dart %}

late MapShapeSource _shapeSource;

@override
void initState() {
  super.initState();

  _shapeSource = MapShapeSource.asset(
    "assets/world_map.json",
    shapeDataField: "continent",
  );
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: SizedBox(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend(MapElement.shape),
                ),
              ],
            ),
          ),
        ),
      ),
   );
}

{% endhighlight %}
{% endtabs %}

![Shape legend support](images/legend/default-legend.png)

N>
* Refer the [`MapLegend.bar`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.bar.html), for showing bar legend.

## Bubble legend

You can show bubble legend by setting the [`MapShapeLayer.legend`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend-class.html) property as `MapLegend(MapElement.bubble)`. By default, the legend item's text is rendered based on the value of [`shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/shapeDataField.html) property.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
  super.initState();
  _data = <Model>[
    Model('Asia', 150),
    Model('Africa', 45),
    Model('Europe', 34),
    Model('North America', 28),
    Model('South America', 25),
    Model('Australia', 5),
  ];

  _shapeSource = MapShapeSource.asset(
    "assets/world_map.json",
    shapeDataField: "continent",
    dataCount: _data.length,
    primaryValueMapper: (int index) => _data[index].continent,
    bubbleSizeMapper: (int index) => _data[index].populationDensityPerSqKm,
  );
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: Container(
        padding: const EdgeInsets.only(left: 10, right: 15, top: 30),
        height: 350,
        child: SfMaps(
          layers: [
            MapShapeLayer(
              source: _shapeSource,
              legend: MapLegend(MapElement.bubble),
              bubbleSettings: const MapBubbleSettings(
                maxRadius: 45,
                minRadius: 15,
              ),
            )
          ],
        ),
      ),
    ),
  );
}

class Model {
  const Model(this.continent, this.populationDensityPerSqKm);

  final String continent;
  final double populationDensityPerSqKm;
}

{% endhighlight %}
{% endtabs %}

![Bubble legend support](images/legend/bubble_legend.png)

N>
* Refer the [`MapLegend.bar`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.bar.html), for showing bar legend.

## Bar shape legend

You can show bar shape legend by setting the [`MapShapeLayer.legend`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.bar.html) property as `MapLegend.bar(MapElement.shape)`. By default, the legend item's text is rendered based on the value of [`shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/shapeDataField.html) property.

{% tabs %}
{% highlight Dart %}

late MapShapeSource _shapeSource;

@override
void initState() {
  super.initState();

  _shapeSource = MapShapeSource.asset(
    "assets/world_map.json",
    shapeDataField: "continent",
  );
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(MapElement.shape),
                ),
              ],
            ),
          ),
        ),
      ),
   );
}

{% endhighlight %}
{% endtabs %}

![Bar shape legend](images/legend/bar-shape-legend.png)

N>
* Refer the [`MapLegend`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html), for showing default legend.

## Bar bubble legend

You can show bar bubble legend by setting the [`MapShapeLayer.legend`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.bar.html) property as `MapLegend.bar(MapElement.bubble)`. By default, the legend item's text is rendered based on the value of [`shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/shapeDataField.html) property.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
  super.initState();
  _data = <Model>[
    Model('Asia', 150),
    Model('Africa', 45),
    Model('Europe', 34),
    Model('North America', 28),
    Model('South America', 25),
    Model('Australia', 5),
  ];

  _shapeSource = MapShapeSource.asset(
    "assets/world_map.json",
    shapeDataField: "continent",
    dataCount: _data.length,
    primaryValueMapper: (int index) => _data[index].continent,
    bubbleSizeMapper: (int index) => _data[index].populationDensityPerSqKm,
  );
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: Container(
        padding: const EdgeInsets.only(left: 10, right: 15, top: 30),
        height: 350,
        child: SfMaps(
          layers: [
            MapShapeLayer(
              source: _shapeSource,
              legend: MapLegend.bar(MapElement.bubble),
              bubbleSettings: const MapBubbleSettings(
                maxRadius: 45,
                minRadius: 15,
              ),
            )
          ],
        ),
      ),
    ),
  );
}

class Model {
  const Model(this.continent, this.populationDensityPerSqKm);

  final String continent;
  final double populationDensityPerSqKm;
}

{% endhighlight %}
{% endtabs %}

![Bar bubble legend](images/legend/bar-bubble-legend.png)

N>
* Refer the [`MapLegend`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html), for showing default legend.

## Title

You can add title to the legend using the `MapLegend.title` property.

N> It is applicable for both shape and bar legend.

{% tabs %}
{% highlight Dart %}

late MapShapeSource _dataSource;
late List<DataModel> _data;

@override
void initState() {
   _data = const <DataModel>[
      DataModel('Asia', 280),
      DataModel('Europe', 120),
      DataModel('Africa', 40),
      DataModel('North America', 90),
      DataModel('South America', 190),
      DataModel('Australia', 210),
   ];

   _dataSource = MapShapeSource.asset(
      'assets/world_map.json',
      shapeDataField: 'continent',
      dataCount: _data.length,
      primaryValueMapper: (int index) => _data[index].continent,
   );
   super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: Column(
        children: [
          SfMaps(
            layers: <MapShapeLayer>[
              MapShapeLayer(
                source: _dataSource,
                legend: MapLegend(
                  MapElement.shape,
                  title: Text('Continents',
                      style:
                          TextStyle(fontSize: 14, fontWeight: FontWeight.bold)),
                ),
              ),
            ],
          ),
        ],
      ),
   );
}

class DataModel {
  const DataModel(this.continent, this.size);

  final String continent;
  final double size;
}

{% endhighlight %}
{% endtabs %}

![Legend title](images/legend/legend-title.png)

## Icon and text customization

The icons color of the legend is applied based on the colors returned from the [`MapShapeLayerDelegate.shapeColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/shapeColorValueMapper.html) property and the text is taken from the [`shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/shapeDataField.html). It is possible to customize the legend icons color and texts using the [`MapColorMapper.color`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/color.html) and [`MapColorMapper.text`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/text.html) properties based on the [`MapColorMapper.value`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/value.html) or [`MapColorMapper.from`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/from.html) and [`MapColorMapper.to`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/to.html) properties.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
  super.initState();
  _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Russia', 310)
  ];

  _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
  ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend(MapElement.shape),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Legend text customization](images/legend/legend-text-customization.png)

## First segment label customization

You can customize the first segment label of the legend using the [`MapColorMapper.text`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/text.html) property with curly braces. The first curly brace value will be applied as segment start label and the next curly brace value will be applied as segment end label. By default, the [`MapColorMapper.from`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/from.html) value is placed at the starting position of first segment and the [`MapColorMapper.to`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/to.html) value is placed at the ending position of the first segment.

{% tabs %}
{% highlight Dart %}

late List<DataModel> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
  _data = <DataModel>[
    DataModel('India', 280),
    DataModel('United States of America', 190),
    DataModel('Kazakhstan', 37),
    DataModel('Italy', 201),
    DataModel('Japan', 335),
    DataModel('Cuba', 103),
    DataModel('China', 148)
  ];

  _shapeSource = MapShapeSource.asset(
    "assets/world_map.json",
    shapeDataField: "name",
    dataCount: _data.length,
    primaryValueMapper: (int index) => _data[index].country,
    shapeColorValueMapper: (int index) => _data[index].density,
    shapeColorMappers: [
      MapColorMapper(
          from: 0, to: 100, color: Colors.red, text: '{0/km},{100/km}'),
      MapColorMapper(from: 101, to: 200, color: Colors.green, text: '200/km'),
      MapColorMapper(from: 201, to: 300, color: Colors.blue, text: '300/km'),
      MapColorMapper(from: 301, to: 400, color: Colors.orange, text: '400/km'),
      MapColorMapper(from: 401, to: 500, color: Colors.teal, text: '500/km'),
    ],
  );
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: Container(
        height: 350,
        child: Padding(
          padding: const EdgeInsets.only(left: 15, right: 15),
          child: SfMaps(
            layers: [
              MapShapeLayer(
                source: _shapeSource,
                legend: MapLegend.bar(
                  MapElement.shape,
                ),
              )
            ],
          ),
        ),
      ),
    ),
  );
}

class DataModel {
  const DataModel(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![First label customization](images/legend/first-label-customization.png)

## Position

You can position the legend items in different directions using the [`MapLegend.position`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/position.html) property. The default value of the [`position`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/position.html) property is `MapLegendPosition.top`. The possible values are `left`, `right`, `top`, and `bottom`.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
  super.initState();
  _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
  ];

  _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
    ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend(
                    MapElement.shape,
                    position: MapLegendPosition.right,
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Legend position](images/legend/legend-position.png)

N>
* Refer the [`offset`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/offset.html), for placing the legend in custom position.

## Offset

You can place the legend in custom position using the [`MapLegend.offset`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/offset.html) property. The default value of the [`offset`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/offset.html) property is `null`.

If the property [`MapLegend.offset`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/offset.html) has been set with the property [`MapLegend.position`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/position.html) as top, then the legend will be placed in top but with absolute position, i.e. legend will not take dedicated position for it and will be drawn at the top of the map.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
    super.initState();
    _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
    ];

    _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
    ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend(
                    MapElement.shape,
                    offset: Offset(60, 275)),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Legend offset](images/legend/legend-offset.png)

## Overflow mode

<b>For default legend</b>

You can wrap or scroll the legend items using the [`MapLegend.overflowMode`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/overflowMode.html) property. The default value of the [`overflowMode`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/overflowMode.html) property is `MapLegendOverflowMode.wrap`. The possible values are `scroll` and `wrap`.

If the legend position is `left` or `right`, then the default scroll direction is `vertical`.

If the legend position is `top` or `bottom`, then the default scroll direction is `horizontal`.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
   super.initState();
   _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];

   _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
        ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend(
                    MapElement.shape,
                    position: MapLegendPosition.bottom,
                    overflowMode: MapLegendOverflowMode.scroll,
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Legend overflow mode](images/legend/legend-overflow-mode.gif)

<b>For bar legend</b>

You can wrap or scroll the bar legend items using the [`MapLegend.overflowMode`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/overflowMode.html) property. The default value of the [`overflowMode`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/overflowMode.html) property is `MapLegendOverflowMode.scroll`. The possible values are `scroll` and `wrap`.

If the legend position is `left` or `right`, then the default scroll direction is `vertical`.

If the legend position is `top` or `bottom`, then the default scroll direction is `horizontal`.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
   super.initState();
   _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];

   _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
        ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    position: MapLegendPosition.bottom,
                    edgeLabelsPlacement: MapLegendEdgeLabelsPlacement.center,
                    overflowMode: MapLegendOverflowMode.scroll,
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Bar legend overflow mode](images/legend/bar-legend-overflow-mode.gif)

N>
* Refer the [`iconSize`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html), for setting the size of the icon.

## Scrollbar for legend

<b>For default legend</b>

You can scroll the legend items using the [`MapLegendOverflowMode.scroll`]() property. Basically, the scrollbar is not visible. Now using this [`shouldAlwaysShowScrollbar`] boolean property to make it visible. The possible values are `true` and `false`.

If the legend position is `left` or `right`, then the default scroll direction is `vertical`.

If the legend position is `top` or `bottom`, then the default scroll direction is `horizontal`.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
   super.initState();
   _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];

   _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
        ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend(
                    MapElement.shape,
                    position: MapLegendPosition.bottom,
                    overflowMode: MapLegendOverflowMode.scroll,
                    shouldAlwaysShowScrollbar: true,
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Map default legend scroll](images/legend/map-default-legend-scroll.png)

<b>For bar legend</b>

You can scroll the legend items using the [`MapLegendOverflowMode.scroll`]() property. Basically, the scrollbar is not visible. Now using this [`shouldAlwaysShowScrollbar`] boolean property to make it visible. The possible values are `true` and `false`.

If the legend position is `left` or `right`, then the default scroll direction is `vertical`.

If the legend position is `top` or `bottom`, then the default scroll direction is `horizontal`.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
   super.initState();
   _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];

   _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
        ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    position: MapLegendPosition.bottom,
                    edgeLabelsPlacement: MapLegendEdgeLabelsPlacement.center,
                    overflowMode: MapLegendOverflowMode.scroll,
                    shouldAlwaysShowScrollbar: true
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Map bar legend scroll](images/legend/map-bar-legend-scroll.png)

## Legend toggling

N> Legend toggling is not applicable for bar type legend.

You can enable toggling the legend items and the corresponding shapes or bubbles using the [`enableToggleInteraction`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html). The default value of the [`enableToggleInteraction`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) is `false`. You can customize the toggled shapes or bubbles using the following properties:

* **Toggled item color** - Change the color for the toggled legend item's icon and it's shape or bubble using the [`toggledItemColor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html).
* **Toggled item stroke color** - Change the stroke color which applies to the toggled legend item's shape or bubble using the [`toggledItemStrokeColor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html).
* **Toggled item stroke width** - Change the stroke width which applies to the toggled legend item's shape or bubble using the [`toggledItemStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html).
* **Toggled item opacity** - Change the opacity of the toggled legend item's shape or bubble using the [`toggledItemOpacity`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html).

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
   super.initState();
   _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];

   _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
    ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend(
                    MapElement.shape,
                    enableToggleInteraction: true,
                    toggledItemColor: Colors.grey,
                    toggledItemStrokeWidth: 3,
                    toggledItemStrokeColor: Colors.black,
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

<b>Using SfMapsTheme</b>

You can also customize the below appearance of the legend using [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

* **Toggled item color** - Change the color for the toggled legend item's icon and it's shape or bubble using the [`SfMapsThemeData.toggledItemColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/toggledItemColor.html) property.
* **Toggled item stroke color** - Change the stroke color which applies to the toggled legend item's shape or bubble using the [`SfMapsThemeData.toggledItemStrokeColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/toggledItemStrokeColor.html) property.
* **Toggled item stroke width** - Change the stroke width which applies to the toggled legend item's shape or bubble using the [`SfMapsThemeData.toggledItemStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/toggledItemStrokeWidth.html) property.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
    super.initState();
    _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];

   _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
    ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMapsTheme(
              data: SfMapsThemeData(
                toggledItemColor: Colors.grey,
                toggledItemStrokeWidth: 3,
                toggledItemStrokeColor: Colors.black,
              ),
              child: SfMaps(
                layers: [
                  MapShapeLayer(
                    source: _shapeSource,
                    legend: MapLegend(
                      MapElement.shape,
                      enableToggleInteraction: true,
                    ),
                  )
                ],
              ),
            ),
          ),
        ),
      ),
   );
}

class Model {
   Model(this.country, this.density);

   final String country;
   final double density;
}

{% endhighlight %}
{% endtabs %}

![Toggles legend items](images/legend/toggles-legend-items.png)

## Text style

You can customize the legend item's text style using the [`MapLegend.textStyle`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/textStyle.html) property.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
    super.initState();
    _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];

   _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
        ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend(
                    MapElement.shape,
                    textStyle: const TextStyle(
                        color: Colors.red,
                        fontSize: 16,
                        fontWeight: FontWeight.bold,
                        fontStyle: FontStyle.italic,
                        fontFamily: 'Times'
                    ),
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

<b>Using SfMapsTheme</b>

You can also customize the legend item's text style using the [`SfMapsThemeData.legendTextStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/legendTextStyle.html) property in [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
    super.initState();
    _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];

   _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
        ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMapsTheme(
              data: SfMapsThemeData(
                legendTextStyle: TextStyle(
                    color: Colors.red,
                    fontSize: 16,
                    fontWeight: FontWeight.bold,
                    fontStyle: FontStyle.italic,
                    fontFamily: 'Times'
                ),
              ),
              child: SfMaps(
                layers: [
                  MapShapeLayer(
                    source: _shapeSource,
                    legend: MapLegend(MapElement.shape),
                  )
                ],
              ),
            ),
          ),
        ),
      ),
    );
  }
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Legend text style](images/legend/legend-text-style.png)

## Default legend appearance customization

You can customize the legend items using the following properties.

* **iconType** - Used to change the icon shape. The default value of the [`iconType`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) is `MapIconType.circle`. The possible values are `circle`, `rectangle`, `triangle`, and `diamond`.
* **iconSize** - Used to change the size of the icon. The default value of [`iconSize`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) is `Size(12.0, 12.0)`.
* **spacing** - Used to provide space between the each legend items. The default value of the [`spacing`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) is `10.0`.
* **direction** - Used to arrange the legend items in either horizontal or vertical direction. The default value of [`direction`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) property is `horizontal`, if the value of the [`position`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) property is `top`, `bottom` and defaults to `vertical`, if the value of the [`position`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) property is `left` or `right`.
* **padding** - Used to set padding around the legend. The default value of the [`padding`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.html) property is `EdgeInsets.all(10.0)`.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
    super.initState();
    _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
    ];

    _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
        ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: const EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend(
                    MapElement.shape,
                    position: MapLegendPosition.bottom,
                    overflowMode: MapLegendOverflowMode.wrap,
                    iconType: MapIconType.square,
                    iconSize: Size(15.0, 15.0),
                    itemsSpacing: 15,
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Legend items customization](images/legend/legend-items-customization.png)

N>
* Refer the [`position`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/position.html), for setting the position of the legend.

## Bar legend segment painting style

### Solid

You can set solid color for the bar by using the [MapLegendPaintingStyle.solid](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegendPaintingStyle.html). By defaults [MapLegendPaintingStyle](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.bar.html) will be `solid`.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
   super.initState();
   _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];

   _shapeSource = MapShapeSource.asset("assets/world_map.json",
        shapeDataField: "name",
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].country,
        shapeColorValueMapper: (int index) => _data[index].density,
        shapeColorMappers: [
          MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
          MapColorMapper(
              from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
          MapColorMapper(
              from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
          MapColorMapper(
              from: 301, to: 400, color: Colors.orange, text: '300 - 400/km'),
          MapColorMapper(
              from: 401, to: 500, color: Colors.teal, text: '400 - 500/km'),
          MapColorMapper(
              from: 501,
              to: 600,
              color: Colors.deepPurple,
              text: '500 - 600/km'),
        ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    segmentPaintingStyle: MapLegendPaintingStyle.solid,
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Bar legend solid type](images/legend/bar-legend-solid-type.png)

### Gradient

You can set gradient color for the bar by using the [MapLegendPaintingStyle.gradient](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegendPaintingStyle.html).

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
   super.initState();
   _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];

    _shapeSource = MapShapeSource.asset("assets/world_map.json",
           shapeDataField: "name",
           dataCount: _data.length,
           primaryValueMapper: (int index) => _data[index].country,
           shapeColorValueMapper: (int index) => _data[index].density,
           shapeColorMappers: [
             MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
             MapColorMapper(
                 from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
             MapColorMapper(
                 from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
             MapColorMapper(
                 from: 301,
                 to: 600,
                 color: Colors.deepPurple,
                 text: '300 - 600/km'),
    ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    labelsPlacement: MapLegendLabelsPlacement.betweenItems,
                    edgeLabelsPlacement: MapLegendEdgeLabelsPlacement.center,
                    segmentPaintingStyle: MapLegendPaintingStyle.gradient,
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Bar legend gradient type](images/legend/bar-legend-gradient-type.png)

## Bar legend appearance customization

You can customize the legend items using the following properties.

* **segmentSize** - Used to change the size of individual bar segments. When gradient paint style is applied, `segmentSize` argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.bar.html) will update the whole bar.
* **labelOverflow** - Used to remove or trim the legend labels based on the bar legend size.The default value of the [`labelOverflow`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.bar.html) argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.bar.html) will be `MapLabelOverflow.hide`.
* **edgeLabelsPlacement** - Used to place the edge labels either inside or outside of the bar legend. The default value of the [`edgeLabelsPlacement`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.bar.html) argument in the [`constructor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/MapLegend.bar.html) will be `MapLegendEdgeLabelsPlacement.inside`.
* **spacing** - Used to provide space between the each legend items. The default value of the [`spacing`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/spacing.html) is `2.0`. This is not applicable for gradient legend.
* **direction** - Used to arrange the legend items in either horizontal or vertical direction. The default value of [`direction`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/direction.html) property is `horizontal`, if the value of the [`position`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/position.html) property is `top`, `bottom` and defaults to `vertical`, if the value of the [`position`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/position.html) property is `left` or `right`.
* **padding** - Used to set padding around the legend. The default value of the [`padding`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegend/padding.html) property is `EdgeInsets.all(10.0)`.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
   super.initState();
   _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];

    _shapeSource = MapShapeSource.asset("assets/world_map.json",
           shapeDataField: "name",
           dataCount: _data.length,
           primaryValueMapper: (int index) => _data[index].country,
           shapeColorValueMapper: (int index) => _data[index].density,
           shapeColorMappers: [
             MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
             MapColorMapper(
                 from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
             MapColorMapper(
                 from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
             MapColorMapper(
                 from: 301,
                 to: 600,
                 color: Colors.deepPurple,
                 text: '300 - 600/km'),
    ]);
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    labelsPlacement: MapLegendLabelsPlacement.betweenItems,
                    edgeLabelsPlacement: MapLegendEdgeLabelsPlacement.center,
                    segmentPaintingStyle: MapLegendPaintingStyle.gradient,
                    labelOverflow: MapLabelOverflow.ellipsis,
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Bar legend customization](images/legend/bar-legend-customization.png)

## Bar legend labels placement

You can place the labels either between the segments or on the segments using the [`labelsPlacement`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegendLabelsPlacement.html) property.

<b>Labels placement for range color mapper</b>

The labels are positioned between the segments when setting range color mapper without setting color mapper [`MapColorMapper.text`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/text.html) property. The [`MapColorMapper.from`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/from.html) value of the first item is positioned at starting point of the first segment and the [`MapColorMapper.to`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/to.html) value of the first item is placed at the first segment end position. For other segments, the values of [`MapColorMapper.to`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/to.html) is positioned as label between the other segments.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
  super.initState();
  _data = <Model>[
    Model('India', 280),
    Model('United States of America', 190),
    Model('Kazakhstan', 37),
    Model('Italy', 201),
    Model('Cuba', 103),
    Model('China', 148),
];

_shapeSource = MapShapeSource.asset("assets/world_map.json",
    shapeDataField: "name",
    dataCount: _data.length,
    primaryValueMapper: (int index) => _data[index].country,
    shapeColorValueMapper: (int index) => _data[index].density,
    shapeColorMappers: [
      MapColorMapper(from: 0, to: 100, color: Colors.red),
      MapColorMapper(
              from: 101, to: 200, color: Colors.green),
      MapColorMapper(
              from: 201, to: 300, color: Colors.blue),
    ]
  );
}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    labelsPlacement: MapLegendLabelsPlacement.betweenItems,
                    segmentPaintingStyle: MapLegendPaintingStyle.gradient,
                  ),
                )
              ],
            ),
          ),
        ),
     ),
  );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Bar legend labels placement](images/legend/bar-legend-range-color-mapper-default.png)

The labels are positioned between the segments when setting range color mapper along with setting color mapper [`MapColorMapper.text`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/text.html) property. The [`MapColorMapper.from`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/from.html) value of the first item is positioned at starting point of the first segment and the [`MapColorMapper.text`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/text.html) value of the first item is placed at the first segment end position. For Other segments, the value of [`MapColorMapper.text`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/text.html) is positioned as label between the segments.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
  super.initState();
  _data = <Model>[
    Model('India', 280),
    Model('United States of America', 190),
    Model('Kazakhstan', 37),
    Model('Italy', 201),
    Model('Cuba', 103),
    Model('China', 148),
  ];

  _shapeSource = MapShapeSource.asset("assets/world_map.json",
    shapeDataField: "name",
    dataCount: _data.length,
    primaryValueMapper: (int index) => _data[index].country,
    shapeColorValueMapper: (int index) => _data[index].density,
    shapeColorMappers: [
        MapColorMapper(from: 0, to: 100, color: Colors.red, text: '<100/km'),
        MapColorMapper(from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
        MapColorMapper(from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
    ]
  );
}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    labelsPlacement: MapLegendLabelsPlacement.betweenItems,
                    segmentPaintingStyle: MapLegendPaintingStyle.gradient,
                  ),
                )
              ],
            ),
          ),
        ),
     ),
  );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Bar legend labels placement](images/legend/bar-legend-range-color-mapper-with-text.png)

The labels are positioned at the center of the segments when setting the [`labelsPlacement`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLegendLabelsPlacement.html) property to `MapLegendLabelsPlacement.onItem`. The labels calculated based on the value of [MapColorMapper.text](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/text.html) property. If the value of [MapColorMapper.text](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/text.html) property is null, labels calculated based on the values of [`MapColorMapper.from`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/from.html) and [`MapColorMapper.to`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/to.html) properties.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
  super.initState();
  _data = <Model>[
    Model('India', 280),
    Model('United States of America', 190),
    Model('Kazakhstan', 37),
    Model('Italy', 201),
    Model('Cuba', 103),
    Model('China', 148),
];

_shapeSource = MapShapeSource.asset("assets/world_map.json",
    shapeDataField: "name",
    dataCount: _data.length,
    primaryValueMapper: (int index) => _data[index].country,
    shapeColorValueMapper: (int index) => _data[index].density,
    shapeColorMappers: [
        MapColorMapper(from: 0, to: 100, color: Colors.red, text: '<100/km'),
        MapColorMapper(from: 101, to: 200, color: Colors.green, text: '100 - 200/km'),
        MapColorMapper(from: 201, to: 300, color: Colors.blue, text: '200 - 300/km'),
    ]
  );
}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    labelsPlacement: MapLegendLabelsPlacement.onItem,
                    edgeLabelsPlacement: MapLegendEdgeLabelsPlacement.center,
                    segmentPaintingStyle: MapLegendPaintingStyle.gradient,
                  ),
                )
              ],
            ),
          ),
        ),
     ),
  );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Bar legend labels placement](images/legend/bar-legend-range-color-mapper-onItem.png)

<b>Labels placement for equal color mapper</b>

The `labelsPlacement` option is not applicable for the shape/bubble applied with equal color mapper. By default, the labels are positioned at center of the segment.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _dataSource;

@override
void initState() {
  _data = <Model>[
    Model('India', "Low"),
    Model('United States of America', "High"),
    Model('Pakistan', "Low"),
    Model('Brazil', "Medium"),
  ];

   _dataSource = MapShapeSource.asset(
     "assets/world_map.json",
     shapeDataField: "name",
     dataCount: _data.length,
     primaryValueMapper: (int index) {
        return _data[index].country;
     },
     shapeColorValueMapper: (int index) {
       return _data[index].storage;
     },
     shapeColorMappers: [
        MapColorMapper(value: "Low", color: Colors.green),
        MapColorMapper(value: "Medium", color: Colors.blue),
        MapColorMapper(value: "High", color: Colors.red),
     ],
  );
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
       child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: <MapShapeLayer>[
                MapShapeLayer(
                  source: _dataSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    edgeLabelsPlacement: MapLegendEdgeLabelsPlacement.center,
                    segmentPaintingStyle: MapLegendPaintingStyle.gradient,
                  ),
                ),
              ],
            ),
          ),
        ),
     ),
  );
}

class Model {
  const Model(this.country, this.storage);

  final String country;
  final String storage;
}

{% endhighlight %}
{% endtabs %}

![Bar legend labels placement](images/legend/bar-legend-equal-color-mapper-default.png)

## Show pointer

You may show a pointer on the solid or gradient bar legend while hovering over a shape or bubble using the `showPointerOnHover` property. The default value of the `showPointerOnHover` property is `false`.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
   super.initState();
   _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Cuba', 103),
      Model('China', 148),
    ];

    _shapeSource = MapShapeSource.asset(
      "assets/world_map.json",
      shapeDataField: "name",
      dataCount: _data.length,
      primaryValueMapper: (int index) => _data[index].country,
      shapeColorValueMapper: (int index) => _data[index].density,
      shapeColorMappers: [
        MapColorMapper(from: 0, to: 100, color: Colors.red, text: '0 - 100'),
        MapColorMapper(
            from: 101, to: 200, color: Colors.green, text: '101 - 200'),
        MapColorMapper(
            from: 201, to: 300, color: Colors.blue, text: '201 - 300'),
      ],
    );
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    segmentPaintingStyle: MapLegendPaintingStyle.gradient,
                    showPointerOnHover: true,
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Bar legend pointer](images/legend/bar-legend-pointer.gif)

## Pointer builder

It returns a widget for the given value.

The pointer is used to indicate the exact color of the hovering shape or bubble on the legend segment.

The `pointerBuilder` will be called when the user interacts with the shapes or bubbles i.e., while tapping in touch devices and hovering in the mouse enabled devices.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
   super.initState();
   _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Cuba', 103),
      Model('China', 148),
   ];

   _shapeSource = MapShapeSource.asset(
      "assets/world_map.json",
      shapeDataField: "name",
      dataCount: _data.length,
      primaryValueMapper: (int index) => _data[index].country,
      shapeColorValueMapper: (int index) => _data[index].density,
      shapeColorMappers: [
        MapColorMapper(from: 0, to: 100, color: Colors.red, text: '0 - 100'),
        MapColorMapper(
            from: 101, to: 200, color: Colors.green, text: '101 - 200'),
        MapColorMapper(
            from: 201, to: 300, color: Colors.blue, text: '201 - 300'),
     ],
   );
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    segmentPaintingStyle: MapLegendPaintingStyle.gradient,
                    showPointerOnHover: true,
                    pointerBuilder: (BuildContext context, dynamic value) {
                      return Icon(Icons.arrow_downward, size: 15);
                    },
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Bar legend custom pointer](images/legend/bar-legend-custom-pointer.png)

## Pointer customization

You can customize the size and color of the pointer using the `pointerSize` and `pointerColor` properties. The default value of the `pointerSize` property is `Size(16, 12)`.

{% tabs %}
{% highlight Dart %}

late List<Model> _data;
late MapShapeSource _shapeSource;

@override
void initState() {
   super.initState();
   _data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
      Model('Italy', 201),
      Model('Cuba', 103),
      Model('China', 148),
    ];

    _shapeSource = MapShapeSource.asset(
      "assets/world_map.json",
      shapeDataField: "name",
      dataCount: _data.length,
      primaryValueMapper: (int index) => _data[index].country,
      shapeColorValueMapper: (int index) => _data[index].density,
      shapeColorMappers: [
        MapColorMapper(from: 0, to: 100, color: Colors.red, text: '0 - 100'),
        MapColorMapper(
            from: 101, to: 200, color: Colors.green, text: '101 - 200'),
        MapColorMapper(
            from: 201, to: 300, color: Colors.blue, text: '201 - 300'),
      ],
   );
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _shapeSource,
                  legend: MapLegend.bar(
                    MapElement.shape,
                    segmentPaintingStyle: MapLegendPaintingStyle.gradient,
                    showPointerOnHover: true,
                    pointerSize: Size(20, 20),
                    pointerColor: Colors.deepPurple,
                  ),
                )
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.density);

  final String country;
  final double density;
}

{% endhighlight %}
{% endtabs %}

![Bar legend pointer customization](images/legend/bar-legend-pointer-customization.png)

N> You can refer to our [Flutter Maps](https://www.syncfusion.com/flutter-widgets/flutter-maps) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Maps Legend example](https://flutter.syncfusion.com/#/maps/shape-layer/legend) that shows how to configure a Maps in Flutter.

