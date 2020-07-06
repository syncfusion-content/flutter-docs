---
layout: post
title: Shape selection in Syncfusion Flutter Maps | Syncfusion
description: This section explains about how to enable shape selection and explains how to perform any action during selection.
platform: Flutter
control: SfMaps
documentation: ug
---

# Shape selection in the Flutter Maps

You can select a shape in order to highlight that area on a map. You can use the callback for performing any action during shape selection.

## Enable shape selection

You can enable shape selection on a map using the `MapShapeLayer.enableSelection` property. The default value of the `enableSelection` property is `false`.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    super.initState();
    data = const <Model>[
        Model('Asia', 'Asia', Color.fromRGBO(60, 120, 255, 0.8)),
        Model('Africa', 'Africa', Color.fromRGBO(51, 102, 255, 0.8)),
        Model('Europe', 'Europe', Color.fromRGBO(0, 57, 230, 0.8)),
        Model('South America', 'SA', Color.fromRGBO(0, 51, 204, 0.8)),
        Model('Australia', 'Australia', Color.fromRGBO(0, 45, 179, 0.8)),
        Model('North America', 'NA', Color.fromRGBO(0, 38, 153, 0.8))
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
                    shapeDataField: "continent",
                    dataCount: data.length,
                    primaryValueMapper: (int index) => data[index].continent,
                    shapeColorValueMapper: (int index) => data[index].color,
                  ),
                  enableSelection: true,
                ),
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.continent, this.code, this.color);

  final String continent;
  final String code;
  final Color color;
}

{% endhighlight %}
{% endtabs %}

![Enable shape selection](images/selection/enable-shape-selection.png)

N>
* Refer the `MapSelectionSettings`, for customizing the selected shape's appearance.

## Selection on initial rendering

You can programmatically select a shape on a map using the `MapShapeLayer.initialSelectedIndex` property.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    super.initState();
    data = const <Model>[
        Model('Asia', 'Asia', Color.fromRGBO(60, 120, 255, 0.8)),
        Model('Africa', 'Africa', Color.fromRGBO(51, 102, 255, 0.8)),
        Model('Europe', 'Europe', Color.fromRGBO(0, 57, 230, 0.8)),
        Model('South America', 'SA', Color.fromRGBO(0, 51, 204, 0.8)),
        Model('Australia', 'Australia', Color.fromRGBO(0, 45, 179, 0.8)),
        Model('North America', 'NA', Color.fromRGBO(0, 38, 153, 0.8))
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
                    shapeDataField: "continent",
                    dataCount: data.length,
                    primaryValueMapper: (int index) => data[index].continent,
                    shapeColorValueMapper: (int index) => data[index].color,
                  ),
                  enableSelection: true,
                  initialSelectedIndex: 5,
                ),
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.continent, this.code, this.color);

  final String continent;
  final String code;
  final Color color;
}

{% endhighlight %}
{% endtabs %}

![Selection on initial rendering](images/selection/selection-on-initial-rendering.png)

## Appearance customization

You can customize the below appearance of the selected shape.

* **Background color** - Change the background color of the selected shape using the `MapSelectionSettings.color` property.
* **Stroke width** - Change the stroke width of the selected shape using the `MapSelectionSettings.strokeWidth` property.
* **Stroke color** - Change the stroke color of the selected shape using the `MapSelectionSettings.strokeColor` property.
* **Opacity** - Change the opacity of the selected shape using the `MapSelectionSettings.opacity` property.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    super.initState();
    data = const <Model>[
        Model('Asia', 'Asia', Color.fromRGBO(60, 120, 255, 0.8)),
        Model('Africa', 'Africa', Color.fromRGBO(51, 102, 255, 0.8)),
        Model('Europe', 'Europe', Color.fromRGBO(0, 57, 230, 0.8)),
        Model('South America', 'SA', Color.fromRGBO(0, 51, 204, 0.8)),
        Model('Australia', 'Australia', Color.fromRGBO(0, 45, 179, 0.8)),
        Model('North America', 'NA', Color.fromRGBO(0, 38, 153, 0.8))
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
                    shapeDataField: "continent",
                    dataCount: data.length,
                    primaryValueMapper: (int index) => data[index].continent,
                    shapeColorValueMapper: (int index) => data[index].color,
                  ),
                  enableSelection: true,
                  selectionSettings: MapSelectionSettings(
                    color: Colors.orange,
                    strokeColor: Colors.red[900],
                    strokeWidth: 3,
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
  const Model(this.continent, this.code, this.color);

  final String continent;
  final String code;
  final Color color;
}

