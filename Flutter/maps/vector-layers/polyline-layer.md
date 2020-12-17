---
layout: post
title: Adding polylines in Syncfusion Flutter maps | Syncfusion
description: This section explains how to add polylines on the map and customize its appearance in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Polylines in the Flutter maps

Polyline layer is a sublayer that renders a group of [`MapPolyline`] on [`MapShapeLayer`] and [`MapTileLayer`]. This section helps to learn about how to add the polylines and customize them.

## Adding polylines

The [`polylines`] is a collection of [`MapPolyline`]. Every single [`MapPolyline`] connects multiple coordinates through a [`points`] property.

N> It is applicable for both the tile layer and shape layer.

<b>In the shape layer</b>

{% tabs %}
{% highlight Dart %}

List<MapLatLng> polyline;
List<List<MapLatLng>> polylines;
MapShapeSource dataSource;
MapZoomPanBehavior zoomPanBehavior;

@override
void initState() {
  polyline = <MapLatLng>[
    MapLatLng(13.0827, 80.2707),
    MapLatLng(13.1746, 79.6117),
    MapLatLng(13.6373, 79.5037),
    MapLatLng(14.4673, 78.8242),
    MapLatLng(14.9091, 78.0092),
    MapLatLng(16.2160, 77.3566),
    MapLatLng(17.1557, 76.8697),
    MapLatLng(18.0975, 75.4249),
    MapLatLng(18.5204, 73.8567),
    MapLatLng(19.0760, 72.8777),
  ];

  polylines = <List<MapLatLng>>[polyline];
  dataSource = MapShapeSource.asset(
    'assets/india.json',
     shapeDataField: 'name',
  );

  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 3,
    focalLatLng: MapLatLng(15.3173, 76.7139),
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
            MapPolylineLayer(
              polylines: List<MapPolyline>.generate(
                polylines.length,
                (int index) {
                  return MapPolyline(
                    points: polylines[index],
                  );
                },
              ).toSet(),
            ),
          ],
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
    ),
  );
}

class PolylineModel {
  PolylineModel(this.points);
  final List<MapLatLng> points;
}

{% endhighlight %}
{% endtabs %}

<b>In the tile layer</b>

{% tabs %}
{% highlight Dart %}

List<MapLatLng> polyline;
List<List<MapLatLng>> polylines;
MapZoomPanBehavior zoomPanBehavior;

@override
void initState() {
  polyline = <MapLatLng>[
    MapLatLng(13.0827, 80.2707),
    MapLatLng(13.1746, 79.6117),
    MapLatLng(13.6373, 79.5037),
    MapLatLng(14.4673, 78.8242),
    MapLatLng(14.9091, 78.0092),
    MapLatLng(16.2160, 77.3566),
    MapLatLng(17.1557, 76.8697),
    MapLatLng(18.0975, 75.4249),
    MapLatLng(18.5204, 73.8567),
    MapLatLng(19.0760, 72.8777),
  ];

  polylines = <List<MapLatLng>>[polyline];
  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 3,
    focalLatLng: MapLatLng(15.3173, 76.7139),
  );
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
            MapPolylineLayer(
              polylines: List<MapPolyline>.generate(
                polylines.length,
                (int index) {
                  return MapPolyline(
                    points: polylines[index],
                  );
                },
              ).toSet(),
            ),
          ],
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
    ),
  );
}

class PolylineModel {
  PolylineModel(this.points);
  final List<MapLatLng> points;
}

{% endhighlight %}
{% endtabs %}

## Color

You can apply the same color for all [`MapPolyline`] in the [`polylines`] collection using the [`MapPolylineLayer.color`] property. Alternatively, you can apply different colors to each [`MapPolyline`] in the [`polylines`] collection using the individual [`MapPolyline.color`] property.

{% tabs %}
{% highlight Dart %}

List<MapLatLng> polyline;
List<PolylineModel> polylines;
MapShapeSource dataSource;
MapZoomPanBehavior zoomPanBehavior;

