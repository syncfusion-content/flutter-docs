---
layout: post
title: Adding lines in Syncfusion Flutter maps | Syncfusion
description: This section explains about how to add lines on the map and customize its appearance in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Lines in the Flutter maps

Line layer is a sublayer that renders a group of [`MapLine`] on [`MapShapeLayer`] and [`MapTileLayer`]. This section helps to learn about how to add the lines and customize them.

## Adding lines

The [`lines`] is a collection of [`MapLine`]. Every single [`MapLine`] connects two location coordinates through a straight line. The start coordinate is set to [`MapLine.from`] property and the end coordinate is set to [`MapLine.to`] property.

N> It is applicable for both the tile layer and shape layer.

<b>In the shape layer</b>

{% tabs %}
{% highlight Dart %}

MapShapeSource dataSource;
List<DataModel> data;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(56.1304, -106.3468)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-9.1900, -75.0152)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(61.5240, 105.3188)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-25.2744, 133.7751)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.all(10),
      child: SfMaps(layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapLineLayer(
              lines: List<MapLine>.generate(data.length, (int index) {
                return MapLine(
                  from: data[index].from,
                  to: data[index].to,
                );
              }).toSet(),
            ),
          ],
        ),
      ]),
    ),
  );
}

class DataModel {
  DataModel(this.from, this.to);

  final MapLatLng from;
  final MapLatLng to;
}

{% endhighlight %}
{% endtabs %}

<b>In the tile layer</b>

{% tabs %}
{% highlight Dart %}

List<DataModel> data;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(56.1304, -106.3468)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-9.1900, -75.0152)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(61.5240, 105.3188)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-25.2744, 133.7751)),
  ];
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.all(10),
      child: SfMaps(layers: [
        MapTileLayer(
          urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
          sublayers: [
            MapLineLayer(
              lines: List<MapLine>.generate(data.length, (int index) {
                return MapLine(
                  from: data[index].from,
                  to: data[index].to,
                );
              }).toSet(),
            ),
          ],
        ),
      ]),
    ),
  );
}

class DataModel {
  DataModel(this.from, this.to);

  final MapLatLng from;
  final MapLatLng to;
}

{% endhighlight %}
{% endtabs %}

![Default line shape](images/line-layer/default_line_shape.png)

## Color

You can apply the same color for all [`MapLine`] in the [`lines`] collection using the [`MapLineLayer.color`] property. Alternatively, you can apply different colors to each [`MapLine`] in the [`lines`] collection using the individual [`MapLine.color`] property.

{% tabs %}
{% highlight Dart %}

MapShapeSource dataSource;
List<DataModel> data;

@override
void initState() {
  data = <DataModel>[
     DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(56.1304, -106.3468), Colors.redAccent),
     DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-9.1900, -75.0152), Colors.deepPurpleAccent),
     DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(61.5240, 105.3188), Colors.blueAccent),
     DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-25.2744, 133.7751), Colors.teal),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.all(10),
      child: SfMaps(layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapLineLayer(
              lines: List<MapLine>.generate(data.length, (int index) {
                return MapLine(
                  from: data[index].from,
                  to: data[index].to,
                  color: data[index].color,
                );
              }).toSet(),
            ),
          ],
        ),
      ]),
    ),
  );
}

class DataModel {
  DataModel(this.from, this.to, this.color);

  final MapLatLng from;
  final MapLatLng to;
  final Color color;
}

{% endhighlight %}
{% endtabs %}

![Line shape color](images/line-layer/line_shape_color.png)

## Width

You can apply the same width for all [`MapLine`] in the [`lines`] collection using the [`MapLineLayer.width`] property. Alternatively, you can apply different width to each [`MapLine`] in the [`lines`] collection using the individual [`MapLine.width`] property. The default value of the [`MapLineLayer.width`] property is `2`.

{% tabs %}
{% highlight Dart %}

