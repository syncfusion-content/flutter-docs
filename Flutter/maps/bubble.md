---
layout: post
title: Bubbles in Flutter Maps widget | Syncfusion
description: Learn here all about the Bubbles feature of Syncfusion Flutter Maps (SfMaps) widget to customize their appearances and more.
platform: Flutter
control: SfMaps
documentation: ug
---

# Bubbles in Flutter Maps (SfMaps)

Bubbles can be rendered in different colors and sizes based on the data values of their assigned shape. You can add information to shapes such as population density, number of users, and more. 

## Enable bubbles

You can enable bubbles using the [`MapShapeSource.bubbleSizeMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/bubbleSizeMapper.html). This property is used to specify the value based on which the bubble's size has to be rendered.

{% tabs %}
{% highlight Dart %}

late List<Model> data;
late MapShapeSource dataSource;

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

   dataSource = MapShapeSource.asset(
      "assets/world_map.json",
      shapeDataField: "continent",
      dataCount: data.length,
      primaryValueMapper: (int index) => data[index].continent,
      bubbleSizeMapper: (int index) => data[index].count,
   );
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.only(left: 15, right: 15),
      child: SfMaps(
        layers: [
          MapShapeLayer(
            source: dataSource,
          ),
        ],
      ),
    ),
  );
}

class Model {
  const Model(this.continent, this.count);

  final String continent;
  final double count;
}

{% endhighlight %}
{% endtabs %}

![Bubble support](images/bubble/default-bubble.png)

## Tooltip for the bubbles

You can enable tooltip for the bubbles using the [`MapShapeLayer.bubbleTooltipBuilder`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/bubbleTooltipBuilder.html) property. It can be used to indicate clearly the information about the currently interacted bubble.

{% tabs %}
{% highlight Dart %}

late List<Model> data;
late MapShapeSource dataSource;

@override
void initState() {
  super.initState();

  data = <Model>[
    Model('Asia', 50, '44,579,000 sq. km.'),
    Model('Africa', 54, '30,370,000 sq. km.'),
    Model('Europe', 51, '10,180,000 sq. km.'),
    Model('North America', 23, '24,709,000 sq. km.'),
    Model('South America', 12, '17,840,000 sq. km.'),
    Model('Australia', 14, '8,600,000 sq. km.'),
  ];

  dataSource = MapShapeSource.asset(
    "assets/world_map.json",
     shapeDataField: "continent",
     dataCount: data.length,
     primaryValueMapper: (int index) => data[index].continent,
     bubbleSizeMapper: (int index) => data[index].countriesCount,
  );
}

@override
Widget build(BuildContext context) {
  final ThemeData themeData = Theme.of(context);
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.only(left: 15, right: 15),
      child: SfMaps(
        layers: [
          MapShapeLayer(
            source: dataSource,
            bubbleTooltipBuilder: (BuildContext context, int index) {
               return Padding(
                  padding: EdgeInsets.all(10),
                  child: Text('Continent : ' +
                     data[index].continent +
                     '\nTotal Countries : ' +
                     data[index].countriesCount.toStringAsFixed(0),
                     style: themeData.textTheme.caption!
                        .copyWith(color: themeData.colorScheme.surface)),
               );
            },
          ),
        ],
      ),
    ),
  );
}

class Model {
  const Model(this.continent, this.countriesCount, this.area);

  final String continent;
  final double countriesCount;
  final String area;
}

{% endhighlight %}
{% endtabs %}

![Bubble tooltip](images/bubble/bubble-tooltip.png)

## Color

You can customize the bubble color based on the value returned from the [`MapShapeSource.bubbleColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/bubbleColorValueMapper.html) property. You can either return a value or a color from the [`bubbleColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/bubbleColorValueMapper.html).

If [`bubbleColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/bubbleColorValueMapper.html) returns a color, then the color will be applied to the bubble straightaway.

