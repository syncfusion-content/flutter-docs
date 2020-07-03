---
layout: post
title: Legend in Syncfusion Flutter Maps | Syncfusion
description: This section explains how to show legend in the Flutter maps and customize its appearance including text, icon, position, etc.
platform: Flutter
control: SfMaps
documentation: ug
---

# Legend in the Flutter Maps

You can provide clear information on the data plotted on the map using legend.

## Show legend

You can show legend using the `MapShapeLayer.showLegend` property. By default, the legend item's text is rendered based on the value of `shapeDataField` property. The default value of the `showLegend` property is `false`.

{% tabs %}
{% highlight Dart %}

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
                  delegate: MapShapeLayerDelegate(
                    shapeFile: "assets/world_map.json",
                    shapeDataField: "continent",
                  ),
                  showLegend: true,
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

![Legend support](images/legend/default-legend.png)

N>
* Refer the `MapLegendSettings`, for customizing the legend items.

## Icon and text customization

The icons color of the legend is applied based on the colors returned from the `MapShapeLayerDelegate.shapeColorValueMapper` property and the text is taken from the `shapeDataField`. It is possible to customize the legend icons color and texts using the `MapColorMapper.color` and `MapColorMapper.text` properties based on the `MapColorMapper.value` or `MapColorMapper.from` and `MapColorMapper.to` properties.

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
      Model('Russia', 310)
    ];
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
                  delegate: MapShapeLayerDelegate(
                      shapeFile: "assets/world_map.json",
                      shapeDataField: "name",
                      dataCount: data.length,
                      primaryValueMapper: (int index) => data[index].country,
                      shapeColorValueMapper: (int index) => data[index].density,
                      shapeColorMappers: [
                        MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
                        MapColorMapper(from: 101, to: 200, color: Colors.green, text:'100 - 200/km'),
                        MapColorMapper(from: 201, to: 300, color: Colors.blue, text:'200 - 300/km'),
                        MapColorMapper(from: 301, to: 400, color: Colors.orange, text:'300 - 400/km'),
                      ]
                  ),
                  showLegend: true,
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

## Position