MapShapeSource dataSource;
List<DataModel> data;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(56.1304, -106.3468), 2),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-9.1900, -75.0152), 4),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(61.5240, 105.3188), 5),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-25.2744, 133.7751), 6),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.all(10),
      child: SfMaps(layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapLineLayer(
              lines: List<MapLine>.generate(data.length, (int index) {
                return MapLine(
                  from: data[index].from,
                  to: data[index].to,
                  width: data[index].width,
                );
              }).toSet(),
            ),
          ],
        ),
      ]),
    ),
  );
}

class DataModel {
  DataModel(this.from, this.to, this.width);

  final MapLatLng from;
  final MapLatLng to;
  final double width;
}

{% endhighlight %}
{% endtabs %}

![Line shape width](images/line-layer/line_shape_width.png)

## Dash array

You can apply dash support for the line using the [`MapLine.dashArray`] property.

A sequence of dash and gap will be rendered based on the values in this list. Once all values of the list is rendered, it will be repeated again till the end of the line.

{% tabs %}
{% highlight Dart %}

MapShapeSource dataSource;
List<DataModel> data;

@override
void initState() {
  data = <DataModel>[
     DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(56.1304, -106.3468)),
     DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-9.1900, -75.0152)),
     DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(61.5240, 105.3188)),
     DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-25.2744, 133.7751)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.all(10),
      child: SfMaps(layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapLineLayer(
              lines: List<MapLine>.generate(data.length, (int index) {
                return MapLine(
                  from: data[index].from,
                  to: data[index].to,
                  dashArray: [8, 4, 2, 4],
                );
              }).toSet(),
              color: Colors.blue,
            ),
          ],
        ),
      ]),
    ),
  );
}

class DataModel {
  DataModel(this.from, this.to);

  final MapLatLng from;
  final MapLatLng to;
}

{% endhighlight %}
{% endtabs %}

![Line shape dash array](images/line-layer/line_shape_dash_array.png)

## Animation

You can apply animation for the [`MapLine`] using the [`MapLineLayer.animation`] property and able to customize the animation flow, curve and duration.

By default, there will not be any animation.

{% tabs %}
{% highlight Dart %}

MapShapeSource dataSource;
List<DataModel> data;
AnimationController animationController;
Animation animation;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(56.1304, -106.3468)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-9.1900, -75.0152)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(61.5240, 105.3188)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-25.2744, 133.7751)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );

  animationController = AnimationController(
    duration: Duration(seconds: 3),
    vsync: this,
  );
  animation = CurvedAnimation(
    parent: animationController,
    curve: Curves.easeInOut,
  );
  animationController.forward(from: 0);
  super.initState();
}

@override
void dispose() {
  animationController?.dispose();
  super.dispose();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.all(10),
      child: SfMaps(layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapLineLayer(
              lines: List<MapLine>.generate(data.length, (int index) {
                return MapLine(
                  from: data[index].from,
                  to: data[index].to,
                );
              }).toSet(),
              color: Colors.blue,
              animation: animation,
            ),
          ],
        ),
      ]),
    ),
  );
}

class DataModel {
  DataModel(this.from, this.to);

  final MapLatLng from;
  final MapLatLng to;
}

{% endhighlight %}
{% endtabs %}

![Line shape animation](images/line-layer/line_shape_animation.gif)

## OnTap

You can use the [`onTap`] callback to get a notification if the particular [`MapLine`] is tapped. You can also customize the tapped [`MapLine`] based on the index passed in the callback as shown in the below code snippet.

{% tabs %}
{% highlight Dart %}

MapShapeSource dataSource;
List<DataModel> data;
int selectedIndex;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(56.1304, -106.3468)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-9.1900, -75.0152)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(61.5240, 105.3188)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-25.2744, 133.7751)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.all(10),
      child: SfMaps(layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapLineLayer(
              lines: List<MapLine>.generate(data.length, (int index) {
                return MapLine(
                    from: data[index].from,
                    to: data[index].to,
                    color: selectedIndex == index ? Colors.pink : Colors.blue,
                    onTap: () {
                      setState(() {
                        selectedIndex = index;
                      });
                    });
              }).toSet(),
            ),
          ],
        ),
      ]),
    ),
  );
}