If [`bubbleColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/bubbleColorValueMapper.html) returns a value other than the color, then you must set the [`MapShapeSource.bubbleColorMappers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/bubbleColorMappers.html) property. The value returned from the [`bubbleColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/bubbleColorValueMapper.html) will be used for the comparison in the [`MapColorMapper.value`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/value.html) or [`MapColorMapper.from`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/from.html) and [`MapColorMapper.to`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/to.html). Then, the [`MapColorMapper.color`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/color.html) will be applied to the respective bubble.

{% tabs %}
{% highlight Dart %}

late List<Model> data;
late MapShapeSource dataSource;

@override
void initState() {
  super.initState();

  data = <Model>[
    Model('Asia', 51, Colors.red[400]!),
    Model('Africa', 58, Colors.green[400]!),
    Model('Europe', 48, Colors.blue[400]!),
    Model('North America', 41, Colors.purple[400]!),
    Model('South America', 14, Colors.yellow[400]!),
    Model('Australia', 23, Colors.orange[400]!),
  ];

  dataSource = MapShapeSource.asset(
     "assets/world_map.json",
     shapeDataField: "continent",
     dataCount: data.length,
     primaryValueMapper: (int index) => data[index].continent,
     bubbleSizeMapper: (int index) => data[index].count,
     bubbleColorValueMapper: (int index) => data[index].bubbleColor,
  );
}

@override
Widget build(BuildContext context) {
   return Scaffold(
     body: Padding(
       padding: EdgeInsets.only(left: 15, right: 15),
       child: SfMaps(
         layers: [
           MapShapeLayer(
             source: dataSource,
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

class Model {
   Model(this.continent, this.count, this.bubbleColor);

  final String continent;
  final double count;
  final Color bubbleColor;
}

{% endhighlight %}
{% endtabs %}

![Bubble palette](images/bubble/bubble-palette.png)

## Appearance customization

You can customize the below appearance of the bubbles.

* **MinRadius** - Change the minimum radius of the bubbles using the [`MapBubbleSettings.minRadius`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapBubbleSettings/minRadius.html) property. The default value of the [`minRadius`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapBubbleSettings/minRadius.html) property is `10.0`.
* **MaxRadius** - Change the maximum radius of the bubbles using the [`MapBubbleSettings.maxRadius`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapBubbleSettings/maxRadius.html) property. The default value of the [`maxRadius`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapBubbleSettings/maxRadius.html) property is `50.0`.
* **Background color** - Change the background color of the bubbles using the [`MapBubbleSettings.color`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapBubbleSettings/color.html) property.
* **Stroke color** - Change the stroke color of the bubbles using the [`MapBubbleSettings.strokeColor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapBubbleSettings/strokeColor.html) property.
* **Stroke width** - Change the stroke width of the bubbles using the [`MapBubbleSettings.strokeWidth`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapBubbleSettings/strokeWidth.html) property.

{% tabs %}
{% highlight Dart %}

late List<Model> data;
late MapShapeSource dataSource;

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

    dataSource = MapShapeSource.asset(
       "assets/world_map.json",
       shapeDataField: "continent",
       dataCount: data.length,
       primaryValueMapper: (int index) => data[index].continent,
       bubbleSizeMapper: (int index) => data[index].count,
    );
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: EdgeInsets.only(left: 15, right: 15),
        child: SfMaps(
          layers: [
            MapShapeLayer(
              source: dataSource,
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
  Model(this.continent, this.count);

  final String continent;
  final double count;
}

{% endhighlight %}
{% endtabs %}

<b>Using SfMapsTheme</b>

You can also customize the below appearance of the bubbles using [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

* **Background color** - Change the background color of the bubbles using the [`SfMapsThemeData.bubbleColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/bubbleColor.html) property.
* **Stroke color** - Change the stroke color of the bubbles using the [`SfMapsThemeData.bubbleStrokeColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/bubbleStrokeColor.html) property.
* **Stroke width** - Change the stroke width of the bubbles using the [`SfMapsThemeData.bubbleStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/bubbleStrokeWidth.html) property.
* **Hover color** - Change the hover color of the bubbles in the web platform using the [`SfMapsThemeData.bubbleHoverColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/bubbleHoverColor.html) property.
* **Hover stroke color** - Change the hover stroke color of the bubbles in the web platform using the [`SfMapsThemeData.bubbleHoverStrokeColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/bubbleHoverStrokeColor.html) property.
* **Hover stroke width** - Change the hover stroke width of the bubbles in the web platform using the [`SfMapsThemeData.bubbleHoverStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/bubbleHoverStrokeWidth.html) property.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

{% tabs %}
{% highlight Dart %}

late List<Model> data;
late MapShapeSource dataSource;

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

   dataSource = MapShapeSource.asset(
     "assets/world_map.json",
      shapeDataField: "continent",
      dataCount: data.length,
      primaryValueMapper: (int index) => data[index].continent,
      bubbleSizeMapper: (int index) => data[index].count,
   );
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: EdgeInsets.only(left: 15, right: 15),
        child: SfMapsTheme(
          data: SfMapsThemeData(
            bubbleColor: Colors.red[200],
            bubbleStrokeColor: Colors.red[800],
            bubbleStrokeWidth: 2,
            bubbleHoverColor: Colors.red[800],
            bubbleHoverStrokeColor: Colors.black,
            bubbleHoverStrokeWidth: 2,
          ),
          child: SfMaps(
            layers: [
              MapShapeLayer(
                source: dataSource,
                bubbleSettings: MapBubbleSettings(
                  maxRadius: 30,
                  minRadius: 15,
                ),
              )
            ],
          ),
        )
      ),
   );
}

class Model {
  Model(this.continent, this.count);

  final String continent;
  final double count;
}

{% endhighlight %}
{% endtabs %}

![Bubble customization](images/bubble/bubble-customization.png)

N> You can refer to our [Flutter Maps](https://www.syncfusion.com/flutter-widgets/flutter-maps) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Maps example](https://flutter.syncfusion.com/#/maps/shape-layer/range-color-mapping) that shows how to configure a Maps in Flutter.