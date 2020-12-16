---
layout: post
title: Arc shape in Syncfusion Flutter maps | Syncfusion
description: This section explains how to add arc shape on the map and customize its appearance in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Arc shape features in maps

Arc shape is used to connect two location on the map with curved path and its customization.

## Arcs

The [`arcs`] is a collection of [`MapArc`]. Every single [`MapArc`] connects two location coordinates through a curved line. The start coordinate is set to [`MapArc.from`] property and the end coordinate is set to [`MapArc.to`] property.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior zoomPanBehavior;
MapShapeSource dataSource;
List<DataModel> data;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.6139, 77.2090), MapLatLng(39.9042, 116.4074)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(31.2304, 121.4737)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(23.1291, 113.2644)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(19.0760, 72.8777), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(22.3193, 114.1694), MapLatLng(13.0827, 80.2707)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 4,
    focalLatLng: MapLatLng(22.9734, 90.6569),
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
            MapArcLayer(
              arcs: List<MapArc>.generate(
                data.length,
                    (int index) {
                  return MapArc(
                    from: data[index].from,
                    to: data[index].to,
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

class DataModel {
  DataModel(this.from, this.to);

  final MapLatLng from;
  final MapLatLng to;
}

{% endhighlight %}
{% endtabs %}

## Height factor

The [`heightFactor`] is the distance from the line connecting two points to the arc bend point. The default value of [`heightFactor`] property is `0.2` and the value ranges from -1 to 1.

By default, the arc will always render above the [`MapArc.from`] and [`MapArc.to`] points. To render the arc below the points, set the value between -1 to 0.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior zoomPanBehavior;
MapShapeSource dataSource;
List<DataModel> data;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.6139, 77.2090), MapLatLng(39.9042, 116.4074)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(31.2304, 121.4737)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(23.1291, 113.2644)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(19.0760, 72.8777), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(22.3193, 114.1694), MapLatLng(13.0827, 80.2707)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 4,
    focalLatLng: MapLatLng(22.9734, 90.6569),
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
            MapArcLayer(
              arcs: List<MapArc>.generate(
                data.length,
                    (int index) {
                  return MapArc(
                    from: data[index].from,
                    to: data[index].to,
                    heightFactor: -0.2,
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

class DataModel {
  DataModel(this.from, this.to);

  final MapLatLng from;
  final MapLatLng to;
}

{% endhighlight %}
{% endtabs %}

## Control point factor

The [`MapArc.controlPointFactor`] is the arc bending position. The default value of [`MapArc.controlPointFactor`] property is `0.5` and the value ranges from 0 to 1.

By default, the arc will bend at the center between the [`MapArc.from`] and [`MapArc.to`] points.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior zoomPanBehavior;
MapShapeSource dataSource;
List<DataModel> data;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.6139, 77.2090), MapLatLng(39.9042, 116.4074)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(31.2304, 121.4737)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(23.1291, 113.2644)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(19.0760, 72.8777), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(22.3193, 114.1694), MapLatLng(13.0827, 80.2707)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 4,
    focalLatLng: MapLatLng(22.9734, 90.6569),
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
            MapArcLayer(
              arcs: List<MapArc>.generate(
                data.length,
                    (int index) {
                  return MapArc(
                    from: data[index].from,
                    to: data[index].to,
                    controlPointFactor: 0.2,
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

class DataModel {
  DataModel(this.from, this.to);

  final MapLatLng from;
  final MapLatLng to;
}

{% endhighlight %}
{% endtabs %}

## Color

You can apply single color for all [`MapArc`] in the [`arcs`] collection using the [`MapArcLayer.color`] property. Also, you can apply different color to the each [`MapArc`] in the [`arcs`] collection using the [`MapArc.color`] property.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior zoomPanBehavior;
MapShapeSource dataSource;
List<DataModel> data;

@override
void initState() {
 data = <DataModel>[
   DataModel(MapLatLng(28.6139, 77.2090), MapLatLng(39.9042, 116.4074), Colors.redAccent),
   DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(31.2304, 121.4737), Colors.purpleAccent),
   DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(23.1291, 113.2644), Colors.deepOrangeAccent),
   DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(22.3193, 114.1694), Colors.deepOrangeAccent),
   DataModel(MapLatLng(19.0760, 72.8777), MapLatLng(22.3193, 114.1694), Colors.blueAccent),
   DataModel(MapLatLng(22.3193, 114.1694), MapLatLng(13.0827, 80.2707), Colors.teal),
 ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 4,
    focalLatLng: MapLatLng(22.9734, 90.6569),
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
            MapArcLayer(
              arcs: List<MapArc>.generate(
                data.length,
                    (int index) {
                  return MapArc(
                    from: data[index].from,
                    to: data[index].to,
                    color: data[index].color,
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

class DataModel {
  DataModel(this.from, this.to, this.color);

  final MapLatLng from;
  final MapLatLng to;
  final Color color;
}

## Width

You can apply same width for all [`MapArc`] in the [`arcs`] collection using the [`MapArc.width`] property. Also, you can apply different width to the each [`MapArc`] in the [`arcs`] collection using the [`MapArc.width`] property. The default value of the [`MapArcLayer.width`] property is `2`.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior zoomPanBehavior;
MapShapeSource dataSource;
List<DataModel> data;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.6139, 77.2090), MapLatLng(39.9042, 116.4074), 2),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(31.2304, 121.4737), 3),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(23.1291, 113.2644), 2),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(22.3193, 114.1694), 4),
    DataModel(MapLatLng(19.0760, 72.8777), MapLatLng(22.3193, 114.1694), 5),
    DataModel(MapLatLng(22.3193, 114.1694), MapLatLng(13.0827, 80.2707), 6),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 4,
    focalLatLng: MapLatLng(22.9734, 90.6569),
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
            MapArcLayer(
              arcs: List<MapArc>.generate(
                data.length,
                    (int index) {
                  return MapArc(
                    from: data[index].from,
                    to: data[index].to,
                    width: data[index].width,
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

class DataModel {
  DataModel(this.from, this.to, this.width);

  final MapLatLng from;
  final MapLatLng to;
  final double width;
}

{% endhighlight %}
{% endtabs %}

## Dash array

You can apply dash support for the arc using the [MapArc.dashArray] property. The default value of [MapArc.dashArray] is [0, 0].

A sequence of dash and gap will be rendered based on the values in this list. Once all values of the list is rendered, it will be repeated again till the end of the arc.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior zoomPanBehavior;
MapShapeSource dataSource;
List<DataModel> data;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.6139, 77.2090), MapLatLng(39.9042, 116.4074)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(31.2304, 121.4737)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(23.1291, 113.2644)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(19.0760, 72.8777), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(22.3193, 114.1694), MapLatLng(13.0827, 80.2707)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 4,
    focalLatLng: MapLatLng(22.9734, 90.6569),
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
            MapArcLayer(
              arcs: List<MapArc>.generate(
                data.length,
                    (int index) {
                  return MapArc(
                    from: data[index].from,
                    to: data[index].to,
                    dashArray: [8, 4, 2, 4],
                  );
                },
              ).toSet(),
              color: Colors.blue,
            ),
          ],
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
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

## Animation

You can apply animation for the [`MapArc`] using the [`MapArcLayer.animation`] property and able to customize the animation flow, curve and duration.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior zoomPanBehavior;
MapShapeSource dataSource;
List<DataModel> data;
AnimationController animationController;
Animation animation;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.6139, 77.2090), MapLatLng(39.9042, 116.4074)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(31.2304, 121.4737)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(23.1291, 113.2644)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(19.0760, 72.8777), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(22.3193, 114.1694), MapLatLng(13.0827, 80.2707)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 4,
    focalLatLng: MapLatLng(22.9734, 90.6569),
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
            MapArcLayer(
              arcs: List<MapArc>.generate(
                data.length,
                (int index) {
                  return MapArc(
                    from: data[index].from,
                    to: data[index].to,
                  );
                },
              ).toSet(),
              color: Colors.blue,
              animation: animation,
            ),
          ],
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
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

## OnTap

You can use the ['onTap'] callback to customize the taped ['MapArc'] based on the arc index. The callback was called when the user clicked on the arc.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior zoomPanBehavior;
MapShapeSource dataSource;
List<DataModel> data;
int selectedIndex;

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.6139, 77.2090), MapLatLng(39.9042, 116.4074)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(31.2304, 121.4737)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(23.1291, 113.2644)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(19.0760, 72.8777), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(22.3193, 114.1694), MapLatLng(13.0827, 80.2707)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 4,
    focalLatLng: MapLatLng(22.9734, 90.6569),
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
            MapArcLayer(
              arcs: List<MapArc>.generate(
                data.length,
                    (int index) {
                  return MapArc(
                    from: data[index].from,
                    to: data[index].to,
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
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
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

## Tooltip

You can show information about the arc drawn using the [`MapArcLayer.tooltipBuilder`] property.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior zoomPanBehavior;
MapShapeSource dataSource;
List<DataModel> data;
int selectedIndex;
Random random = Random();

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.6139, 77.2090), MapLatLng(39.9042, 116.4074)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(31.2304, 121.4737)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(23.1291, 113.2644)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(19.0760, 72.8777), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(22.3193, 114.1694), MapLatLng(13.0827, 80.2707)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 4,
    focalLatLng: MapLatLng(22.9734, 90.6569),
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
            MapArcLayer(
              arcs: List<MapArc>.generate(
                data.length,
                    (int index) {
                  return MapArc(
                    from: data[index].from,
                    to: data[index].to,
                  );
                },
              ).toSet(),
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
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
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

## Tooltip customization

You can customize the appearance of the tooltip.

Background color - Change the background color of the tooltip in the maps using the [`MapTooltipSettings.color`] property.
Stroke color - Change the stroke color of the tooltip in the maps using the [`MapTooltipSettings.strokeColor`] property.
Stroke width - Change the stroke width of the tooltip in the maps using the [`MapTooltipSettings.strokeWidth`] property.

{% tabs %}
{% highlight Dart %}


MapZoomPanBehavior zoomPanBehavior;
MapShapeSource dataSource;
List<DataModel> data;
int selectedIndex;
Random random = Random();

@override
void initState() {
  data = <DataModel>[
    DataModel(MapLatLng(28.6139, 77.2090), MapLatLng(39.9042, 116.4074)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(31.2304, 121.4737)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(23.1291, 113.2644)),
    DataModel(MapLatLng(28.7041, 77.1025), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(19.0760, 72.8777), MapLatLng(22.3193, 114.1694)),
    DataModel(MapLatLng(22.3193, 114.1694), MapLatLng(13.0827, 80.2707)),
  ];

  dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  zoomPanBehavior = MapZoomPanBehavior(
    zoomLevel: 4,
    focalLatLng: MapLatLng(22.9734, 90.6569),
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
             strokeColor: Colors.black,
             strokeWidth: 2,
          ),
          sublayers: [
            MapArcLayer(
              arcs: List<MapArc>.generate(
                data.length,
                    (int index) {
                  return MapArc(
                    from: data[index].from,
                    to: data[index].to,
                  );
                },
              ).toSet(),
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
          zoomPanBehavior: zoomPanBehavior,
        ),
      ],
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