@override
void initState() {
  polyline = <MapLatLng>[
    MapLatLng(13.0827, 80.2707),
    MapLatLng(13.1746, 79.6117),
    MapLatLng(13.6373, 79.5037),
    MapLatLng(14.4673, 78.8242),
    MapLatLng(14.9091, 78.0092),
    MapLatLng(16.2160, 77.3566),
    MapLatLng(17.1557, 76.8697),
    MapLatLng(18.0975, 75.4249),
    MapLatLng(18.5204, 73.8567),
    MapLatLng(19.0760, 72.8777),
  ];

  polylines = <PolylineModel>[
    PolylineModel(polyline, Colors.purple),
  ];
  dataSource = MapShapeSource.asset(
    'assets/india.json',
    shapeDataField: 'name',
  );

  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 3,
    focalLatLng: MapLatLng(15.3173, 76.7139),
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
            MapPolylineLayer(
              polylines: List<MapPolyline>.generate(
                polylines.length,
                (int index) {
                  return MapPolyline(
                    points: polylines[index].points,
                    color: polylines[index].color,
                  );
                },
              ).toSet(),
            ),
          ],
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
    ),
  );
}

class PolylineModel {
  PolylineModel(this.points, this.color);
  final List<MapLatLng> points;
  final Color color;
}

{% endhighlight %}
{% endtabs %}

## Width

You can apply the same width for all [`MapPolyline`] in the [`polylines`] collection using the [`MapPolylineLayer.width`] property. Alternatively, you can apply different width to each [`MapPolyline`] in the [`polylines`] collection using the individual [`MapPolyline.width`] property. The default value of the [`MapPolylineLayer.width`] property is `2`.

{% tabs %}
{% highlight Dart %}

List<MapLatLng> polyline;
List<PolylineModel> polylines;
MapShapeSource dataSource;
MapZoomPanBehavior zoomPanBehavior;

@override
void initState() {
  polyline = <MapLatLng>[
    MapLatLng(13.0827, 80.2707),
    MapLatLng(13.1746, 79.6117),
    MapLatLng(13.6373, 79.5037),
    MapLatLng(14.4673, 78.8242),
    MapLatLng(14.9091, 78.0092),
    MapLatLng(16.2160, 77.3566),
    MapLatLng(17.1557, 76.8697),
    MapLatLng(18.0975, 75.4249),
    MapLatLng(18.5204, 73.8567),
    MapLatLng(19.0760, 72.8777),
  ];

  polylines = <PolylineModel>[
    PolylineModel(polyline, 3),
  ];
  dataSource = MapShapeSource.asset(
    'assets/india.json',
    shapeDataField: 'name',
  );

  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 3,
    focalLatLng: MapLatLng(15.3173, 76.7139),
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
            MapPolylineLayer(
              polylines: List<MapPolyline>.generate(
                polylines.length,
                (int index) {
                  return MapPolyline(
                    points: polylines[index].points,
                    width: polylines[index].width,
                  );
                },
              ).toSet(),
            ),
          ],
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
    ),
  );
}

class PolylineModel {
  PolylineModel(this.points, this.width);
  final List<MapLatLng> points;
  final double width;
}

{% endhighlight %}
{% endtabs %}

## Dash array

You can apply dash for the polyline using the [`MapPolyline.dashArray`] property.

A sequence of dash and gap will be rendered based on the values in this list. Once all values of the list is rendered, it will be repeated again till the end of the polyline.

{% tabs %}
{% highlight Dart %}

List<MapLatLng> polyline;
List<PolylineModel> polylines;
MapShapeSource dataSource;
MapZoomPanBehavior zoomPanBehavior;

@override
void initState() {
  polyline = <MapLatLng>[
    MapLatLng(13.0827, 80.2707),
    MapLatLng(13.1746, 79.6117),
    MapLatLng(13.6373, 79.5037),
    MapLatLng(14.4673, 78.8242),
    MapLatLng(14.9091, 78.0092),
    MapLatLng(16.2160, 77.3566),
    MapLatLng(17.1557, 76.8697),
    MapLatLng(18.0975, 75.4249),
    MapLatLng(18.5204, 73.8567),
    MapLatLng(19.0760, 72.8777),
  ];

  polylines = <PolylineModel>[
    PolylineModel(polyline),
  ];
  dataSource = MapShapeSource.asset(
    'assets/india.json',
    shapeDataField: 'name',
  );

  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 3,
    focalLatLng: MapLatLng(15.3173, 76.7139),
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
            MapPolylineLayer(
              polylines: List<MapPolyline>.generate(
                polylines.length,
                (int index) {
                  return MapPolyline(
                    points: polylines[index].points,
                    dashArray: [8, 4, 2, 4],
                  );
                },
              ).toSet(),
            ),
          ],
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
    ),
  );
}

