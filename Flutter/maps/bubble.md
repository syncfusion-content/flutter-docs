---
layout: post
title: Bubbles in Syncfusion Flutter Maps | Syncfusion
description: This section explains how to show bubbles and customize its appearance in the Flutter maps application.
platform: Flutter
control: SfMaps
documentation: ug
---

# Bubbles in the Flutter Maps

You can add information to shapes such as population density, number of users, and more. Bubbles can be rendered in different colors and sizes based on the data values of their assigned shape.

## Show bubbles

You can show bubbles using the `showBubbles` property in the `MapShapeLayer`. The `bubbleSizeMapper` property of the `MapShapeLayerDelegate` is used to specify the value based on which the bubble's size has to be rendered.

{% tabs %}
{% highlight Dart %}

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
                  bubbleSizeMapper: (int index) => data[index].count
              ),
              showBubbles: true,
            )
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

## Bubbles color

You can customize the bubble color based on the value returned from the `bubbleColorValueMapper` property in the `MapShapeLayerDelegate`. You can either return a value or a color from the `bubbleColorValueMapper`.

If `bubbleColorValueMapper` returns a color, then the color will be applied to the bubble from the underlying model straightaway.

If `bubbleColorValueMapper` returns a value other than the color, then you must set the `MapShapeLayer.bubbleColorMappers` property. The value returned from the `bubbleColorValueMapper` will be used for the comparison in the `MapColorMapper.value` or `MapColorMapper.from` and `MapColorMapper.to`. Then, the `MapColorMapper.color` will be applied to the respective bubble.

{% tabs %}
{% highlight Dart %}

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
                bubbleSizeMapper: (int index) => data[index].count,
                bubbleColorValueMapper: (int index) => data[index].bubbleColor,
                bubbleTooltipTextMapper: (int index) =>
                data[index].count.toStringAsFixed(0) + 'countries',
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
  const Model(this.continent, this.count, this.bubbleColor);

  final String continent;
  final double count;
  final Color bubbleColor;
}

{% endhighlight %}
{% endtabs %}

![Bubble palette](images/bubble/bubble-palette.png)

## Bubbles tooltip

You can enable bubble tooltip using the `MapShapeLayer.enableBubbleTooltip` property. It is used to indicate clearly the information on the current tapped bubble. By default, the bubble tooltip text will be `shapeDataField` values.

N> Refer the `bubbleTooltipTextMapper` for changing the default bubble tooltip text.

{% tabs %}
{% highlight Dart %}

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
                  bubbleSizeMapper: (int index) => data[index].count,
                  bubbleTooltipTextMapper: (int index) => data[index].count.toStringAsFixed(0) + 'countries',
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
  const Model(this.continent, this.count);

  final String continent;
  final double count;
}

{% endhighlight %}
{% endtabs %}

![Bubble tooltip](images/bubble/bubble-tooltip.png)

## Bubbles customization

You can customize the bubbles using the `minRadius`, `maxRadius`, `color`, `strokeWidth`, and `strokeColor` properties in the `bubbleSettings`.

N>
* The default value of the `minRadius` property is `10.0`.
* The default value of the `maxRadius` property is `50.0`.
* The default value of the `opacity` property is `0.75`.

{% tabs %}
{% highlight Dart %}

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
                  bubbleSizeMapper: (int index) => data[index].count,
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
  const Model(this.continent, this.count);

  final String continent;
  final double count;
}

{% endhighlight %}
{% endtabs %}

![Bubble customization](images/bubble/bubble-customization.png)
