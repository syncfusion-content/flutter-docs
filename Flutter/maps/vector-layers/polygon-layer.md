---
layout: post
title: Adding polygons in Syncfusion Flutter maps | Syncfusion
description: This section explains how to add polygons on the map and customize its appearance in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Polygons in the Flutter maps

Polygon layer is a sublayer that renders a group of [`MapPolygon`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPolygon-class.html) on [`MapShapeLayer`] and [`MapTileLayer`]. This section helps to learn about how to add the polygons and customize them.

## Adding polygons

The [`polygons`] is a collection of [`MapPolygon`]. Every single [`MapPolygon`] connects multiple coordinates through a [`points`] property.

N> It is applicable for both the tile layer and shape layer.

<b>In the shape layer</b>

{% tabs %}
{% highlight Dart %}

List<PolygonModel> polygons;
List<MapLatLng> polygon1;
List<MapLatLng> polygon2;
MapShapeSource dataSource;

@override
void initState() {
    polygon1 = <MapLatLng>[
      MapLatLng(55.7558, 37.6173),
      MapLatLng(54.9833, 82.8964),
      MapLatLng(47.2357, 39.7015),
    ];

    polygon2 = <MapLatLng>[
      MapLatLng(64.2823, -135.0000),
      MapLatLng(51.2538, -85.3232),
      MapLatLng(48.4284, -123.3656),
    ];

    polygons = <PolygonModel>[
      PolygonModel(polygon1),
      PolygonModel(polygon2),
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
    body: SfMaps(
      layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapPolygonLayer(
              polygons: List<MapPolygon>.generate(
                polygons.length,
                (int index) {
                  return MapPolygon(
                    points: polygons[index].points,
                  );
                },
              ).toSet(),
            ),
          ],
        ),
      ],
    ),
  );
}

class PolygonModel {
  PolygonModel(this.points);
  final List<MapLatLng> points;
}

{% endhighlight %}
{% endtabs %}

<b>In the tile layer</b>

{% tabs %}
{% highlight Dart %}

List<PolygonModel> polygons;
List<MapLatLng> polygon1;
List<MapLatLng> polygon2;

@override
void initState() {
    polygon1 = <MapLatLng>[
      MapLatLng(55.7558, 37.6173),
      MapLatLng(54.9833, 82.8964),
      MapLatLng(47.2357, 39.7015),
    ];

    polygon2 = <MapLatLng>[
      MapLatLng(64.2823, -135.0000),
      MapLatLng(51.2538, -85.3232),
      MapLatLng(48.4284, -123.3656),
    ];

    polygons = <PolygonModel>[
      PolygonModel(polygon1),
      PolygonModel(polygon2),
    ];
    super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfMaps(
      layers: [
        MapTileLayer(
          urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
          sublayers: [
            MapPolygonLayer(
              polygons: List<MapPolygon>.generate(
                polygons.length,
                (int index) {
                  return MapPolygon(
                    points: polygons[index].points,
                  );
                },
              ).toSet(),
            ),
          ],
        ),
      ],
    ),
  );
}

class PolygonModel {
  PolygonModel(this.points);
  final List<MapLatLng> points;
}

{% endhighlight %}
{% endtabs %}

## Fill color

You can apply the same color for all [`MapPolygon`] in the [`polygons`] collection using the [`MapPolygonLayer.color`] property. Alternatively, you can apply different colors to each [`MapPolygon`] in the [`polygons`] collection using the individual [`MapPolygon.color`] property.

{% tabs %}
{% highlight Dart %}

List<PolygonModel> polygons;
List<MapLatLng> polygon1;
List<MapLatLng> polygon2;
MapShapeSource dataSource;