class DataModel {
  DataModel(this.from, this.to);

  final MapLatLng from;
  final MapLatLng to;
}

{% endhighlight %}
{% endtabs %}

![Line shape onTap](images/line-layer/line_shape_onTap.gif)

## Tooltip

You can show additional information about the line drawn using the [`MapLineLayer.tooltipBuilder`] property.

{% tabs %}
{% highlight Dart %}

MapShapeSource dataSource;
List<DataModel> data;
Random random = Random();

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(56.1304, -106.3468)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-9.1900, -75.0152)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(61.5240, 105.3188)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-25.2744, 133.7751)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.all(10),
      child: SfMaps(layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapLineLayer(
              lines: List<MapLine>.generate(data.length, (int index) {
                return MapLine(
                  from: data[index].from,
                  to: data[index].to,
                );
              }).toSet(),
              tooltipBuilder: (BuildContext context, int index) {
                return Container(
                  padding: EdgeInsets.only(left: 5, top: 5),
                  height: 40,
                  width: 100,
                  child: Column(
                    children: [
                      Row(
                        children: [
                          Text('Flight   : '),
                          Text('Air India'),
                        ],
                      ),
                      Row(
                        children: [
                          Text('Depart : '),
                          Text(random.nextInt(12).toString() + 'AM'),
                        ],
                      ),
                    ],
                  ),
                );
              },
            ),
          ],
        ),
      ]),
    ),
  );
}

class DataModel {
  DataModel(this.from, this.to);

  final MapLatLng from;
  final MapLatLng to;
}

{% endhighlight %}
{% endtabs %}

![Line shape tooltip](images/line-layer/line_shape_tooltip.png)

## Tooltip customization

You can customize the appearance of the tooltip.

* Background color - Change the background color of the tooltip in the maps using the [`MapTooltipSettings.color`] property.
* Stroke color - Change the stroke color of the tooltip in the maps using the [`MapTooltipSettings.strokeColor`] property.
* Stroke width - Change the stroke width of the tooltip in the maps using the [`MapTooltipSettings.strokeWidth`] property.

{% tabs %}
{% highlight Dart %}

MapShapeSource dataSource;
List<DataModel> data;
Random random = Random();

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(56.1304, -106.3468)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-9.1900, -75.0152)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(61.5240, 105.3188)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(-25.2744, 133.7751)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.all(10),
      child: SfMaps(layers: [
        MapShapeLayer(
          source: dataSource,
          tooltipSettings: const MapTooltipSettings(
            color: Colors.white,
            strokeWidth: 2,
            strokeColor: Colors.black,
          ),
          sublayers: [
            MapLineLayer(
              lines: List<MapLine>.generate(data.length, (int index) {
                return MapLine(
                  from: data[index].from,
                  to: data[index].to,
                );
              }).toSet(),
              tooltipBuilder: (BuildContext context, int index) {
                return Container(
                  padding: EdgeInsets.only(left: 5, top: 5),
                  height: 40,
                  width: 100,
                  child: Column(
                    children: [
                      Row(
                        children: [
                          Text('Flight   : '),
                          Text('Air India'),
                        ],
                      ),
                      Row(
                        children: [
                          Text('Depart : '),
                          Text(random.nextInt(12).toString() + 'AM'),
                        ],
                      ),
                    ],
                  ),
                );
              },
            ),
          ],
        ),
      ]),
    ),
  );
}

class DataModel {
  DataModel(this.from, this.to);

  final MapLatLng from;
  final MapLatLng to;
}

{% endhighlight %}
{% endtabs %}

![Line shape tooltip customization](images/line-layer/line_shape_tooltip_customization.png)
