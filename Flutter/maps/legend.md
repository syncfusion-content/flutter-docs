---
layout: post
title: Legend in Syncfusion Flutter Maps | Syncfusion
description: This section explains about how to show legend and customize its appearance in the Flutter maps application.
platform: Flutter
control: SfMaps
documentation: ug
---

# Legend in the Flutter Maps

You can provide clear information on the data plotted in the map. You can use the legend toggling feature to visualize only the shapes to which the legend applies.

## Show legend

You can show legend using the `showLegend` property in the `MapShapeLayer`. The legend text is rendered based on the value of `shapeDataField` property.

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

## Icon color

The icon color of the legend is applied based on the color returned in the `shapeColorValueMapper` property in the `MapShapeLayerDelegate` and the text will be taken from `primaryValueMapper`.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    super.initState();

    data = <Model>[
      Model('Asia', Colors.yellow[300]),
      Model('Africa', Colors.green[300]),
      Model('Europe', Colors.blue[300]),
      Model('North America', Colors.purple[300]),
      Model('South America', Colors.red[300]),
      Model('Australia', Colors.orange[300]),
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
                  showLegend: true,
                ),
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  const Model(this.continent, this.color);

  final String continent;
  final Color color;
}

{% endhighlight %}
{% endtabs %}

![Legend icon color](images/legend/legend-icon-color.png)

## Legend text customization

You can customize the legend item's color and text using the [MapColorMapper.text] property of `shapeColorMappers` property in the `MapShapeLayerDelegate`.

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

## Legend customization

You can customize the legend items using the following properties.

* **showIcon** - You can show or hide the legend icon. The default value of the `showIcon` property is `true`.
* **position** - You can position the legend in the different directions. The default value of the `position` property is `MapLegendPosition.top`. The `MapLegendPosition` contains four values such as `left`, `right`, `top`, and `bottom`.
* **overflowMode** - You can wrap or scroll the legend items. The default value of the `overflowMode` property is `MapLegendOverflowMode.wrap`. The `MapLegendOverflowMode` contains two values such as `scroll` and `wrap`. If the legend position is left or right, then scroll direction is vertical and the legend position is top or bottom, then scroll direction is horizontal.
* **iconType** - You can change the icon shape. The default value of the `iconType` property is `MapIconType.circle`. The `MapIconType` contains four values such as `circle`, `square`, `triangle`, and `diamond`.
* **iconSize** - You can change the size of the icon. The default value of the `iconType` is `Size(12.0, 12.0)`.
* **offset** - You can place the legend in custom position. The default value of the `offset` property is `null`.
* **itemsSpacing** - You can provide space between the each legend items. The default value of the `itemsSpacing` is `10.0`.
* **direction** - You can arrange the legend items in either horizontal or vertical direction. It defaults to `horizontal`, if the value of the `position` property is `top`, `bottom` or `null` and defaults to `vertical`, if the value of the `position` property is `left` or `right`.
* **padding** - You can set padding around the legend. The default value of the `padding` property is `EdgeInsets.all(10.0)`.
* **textStyle** - You can customize the legend text style.
* **enableToggleInteraction** - You can enable the toggle interaction for the legend items. The default value of the `enableToggleInteraction` property is `false`.
* **toggledShapeColor** - You can fill the selected legend item icon and it's shape using the `toggledShapeColor` property.
* **toggledShapeStrokeColor** - You can change the stroke color which applies to selected legend item's shape using the `toggledShapeStrokeColor` property.
* **toggledShapeStrokeWidth** - You can change the stroke width which applies to selected legend item's shape using the `toggledShapeStrokeWidth` property.
* **toggledShapeOpacity** - You can set the color opacity to the selected legend item's shape using the `toggledShapeOpacity` property.

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

![Legend items customization](images/legend/legend-items-customization.png)