@override
void initState() {
    polygon1 = <MapLatLng>[
      MapLatLng(55.7558, 37.6173),
      MapLatLng(54.9833, 82.8964),
      MapLatLng(47.2357, 39.7015),
    ];

    polygon2 = <MapLatLng>[
      MapLatLng(64.2823, -135.0000),
      MapLatLng(51.2538, -85.3232),
      MapLatLng(48.4284, -123.3656),
    ];

    polygons = <PolygonModel>[
       PolygonModel(polygon1, Colors.greenAccent),
       PolygonModel(polygon2, Colors.pinkAccent),
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
    body: SfMaps(
      layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapPolygonLayer(
              polygons: List<MapPolygon>.generate(
                polygons.length,
                (int index) {
                  return MapPolygon(
                    points: polygons[index].points,
                    color: polygons[index].color,
                  );
                },
              ).toSet(),
            ),
          ],
        ),
      ],
    ),
  );
}

class PolygonModel {
  PolygonModel(this.points, this.color);
  final List<MapLatLng> points;
  final Color color;
}

{% endhighlight %}
{% endtabs %}

## Stroke width and color

You can apply the same stroke width for all [`MapPolygon`] in the [`polygons`] collection using the [`MapPolygonLayer.strokeWidth`] property. Alternatively, you can apply different stroke width to each [`MapPolygon`] in the [`polygons`] collection using the individual [`MapPolygon.strokeWidth`] property. The default value of the [`MapPolygonLayer.strokeWidth`] property is `2`.

You can apply the same stroke color for all [`MapPolygon`] in the [`polygons`] collection using the [`MapPolygonLayer.strokeColor`] property. Alternatively, you can apply different stroke color to each [`MapPolygon`] in the [`polygons`] collection using the individual [`MapPolygon.strokeColor`] property.

{% tabs %}
{% highlight Dart %}

List<PolygonModel> polygons;
List<MapLatLng> polygon1;
List<MapLatLng> polygon2;
MapShapeSource dataSource;

@override
void initState() {
    polygon1 = <MapLatLng>[
      MapLatLng(55.7558, 37.6173),
      MapLatLng(54.9833, 82.8964),
      MapLatLng(47.2357, 39.7015),
    ];

    polygon2 = <MapLatLng>[
      MapLatLng(64.2823, -135.0000),
      MapLatLng(51.2538, -85.3232),
      MapLatLng(48.4284, -123.3656),
    ];

    polygons = <PolygonModel>[
       PolygonModel(polygon1, 3),
       PolygonModel(polygon2, 4),
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
    body: SfMaps(
      layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapPolygonLayer(
              polygons: List<MapPolygon>.generate(
                polygons.length,
                (int index) {
                  return MapPolygon(
                    points: polygons[index].points,
                    strokeWidth: polygons[index].width,
                    strokeColor: Colors.pink,
                  );
                },
              ).toSet(),
            ),
          ],
        ),
      ],
    ),
  );
}

class PolygonModel {
  PolygonModel(this.points, this.width);
  final List<MapLatLng> points;
  final double width;
}

{% endhighlight %}
{% endtabs %}

## Tap

You can use the [`onTap`] callback to get a notification if the particular [`MapPolygon`] is tapped. You can also customize the tapped [`MapPolygon`] based on the index passed in the callback as shown in the below code snippet.

{% tabs %}
{% highlight Dart %}

List<PolygonModel> polygons;
List<MapLatLng> polygon1;
List<MapLatLng> polygon2;
MapShapeSource dataSource;
int selectedIndex;

@override
void initState() {
    polygon1 = <MapLatLng>[
      MapLatLng(55.7558, 37.6173),
      MapLatLng(54.9833, 82.8964),
      MapLatLng(47.2357, 39.7015),
    ];

    polygon2 = <MapLatLng>[
      MapLatLng(64.2823, -135.0000),
      MapLatLng(51.2538, -85.3232),
      MapLatLng(48.4284, -123.3656),
    ];

    polygons = <PolygonModel>[
      PolygonModel(polygon1),
      PolygonModel(polygon2),
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
    body: SfMaps(
      layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapPolygonLayer(
              polygons: List<MapPolygon>.generate(
                polygons.length,
                (int index) {
                  return MapPolygon(
                    points: polygons[index].points,
                    color: selectedIndex == index ? Colors.pink : Colors.blue,
                    onTap: () {
                       setState(() {
                         selectedIndex = index;
                       });
                    }
                  );
                },
              ).toSet(),
            ),
          ],
        ),
      ],
    ),
  );
}