class PolylineModel {
  PolylineModel(this.points);
  final List<MapLatLng> points;
}

{% endhighlight %}
{% endtabs %}

![Line shape dash array](images/line-layer/line_shape_dash_array.png)

## Animation

You can apply animation for the [`MapPolyline`] using the [`MapPolylineLayer.animation`] property and able to customize the animation flow, curve and duration.

By default, there will not be any animation.

{% tabs %}
{% highlight Dart %}

List<MapLatLng> polyline;
List<PolylineModel> polylines;
MapShapeSource dataSource;
MapZoomPanBehavior zoomPanBehavior;
AnimationController animationController;
Animation animation;

@override
void initState() {
  polyline = <MapLatLng>[
    MapLatLng(13.0827, 80.2707),
    MapLatLng(13.1746, 79.6117),
    MapLatLng(13.6373, 79.5037),
    MapLatLng(14.4673, 78.8242),
    MapLatLng(14.9091, 78.0092),
    MapLatLng(16.2160, 77.3566),
    MapLatLng(17.1557, 76.8697),
    MapLatLng(18.0975, 75.4249),
    MapLatLng(18.5204, 73.8567),
    MapLatLng(19.0760, 72.8777),
  ];

  polylines = <PolylineModel>[
    PolylineModel(polyline),
  ];
  dataSource = MapShapeSource.asset(
    'assets/india.json',
    shapeDataField: 'name',
  );

  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 3,
    focalLatLng: MapLatLng(15.3173, 76.7139),
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
    body: SfMaps(
      layers: [
        MapShapeLayer(
          source: dataSource,
          sublayers: [
            MapPolylineLayer(
              polylines: List<MapPolyline>.generate(
                polylines.length,
                (int index) {
                  return MapPolyline(
                    points: polylines[index].points,
                    dashArray: [8, 4, 2, 4],
                  );
                },
              ).toSet(),
              animation: animation,
            ),
          ],
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
    ),
  );
}

class PolylineModel {
  PolylineModel(this.points);
  final List<MapLatLng> points;
}

{% endhighlight %}
{% endtabs %}

## OnTap

You can use the [`onTap`] callback to get a notification if the particular [`MapPolyline`] is tapped. You can also customize the tapped [`MapPolyline`] based on the index passed in the callback as shown in the below code snippet.

{% tabs %}
{% highlight Dart %}

List<MapLatLng> polyline;
List<PolylineModel> polylines;
MapShapeSource dataSource;
MapZoomPanBehavior zoomPanBehavior;
int selectedIndex;

@override
void initState() {
  polyline = <MapLatLng>[
    MapLatLng(13.0827, 80.2707),
    MapLatLng(13.1746, 79.6117),
    MapLatLng(13.6373, 79.5037),
    MapLatLng(14.4673, 78.8242),
    MapLatLng(14.9091, 78.0092),
    MapLatLng(16.2160, 77.3566),
    MapLatLng(17.1557, 76.8697),
    MapLatLng(18.0975, 75.4249),
    MapLatLng(18.5204, 73.8567),
    MapLatLng(19.0760, 72.8777),
  ];

  polylines = <PolylineModel>[
    PolylineModel(polyline),
  ];
  dataSource = MapShapeSource.asset(
    'assets/india.json',
    shapeDataField: 'name',
  );

  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 3,
    focalLatLng: MapLatLng(15.3173, 76.7139),
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
            MapPolylineLayer(
              polylines: List<MapPolyline>.generate(
                polylines.length,
                (int index) {
                  return MapPolyline(
                    points: polylines[index].points,
                    color: selectedIndex == index ? Colors.pink: Colors.blue,
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
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
    ),
  );
}

class PolylineModel {
  PolylineModel(this.points);
  final List<MapLatLng> points;
}

{% endhighlight %}
{% endtabs %}

## Tooltip

You can show additional information about the polyline drawn using the [`MapPolylineLayer.tooltipBuilder`] property.

{% tabs %}
{% highlight Dart %}

List<MapLatLng> polyline;
List<PolylineModel> polylines;
MapShapeSource dataSource;
MapZoomPanBehavior zoomPanBehavior;
Random random = Random();

@override
void initState() {
  polyline = <MapLatLng>[
    MapLatLng(13.0827, 80.2707),
    MapLatLng(13.1746, 79.6117),
    MapLatLng(13.6373, 79.5037),
    MapLatLng(14.4673, 78.8242),
    MapLatLng(14.9091, 78.0092),
    MapLatLng(16.2160, 77.3566),
    MapLatLng(17.1557, 76.8697),
    MapLatLng(18.0975, 75.4249),
    MapLatLng(18.5204, 73.8567),
    MapLatLng(19.0760, 72.8777),
  ];

  polylines = <PolylineModel>[
    PolylineModel(polyline),
  ];
  dataSource = MapShapeSource.asset(
    'assets/india.json',
    shapeDataField: 'name',
  );

  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 3,
    focalLatLng: MapLatLng(15.3173, 76.7139),
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
            MapPolylineLayer(
              polylines: List<MapPolyline>.generate(
                polylines.length,
                (int index) {
                  return MapPolyline(
                    points: polylines[index].points,
                  );
                },
              ).toSet(),
              tooltipBuilder: (BuildContext context, int index) {
                 return Container(
                    padding: EdgeInsets.only(left: 15, top: 10),
                       width: 150,
                       height: 50,
                       child: Column(
                          children: [
                            Row(
                              children: [
                                Text('Order item :  ',
                                   style: TextStyle(fontWeight: FontWeight.bold)),
                                Text('Pizza'),
                              ],
                            ),
                            Row(
                               children: [
                                  Text('Time left    :  ',
                                      style: TextStyle(fontWeight: FontWeight.bold)),
                                  Text(random.nextInt(30).toString() + ' mins'),
                               ],
                            ),
                          ],
                       ),
                    );
                 },
            ),
          ],
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
    ),
  );
}