You can position the legend items in different directions using the `MapLegendSettings.position` property. The default value of the `position` property is `MapLegendPosition.top`. The possible values are `left`, `right`, `top`, and `bottom`.

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
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
  ];
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
                  delegate: MapShapeLayerDelegate(
                      shapeFile: "assets/world_map.json",
                      shapeDataField: "name",
                      dataCount: data.length,
                      primaryValueMapper: (int index) => data[index].country,
                      shapeColorValueMapper: (int index) => data[index].density,
                      shapeColorMappers: [
                        MapColorMapper(from: 0,
                            to: 100,
                            color: Colors.red,
                            text: '< 100/km'),
                        MapColorMapper(from: 101,
                            to: 200,
                            color: Colors.green,
                            text: '100 - 200/km'),
                        MapColorMapper(from: 201,
                            to: 300,
                            color: Colors.blue,
                            text: '200 - 300/km'),
                        MapColorMapper(from: 301,
                            to: 400,
                            color: Colors.orange,
                            text: '300 - 400/km'),
                        MapColorMapper(from: 401,
                            to: 500,
                            color: Colors.teal,
                            text: '400 - 500/km'),
                        MapColorMapper(from: 501,
                            to: 600,
                            color: Colors.deepPurple,
                            text: '500 - 600/km'),
                      ]
                  ),
                  showLegend: true,
                  legendSettings: MapLegendSettings(
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
* Refer the `offset`, for placing the legend in custom position.

## Offset

You can place the legend in custom position using the `MapLegendSettings.offset` property. The default value of the `offset` property is `null`.

If the property 'MapLegendSettings.offset' has been set with the property 'MapLegendSettings.position' as top, then the legend will be placed in top but with absolute position, i.e. legend will not take dedicated position for it and will be drawn at the top of the map.

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
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
    ];
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
                  delegate: MapShapeLayerDelegate(
                      shapeFile: "assets/world_map.json",
                      shapeDataField: "name",
                      dataCount: data.length,
                      primaryValueMapper: (int index) => data[index].country,
                      shapeColorValueMapper: (int index) => data[index].density,
                      shapeColorMappers: [
                        MapColorMapper(from: 0,
                            to: 100,
                            color: Colors.red,
                            text: '< 100/km'),
                        MapColorMapper(from: 101,
                            to: 200,
                            color: Colors.green,
                            text: '100 - 200/km'),
                        MapColorMapper(from: 201,
                            to: 300,
                            color: Colors.blue,
                            text: '200 - 300/km'),
                        MapColorMapper(from: 301,
                            to: 400,
                            color: Colors.orange,
                            text: '300 - 400/km'),
                        MapColorMapper(from: 401,
                            to: 500,
                            color: Colors.teal,
                            text: '400 - 500/km'),
                        MapColorMapper(from: 501,
                            to: 600,
                            color: Colors.deepPurple,
                            text: '500 - 600/km'),
                      ]
                  ),
                  showLegend: true,
                  legendSettings: MapLegendSettings(
                    offset: Offset(60, 275),
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

![Legend offset](images/legend/legend-offset.png)

## Overflow mode

You can wrap or scroll the legend items using the `MapLegendSettings.overflowMode` property. The default value of the `overflowMode` property is `MapLegendOverflowMode.wrap`. The possible values are `scroll` and `wrap`.

If the legend position is `left` or `right`, then the default scroll direction is `vertical`.

If the legend position is `top` or `bottom`, then the default scroll direction is `horizontal`.

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
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];
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
                  delegate: MapShapeLayerDelegate(
                      shapeFile: "assets/world_map.json",
                      shapeDataField: "name",
                      dataCount: data.length,
                      primaryValueMapper: (int index) => data[index].country,
                      shapeColorValueMapper: (int index) => data[index].density,
                      shapeColorMappers: [
                        MapColorMapper(from: 0,
                            to: 100,
                            color: Colors.red,
                            text: '< 100/km'),
                        MapColorMapper(from: 101,
                            to: 200,
                            color: Colors.green,
                            text: '100 - 200/km'),
                        MapColorMapper(from: 201,
                            to: 300,
                            color: Colors.blue,
                            text: '200 - 300/km'),
                        MapColorMapper(from: 301,
                            to: 400,
                            color: Colors.orange,
                            text: '300 - 400/km'),
                        MapColorMapper(from: 401,
                            to: 500,
                            color: Colors.teal,
                            text: '400 - 500/km'),
                        MapColorMapper(from: 501,
                            to: 600,
                            color: Colors.deepPurple,
                            text: '500 - 600/km'),
                      ]
                  ),
                  showLegend: true,
                  legendSettings: MapLegendSettings(
                    position: MapLegendPosition.bottom,
                    overflowMode: MapLegendOverflowMode.wrap
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

N>
* Refer the `showIcon`, for enabling the icon for the legend.
* Refer the `iconSize`, for setting the size of the icon.

## Legend toggling

You can enable toggling the legend items and the corresponding shapes using the `MapLegendSettings.enableToggleInteraction` property. The default value of the `enableToggleInteraction` property is `false`. You can customize the toggled shapes using the following properties:

* **Toggled shape color** - Change the color for the toggled legend item's icon and it's shape using the `MapLegendSettings.toggledShapeColor` property.
* **Toggled shape stroke color** - Change the stroke color which applies to the toggled legend item's shape using the `MapLegendSettings.toggledShapeStrokeColor` property.
* **Toggled shape stroke width** - Change the stroke width which applies to the toggled legend item's shape using the `MapLegendSettings.toggledShapeStrokeWidth` property.
* **Toggled shape opacity** - Change the opacity of the toggled legend item's shape using the `MapLegendSettings.opacity` property.

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
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];
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
                  delegate: MapShapeLayerDelegate(
                      shapeFile: "assets/world_map.json",
                      shapeDataField: "name",
                      dataCount: data.length,
                      primaryValueMapper: (int index) => data[index].country,
                      shapeColorValueMapper: (int index) => data[index].density,
                      shapeColorMappers: [
                        MapColorMapper(from: 0,
                            to: 100,
                            color: Colors.red,
                            text: '< 100/km'),
                        MapColorMapper(from: 101,
                            to: 200,
                            color: Colors.green,
                            text: '100 - 200/km'),
                        MapColorMapper(from: 201,
                            to: 300,
                            color: Colors.blue,
                            text: '200 - 300/km'),
                        MapColorMapper(from: 301,
                            to: 400,
                            color: Colors.orange,
                            text: '300 - 400/km'),
                        MapColorMapper(from: 401,
                            to: 500,
                            color: Colors.teal,
                            text: '400 - 500/km'),
                        MapColorMapper(from: 501,
                            to: 600,
                            color: Colors.deepPurple,
                            text: '500 - 600/km'),
                      ]
                  ),
                  showLegend: true,
                  legendSettings: MapLegendSettings(
                    enableToggleInteraction: true,
                    toggledShapeColor: Colors.grey,
                    toggledShapeStrokeWidth: 3,
                    toggledShapeStrokeColor: Colors.black,
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

You can also customize the below appearance of the legend using `SfMapsTheme`.

* **Toggled shape color** - Change the color for the toggled legend item's icon and it's shape using the `SfMapsThemeData.toggledShapeColor` property.
* **Toggled shape stroke color** - Change the stroke color which applies to the toggled legend item's shape using the `SfMapsThemeData.toggledShapeStrokeColor` property.
* **Toggled shape stroke width** - Change the stroke width which applies to the toggled legend item's shape using the `SfMapsThemeData.toggledShapeStrokeWidth` property.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

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
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
            child: SfMapsTheme(
              data: SfMapsThemeData(
                toggledShapeColor: Colors.grey,
                toggledShapeStrokeWidth: 3,
                toggledShapeStrokeColor: Colors.black,
              ),
              child: SfMaps(
                layers: [
                  MapShapeLayer(
                    delegate: MapShapeLayerDelegate(
                        shapeFile: "assets/world_map.json",
                        shapeDataField: "name",
                        dataCount: data.length,
                        primaryValueMapper: (int index) => data[index].country,
                        shapeColorValueMapper: (int index) => data[index].density,
                        shapeColorMappers: [
                          MapColorMapper(from: 0,
                              to: 100,
                              color: Colors.red,
                              text: '< 100/km'),
                          MapColorMapper(from: 101,
                              to: 200,
                              color: Colors.green,
                              text: '100 - 200/km'),
                          MapColorMapper(from: 201,
                              to: 300,
                              color: Colors.blue,
                              text: '200 - 300/km'),
                          MapColorMapper(from: 301,
                              to: 400,
                              color: Colors.orange,
                              text: '300 - 400/km'),
                          MapColorMapper(from: 401,
                              to: 500,
                              color: Colors.teal,
                              text: '400 - 500/km'),
                          MapColorMapper(from: 501,
                              to: 600,
                              color: Colors.deepPurple,
                              text: '500 - 600/km'),
                        ]
                    ),
                    showLegend: true,
                    legendSettings: MapLegendSettings(
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

You can customize the legend item's text style using the `MapLegendSettings.textStyle` property.

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
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];
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
                  delegate: MapShapeLayerDelegate(
                      shapeFile: "assets/world_map.json",
                      shapeDataField: "name",
                      dataCount: data.length,
                      primaryValueMapper: (int index) => data[index].country,
                      shapeColorValueMapper: (int index) => data[index].density,
                      shapeColorMappers: [
                        MapColorMapper(from: 0,
                            to: 100,
                            color: Colors.red,
                            text: '< 100/km'),
                        MapColorMapper(from: 101,
                            to: 200,
                            color: Colors.green,
                            text: '100 - 200/km'),
                        MapColorMapper(from: 201,
                            to: 300,
                            color: Colors.blue,
                            text: '200 - 300/km'),
                        MapColorMapper(from: 301,
                            to: 400,
                            color: Colors.orange,
                            text: '300 - 400/km'),
                        MapColorMapper(from: 401,
                            to: 500,
                            color: Colors.teal,
                            text: '400 - 500/km'),
                        MapColorMapper(from: 501,
                            to: 600,
                            color: Colors.deepPurple,
                            text: '500 - 600/km'),
                      ]
                  ),
                  showLegend: true,
                  legendSettings: MapLegendSettings(
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

You can also customize the legend item's text style using the `SfMapsThemeData.legendTextStyle` property in `SfMapsTheme`.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

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
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
   ];
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 350,
          child: Padding(
            padding: EdgeInsets.only(left: 15, right: 15),
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
                    delegate: MapShapeLayerDelegate(
                        shapeFile: "assets/world_map.json",
                        shapeDataField: "name",
                        dataCount: data.length,
                        primaryValueMapper: (int index) => data[index].country,
                        shapeColorValueMapper: (int index) => data[index].density,
                        shapeColorMappers: [
                          MapColorMapper(from: 0,
                              to: 100,
                              color: Colors.red,
                              text: '< 100/km'),
                          MapColorMapper(from: 101,
                              to: 200,
                              color: Colors.green,
                              text: '100 - 200/km'),
                          MapColorMapper(from: 201,
                              to: 300,
                              color: Colors.blue,
                              text: '200 - 300/km'),
                          MapColorMapper(from: 301,
                              to: 400,
                              color: Colors.orange,
                              text: '300 - 400/km'),
                          MapColorMapper(from: 401,
                              to: 500,
                              color: Colors.teal,
                              text: '400 - 500/km'),
                          MapColorMapper(from: 501,
                              to: 600,
                              color: Colors.deepPurple,
                              text: '500 - 600/km'),
                        ]
                    ),
                    showLegend: true,
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

## Appearance customization

You can customize the legend items using the following properties.

* **showIcon** - Used to show or hide the legend icons. The default value of the `showIcon` property is `true`.
* **iconType** - Used to change the icon shape. The default value of the `iconType` property is `MapIconType.circle`. The possible values are `circle`, `square`, `triangle`, and `diamond`.
* **iconSize** - Used to change the size of the icon. The default value is `Size(12.0, 12.0)`.
* **itemsSpacing** - Used to provide space between the each legend items. The default value of the `itemsSpacing` is `10.0`.
* **direction** - Used to arrange the legend items in either horizontal or vertical direction. It defaults to `horizontal`, if the value of the `position` property is `top`, `bottom` and defaults to `vertical`, if the value of the `position` property is `left` or `right`.
* **padding** - Used to set padding around the legend. The default value of the `padding` property is `EdgeInsets.all(10.0)`.

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
      Model('Italy', 201),
      Model('Korea', 512),
      Model('Japan', 335),
      Model('Cuba', 103),
      Model('China', 148)
    ];
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
                  delegate: MapShapeLayerDelegate(
                      shapeFile: "assets/world_map.json",
                      shapeDataField: "name",
                      dataCount: data.length,
                      primaryValueMapper: (int index) => data[index].country,
                      shapeColorValueMapper: (int index) => data[index].density,
                      shapeColorMappers: [
                        MapColorMapper(from: 0, to: 100, color: Colors.red, text: '< 100/km'),
                        MapColorMapper(from: 101, to: 200, color: Colors.green, text:'100 - 200/km'),
                        MapColorMapper(from: 201, to: 300, color: Colors.blue, text:'200 - 300/km'),
                        MapColorMapper(from: 301, to: 400, color: Colors.orange, text:'300 - 400/km'),
                        MapColorMapper(from: 401, to: 500, color: Colors.teal, text:'400 - 500/km'),
                        MapColorMapper(from: 501, to: 600, color: Colors.deepPurple, text:'500 - 600/km'),
                      ]
                  ),
                  showLegend: true,
                  legendSettings: MapLegendSettings(
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
* Refer the `EdgeInsetsGeometry`, to use the EdgeInsets values.
* Refer the `position`, for setting the position of the legend.