class PolygonModel {
  PolygonModel(this.points);
  final List<MapLatLng> points;
}

{% endhighlight %}
{% endtabs %}

## Tooltip

You can show additional information about the polygon drawn using the [`MapPolygonLayer.tooltipBuilder`] property.

{% tabs %}
{% highlight Dart %}

List<PolygonModel> polygons;
List<MapLatLng> polygon1;
List<MapLatLng> polygon2;
MapShapeSource dataSource;

@override
void initState() {
    polygon1 = <MapLatLng>[
      MapLatLng(55.7558, 37.6173),
      MapLatLng(54.9833, 82.8964),
      MapLatLng(47.2357, 39.7015),
    ];

    polygon2 = <MapLatLng>[
      MapLatLng(64.2823, -135.0000),
      MapLatLng(51.2538, -85.3232),
      MapLatLng(48.4284, -123.3656),
    ];

    polygons = <PolygonModel>[
      PolygonModel(polygon1),
      PolygonModel(polygon2),
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
    body: SfMaps(
      layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapPolygonLayer(
              polygons: List<MapPolygon>.generate(
                polygons.length,
                (int index) {
                  return MapPolygon(
                    points: polygons[index].points,
                  );
                },
              ).toSet(),
              tooltipBuilder: (BuildContext context, int index) {
                 return Padding(
                    padding: EdgeInsets.all(10),
                    child: Text('Luxurious \n restaurant'),
                 );
              },
            ),
          ],
        ),
      ],
    ),
  );
}

class PolygonModel {
  PolygonModel(this.points);
  final List<MapLatLng> points;
}

{% endhighlight %}
{% endtabs %}

## Tooltip customization

You can customize the appearance of the tooltip.

* Background color - Change the background color of the tooltip in the maps using the [`MapTooltipSettings.color`] property.
* Stroke color - Change the stroke color of the tooltip in the maps using the [`MapTooltipSettings.strokeColor`] property.
* Stroke width - Change the stroke width of the tooltip in the maps using the [`MapTooltipSettings.strokeWidth`] property.

{% tabs %}
{% highlight Dart %}

List<PolygonModel> polygons;
List<MapLatLng> polygon1;
List<MapLatLng> polygon2;
MapShapeSource dataSource;

@override
void initState() {
    polygon1 = <MapLatLng>[
      MapLatLng(55.7558, 37.6173),
      MapLatLng(54.9833, 82.8964),
      MapLatLng(47.2357, 39.7015),
    ];

    polygon2 = <MapLatLng>[
      MapLatLng(64.2823, -135.0000),
      MapLatLng(51.2538, -85.3232),
      MapLatLng(48.4284, -123.3656),
    ];

    polygons = <PolygonModel>[
      PolygonModel(polygon1),
      PolygonModel(polygon2),
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
    body: SfMaps(
      layers: [
        MapShapeLayer(
          source: dataSource,
          tooltipSettings: const MapTooltipSettings(
            color: Colors.white,
            strokeColor: Colors.black,
            strokeWidth: 2,
          ),
          sublayers: [
            MapPolygonLayer(
              polygons: List<MapPolygon>.generate(
                polygons.length,
                (int index) {
                  return MapPolygon(
                    points: polygons[index].points,
                  );
                },
              ).toSet(),
              tooltipBuilder: (BuildContext context, int index) {
                 return Padding(
                    padding: EdgeInsets.all(10),
                    child: Text('Luxurious \n restaurant'),
                 );
              },
            ),
          ],
        ),
      ],
    ),
  );
}

class PolygonModel {
  PolygonModel(this.points);
  final List<MapLatLng> points;
}

{% endhighlight %}
{% endtabs %}