class PolylineModel {
  PolylineModel(this.points);
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

List<MapLatLng> polyline;
List<PolylineModel> polylines;
MapShapeSource dataSource;
MapZoomPanBehavior zoomPanBehavior;
Random random = Random();

@override
void initState() {
  polyline = <MapLatLng>[
    MapLatLng(13.0827, 80.2707),
    MapLatLng(13.1746, 79.6117),
    MapLatLng(13.6373, 79.5037),
    MapLatLng(14.4673, 78.8242),
    MapLatLng(14.9091, 78.0092),
    MapLatLng(16.2160, 77.3566),
    MapLatLng(17.1557, 76.8697),
    MapLatLng(18.0975, 75.4249),
    MapLatLng(18.5204, 73.8567),
    MapLatLng(19.0760, 72.8777),
  ];

  polylines = <PolylineModel>[
    PolylineModel(polyline),
  ];
  dataSource = MapShapeSource.asset(
    'assets/india.json',
    shapeDataField: 'name',
  );

  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 3,
    focalLatLng: MapLatLng(15.3173, 76.7139),
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
          tooltipSettings: MapTooltipSettings(
            color: Colors.white,
            strokeWidth: 2,
            strokeColor: Colors.black,
          ),
          sublayers: [
            MapPolylineLayer(
              polylines: List<MapPolyline>.generate(
                polylines.length,
                (int index) {
                  return MapPolyline(
                    points: polylines[index].points,
                  );
                },
              ).toSet(),
              tooltipBuilder: (BuildContext context, int index) {
                 return Container(
                    padding: EdgeInsets.only(left: 15, top: 10),
                       width: 150,
                       height: 50,
                       child: Column(
                          children: [
                            Row(
                              children: [
                                Text('Order item :  ',
                                   style: TextStyle(fontWeight: FontWeight.bold)),
                                Text('Pizza'),
                              ],
                            ),
                            Row(
                               children: [
                                  Text('Time left    :  ',
                                      style: TextStyle(fontWeight: FontWeight.bold)),
                                  Text(random.nextInt(30).toString() + ' mins'),
                               ],
                            ),
                          ],
                       ),
                    );
                 },
            ),
          ],
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
    ),
  );
}

class PolylineModel {
  PolylineModel(this.points);
  final List<MapLatLng> points;
}

{% endhighlight %}
{% endtabs %}