{% endhighlight %}
{% endtabs %}

<b>Using SfMapsTheme</b>

You can customize the below appearance of the selected shape using `SfMapsTheme`.

* **Background color** - Change the background color of the selected shape using the `SfMapsThemeData.selectionColor` property.
* **Stroke width** - Change the stroke width of the selected shape using the `SfMapsThemeData.selectionStrokeWidth` property.
* **Stroke color** - Change the stroke color of the selected shape using the `SfMapsThemeData.selectionStrokeColor` property.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    super.initState();
    data = const <Model>[
      Model('Asia', 'Asia', Color.fromRGBO(60, 120, 255, 0.8)),
      Model('Africa', 'Africa', Color.fromRGBO(51, 102, 255, 0.8)),
      Model('Europe', 'Europe', Color.fromRGBO(0, 57, 230, 0.8)),
      Model('South America', 'SA', Color.fromRGBO(0, 51, 204, 0.8)),
      Model('Australia', 'Australia', Color.fromRGBO(0, 45, 179, 0.8)),
      Model('North America', 'NA', Color.fromRGBO(0, 38, 153, 0.8))
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
                selectionColor: Colors.orange,
                selectionStrokeWidth: 3,
                selectionStrokeColor: Colors.red[900],
              ),
              child: SfMaps(
                layers: [
                  MapShapeLayer(
                    delegate: MapShapeLayerDelegate(
                      shapeFile: "assets/world_map.json",
                      shapeDataField: "continent",
                      dataCount: data.length,
                      primaryValueMapper: (int index) => data[index].continent,
                      shapeColorValueMapper: (int index) => data[index].color,
                    ),
                    enableSelection: true,
                  ),
                ],
              ),
            )
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.continent, this.code, this.color);

  final String continent;
  final String code;
  final Color color;
}

{% endhighlight %}
{% endtabs %}

![Selection customization](images/selection/selection-customization.png)

## Handling selection change

The `onSelectionChanged` callback is used to pass the index of the selected shape when the user is selecting a shape by tapping or clicking.

If the selected shape is tapped or clicked again, the index will be passed as -1. It means that, the shape is unselected.

N> You can get the index of the selected shape from `MapShapeLayerController.selectedIndex`.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
   super.initState();
    data = const <Model>[
    Model('Asia', 'Asia', Color.fromRGBO(60, 120, 255, 0.8)),
    Model('Africa', 'Africa', Color.fromRGBO(51, 102, 255, 0.8)),
    Model('Europe', 'Europe', Color.fromRGBO(0, 57, 230, 0.8)),
    Model('South America', 'SA', Color.fromRGBO(0, 51, 204, 0.8)),
    Model('Australia', 'Australia', Color.fromRGBO(0, 45, 179, 0.8)),
    Model('North America', 'NA', Color.fromRGBO(0, 38, 153, 0.8))
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
                    shapeDataField: "continent",
                    dataCount: data.length,
                    primaryValueMapper: (int index) => data[index].continent,
                    shapeColorValueMapper: (int index) => data[index].color,
                  ),
                  enableSelection: true,
                  onSelectionChanged: (int index) {
                    print('The selected region is ${data[index].code}');
                  },
                ),
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.continent, this.code, this.color);

  final String continent;
  final String code;
  final Color color;
}

{% endhighlight %}
{% endtabs %}
