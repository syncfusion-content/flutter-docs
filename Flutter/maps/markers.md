---
layout: post
title: Markers in Syncfusion Flutter Maps | Syncfusion
description: This section explains about how to add the markers and customize them dynamically in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Markers in the Flutter Maps

Markers can be used to denote the locations. It is possible to use the built-in symbols or display a custom widget at a specific latitude and longitude on a map.

## Adding markers

### Shape layer

You can show markers at any position on the map by providing latitude and longitude position to the [`MapMarker`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker-class.html), which is the widget returns from the [`markerBuilder`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/markerBuilder.html) property.

The [`markerBuilder`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/markerBuilder.html) callback will be called number of times equal to the value specified in the [`initialMarkersCount`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/initialMarkersCount.html) property. The default value of the [`initialMarkersCount`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/initialMarkersCount.html) property is `null`.

{% tabs %}
{% highlight Dart %}

List<Model> _data;
MapShapeSource _dataSource;

@override
void initState() {
    _data = const <Model>[
      Model('Brazil', -14.235004, -51.92528),
      Model('Germany', 51.16569, 10.451526),
      Model('Australia', -25.274398, 133.775136),
      Model('India', 20.593684, 78.96288),
      Model('Russia', 61.52401, 105.318756)
    ];

    _dataSource = MapShapeSource.asset(
       'assets/world_map.json',
        shapeDataField: 'name',
        dataCount: _data.length,
        primaryValueMapper: (index) => _data[index].country,
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
            layers: <MapLayer>[
              MapShapeLayer(
                source: _dataSource,
                initialMarkersCount: 5,
                markerBuilder: (BuildContext context, int index) {
                  return MapMarker(
                    latitude: _data[index].latitude,
                    longitude: _data[index].longitude,
                  );
                },
              ),
            ],
          ),
        ),
      )),
   );
}

class Model {
  const Model(this.country, this.latitude, this.longitude);

  final String country;
  final double latitude;
  final double longitude;
}

{% endhighlight %}
{% endtabs %}

![default marker](images/markers/default_marker.png)

N>
* Refer the [`markerBuilder`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/markerBuilder.html), for returning the [`MapMarker`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker-class.html).
* Refer the [`controller`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/controller.html), for dynamically updating the markers.

### Tile layer

You can show markers at any position on the map by providing latitude and longitude position to the [`MapMarker`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker-class.html), which is the widget returns from the [`MapTileLayer.markerBuilder`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/markerBuilder.html) property.

The [`markerBuilder`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/markerBuilder.html) callback will be called number of times equal to the value specified in the [`initialMarkersCount`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/initialMarkersCount.html) property. The default value of the [`initialMarkersCount`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/initialMarkersCount.html) property is `null`.

{% tabs %}
{% highlight Dart %}

List<Model> _data;

@override
void initState() {
    _data = const <Model>[
      Model('Brazil', -14.235004, -51.92528),
      Model('Germany', 51.16569, 10.451526),
      Model('Australia', -25.274398, 133.775136),
      Model('India', 20.593684, 78.96288),
      Model('Russia', 61.52401, 105.318756)
    ];

    super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: Container(
        height: 350,
        child: SfMaps(
          layers: <MapLayer>[
            MapTileLayer(
              urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
              initialMarkersCount: 5,
              markerBuilder: (BuildContext context, int index) {
                return MapMarker(
                  latitude: _data[index].latitude,
                  longitude: _data[index].longitude,
                  iconColor: Colors.blue,
                );
              },
            ),
          ],
        ),
      ),
    ),
  );
}

class Model {
  const Model(this.country, this.latitude, this.longitude);

  final String country;
  final double latitude;
  final double longitude;
}

{% endhighlight %}
{% endtabs %}

![Tile layer marker](images/markers/tile_layer_marker.png)

N>
* Refer the [`markerBuilder`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/markerBuilder.html), for returning the [`MapMarker`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker-class.html).
* Refer the [`controller`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapTileLayer/controller.html) for dynamically updating the markers.

## Appearance customization

You can customize the built-in markers appearance using the [`iconType`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker/iconType.html), [`iconColor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker/iconColor.html), [`iconStrokeColor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker/iconStrokeColor.html), [`iconStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker/iconStrokeWidth.html), and [`size`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker/size.html) properties of the [`MapMarker`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker-class.html).

N>
* The default value of the [`iconType`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker/iconType.html) is `MapIconType.circle`.
* The default value of the [`iconStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker/iconStrokeWidth.html) is `1.0`.
* The default value of the [`iconColor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker/iconColor.html) is `Colors.blue`.
* The default value of the [`size`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker/size.html) is `Size(14.0, 14.0)`.

{% tabs %}
{% highlight Dart %}

List<Model> _data;
MapShapeSource _dataSource;

@override
void initState() {
    _data = <Model>[
      Model(-14.235004, -51.92528),
      Model(51.16569, 10.451526),
      Model(-25.274398, 133.775136),
      Model(20.593684, 78.96288),
      Model(61.52401, 105.318756)
    ];

    _dataSource = MapShapeSource.asset(
       'assets/world_map.json',
       shapeDataField: 'name',
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
                layers: <MapLayer>[
                  MapShapeLayer(
                    source: _dataSource,
                    initialMarkersCount: 5,
                    markerBuilder: (BuildContext context, int index){
                      return MapMarker(
                        latitude: _data[index].latitude,
                        longitude: _data[index].longitude,
                        iconType: MapIconType.triangle,
                        size: Size(18, 18),
                        iconColor: Colors.green[200],
                        iconStrokeColor: Colors.green[900],
                        iconStrokeWidth: 2,
                      );
                    },
                  ),
                ],
              ),
            ),
          )
      ),
   );
}

class Model {
  Model(this.latitude, this.longitude);

  final double latitude;
  final double longitude;
}

{% endhighlight %}
{% endtabs %}

![marker customization](images/markers/marker_customization.png)

## Adding custom markers

You can show custom marker using the `child` property of the [`MapMarker`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapMarker-class.html) which returns from the [`markerBuilder`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/markerBuilder.html).

{% tabs %}
{% highlight Dart %}

List<Model> _data;
List<Widget> _iconsList;
MapShapeSource _dataSource;

@override
void initState() {
     _data = <Model>[
       Model(-14.235004, -51.92528),
       Model(51.16569, 10.451526),
       Model(-25.274398, 133.775136),
       Model(20.593684, 78.96288),
       Model(61.52401, 105.318756)
     ];

     _iconsList = <Widget>[
       Icon(Icons.add_location),
       Icon(Icons.airplanemode_active),
       Icon(Icons.add_alarm),
       Icon(Icons.accessibility_new),
       Icon(Icons.account_balance)
     ];

     _dataSource = MapShapeSource.asset(
        'assets/world_map.json',
        shapeDataField: 'name',
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
                 layers: <MapLayer>[
                   MapShapeLayer(
                     source: _dataSource,
                     initialMarkersCount: 5,
                     markerBuilder: (BuildContext context, int index){
                       return MapMarker(
                         latitude: _data[index].latitude,
                         longitude: _data[index].longitude,
                         child: _iconsList[index],
                       );
                     },
                   ),
                 ],
               ),
             ),
           )
       ),
     );
  }
}

class Model {
   Model(this.latitude, this.longitude);

   final double latitude;
   final double longitude;
}

{% endhighlight %}
{% endtabs %}

![custom marker](images/markers/custom_marker.png)

## Adding markers dynamically

You can add markers dynamically using the [`insertMarker`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayerController/insertMarker.html) method. The [`markerBuilder`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/markerBuilder.html) will be called for the respective index once [`insertMarker`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayerController/insertMarker.html) method is called. The [`controller`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/controller.html) property of [`MapShapeLayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer-class.html) has to be set with the new instance of [`MapShapeLayerController`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerController-class.html).

Marker will be inserted at the given index if the index value is less than or equal to the current available index and the marker will be added as a last item if the index value is greater than the current available index.

N> You can get the current markers count from [`MapShapeLayerController.markersCount`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerController/markersCount.html).

### For shape layer

{% tabs %}
{% highlight Dart %}

List<Model> _data;
MapShapeLayerController _controller;
MapShapeSource _dataSource;
Random random = Random();

@override
void initState() {
    _data = <Model>[
      Model(-14.235004, -51.92528),
      Model(51.16569, 10.451526),
      Model(-25.274398, 133.775136),
      Model(20.593684, 78.96288),
      Model(61.52401, 105.318756)
    ];

    _dataSource = MapShapeSource.asset(
       'assets/world_map.json',
       shapeDataField: 'name',
    );
    _controller = MapShapeLayerController();
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
              child: Column(
                children: [
                  SfMaps(
                    layers: <MapLayer>[
                      MapShapeLayer(
                        source: _dataSource,
                        initialMarkersCount: 5,
                        markerBuilder: (BuildContext context, int index){
                          return MapMarker(
                            latitude: _data[index].latitude,
                            longitude: _data[index].longitude,
                            child: Icon(Icons.add_location),
                          );
                        },
                        controller: _controller,
                      ),
                    ],
                  ),
                  RaisedButton(
                    child: Text('Add marker'),
                    onPressed: () {
                      _data.add(Model(
                          -180 + random.nextInt(360).toDouble(),
                          -55 + random.nextInt(139).toDouble()));
                      _controller.insertMarker(5);
                    },
                  ),
                ],
              ),
            ),
          )
      ),
   );
}

class Model {
  Model(this.latitude, this.longitude);

  final double latitude;
  final double longitude;
}

{% endhighlight %}
{% endtabs %}

### For Tile layer

{% tabs %}
{% highlight Dart %}

List<Model> _data;
MapTileLayerController _controller;
Random random = Random();

@override
void initState() {
    _data = <Model>[
      Model(-14.235004, -51.92528),
      Model(51.16569, 10.451526),
      Model(-25.274398, 133.775136),
      Model(20.593684, 78.96288),
      Model(61.52401, 105.318756)
    ];
    _controller = MapTileLayerController();
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
              child: Column(
                children: [
                  SfMaps(
                    layers: <MapLayer>[
                      MapTileLayer(
                        urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
                        initialMarkersCount: 5,
                        markerBuilder: (BuildContext context, int index){
                          return MapMarker(
                            latitude: _data[index].latitude,
                            longitude: _data[index].longitude,
                            child: Icon(Icons.add_location),
                          );
                        },
                        controller: _controller,
                      ),
                    ],
                  ),
                  RaisedButton(
                    child: Text('Add marker'),
                    onPressed: () {
                      _data.add(Model(
                          -180 + random.nextInt(360).toDouble(),
                          -55 + random.nextInt(139).toDouble()));
                      _controller.insertMarker(5);
                    },
                  ),
                ],
              ),
            ),
          )
      ),
   );
}

class Model {
  Model(this.latitude, this.longitude);

  final double latitude;
  final double longitude;
}

{% endhighlight %}
{% endtabs %}

![Add markers dynamically](images/markers/add-markers.gif)

## Updating the existing markers

You can update multiple markers at a same time by passing indices to the [`updateMarkers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayerController/updateMarkers.html) method in the [`MapShapeLayerController`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerController-class.html). The [`markerBuilder`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/markerBuilder.html) will be called again for the respective indices once [`updateMarkers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayerController/updateMarkers.html) method is called.

N>
* You can get the current markers count from [`MapShapeLayerController.markersCount`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerController/markersCount.html).
* You can refer this [`snippet`](https://help.syncfusion.com/flutter/maps/markers#for-tile-layer) to update the markers dynamically for tile layer.

{% tabs %}
{% highlight Dart %}

List<Model> _data;
MapShapeLayerController _controller;
Widget _markerWidget;
MapShapeSource _dataSource;

@override
void initState() {
    _data = <Model>[
      Model(-14.235004, -51.92528),
      Model(51.16569, 10.451526),
      Model(-25.274398, 133.775136),
      Model(20.593684, 78.96288),
      Model(61.52401, 105.318756)
    ];

    _dataSource = MapShapeSource.asset(
       'assets/world_map.json',
        shapeDataField: 'name',
    );

    _controller = MapShapeLayerController();
    _markerWidget =  Icon(Icons.add_location);
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
              child: Column(
                children: [
                  SfMaps(
                    layers: <MapLayer>[
                      MapShapeLayer(
                        source: _dataSource,
                        initialMarkersCount: 5,
                        markerBuilder: (BuildContext context, int index){
                          return MapMarker(
                            latitude: _data[index].latitude,
                            longitude: _data[index].longitude,
                            child: _markerWidget,
                          );
                        },
                        controller: _controller,
                      ),
                    ],
                  ),
                  RaisedButton(
                    child: Text('Update marker'),
                    onPressed: () {
                      List<int> updateList = <int>[1, 2];
                      _markerWidget = Icon(Icons.people);
                      _controller.updateMarkers(updateList);
                    },
                  ),
                ],
              ),
            ),
          )
      ),
   );
}

class Model {
  Model(this.latitude, this.longitude);

  final double latitude;
  final double longitude;
}

{% endhighlight %}
{% endtabs %}

![Update markers dynamically](images/markers/update-markers.gif)

## Deleting a marker

You can remove marker at any index using the [`removeMarkerAt`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayerController/removeMarkerAt.html) method.

N>
* You can get the current markers count from [`MapShapeLayerController.markersCount`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerController/markersCount.html).
* You can refer this [`snippet`](https://help.syncfusion.com/flutter/maps/markers#for-tile-layer) to update the markers dynamically for tile layer.

{% tabs %}
{% highlight Dart %}

List<Model> _data;
MapShapeLayerController _controller;
MapShapeSource _dataSource;

@override
void initState() {
    _data = <Model>[
      Model(-14.235004, -51.92528),
      Model(51.16569, 10.451526),
      Model(-25.274398, 133.775136),
      Model(20.593684, 78.96288),
      Model(61.52401, 105.318756)
    ];

    _dataSource = MapShapeSource.asset(
       'assets/world_map.json',
       shapeDataField: 'name',
    );
    _controller = MapShapeLayerController();
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
              child: Column(
                children: [
                  SfMaps(
                    layers: <MapLayer>[
                      MapShapeLayer(
                        source: _dataSource,
                        initialMarkersCount: 5,
                        markerBuilder: (BuildContext context, int index){
                          return MapMarker(
                            latitude: _data[index].latitude,
                            longitude: _data[index].longitude,
                            child: Icon(Icons.add_location),
                          );
                        },
                        controller: _controller,
                      ),
                    ],
                  ),
                  RaisedButton(
                    child: Text('Remove marker'),
                    onPressed: () {
                      _controller.removeMarkerAt(4);
                    },
                  ),
                ],
              ),
            ),
          )
      ),
   );
}

class Model {
  Model(this.latitude, this.longitude);

  final double latitude;
  final double longitude;
}

{% endhighlight %}
{% endtabs %}

![Remove marker dynamically](images/markers/remove-marker.gif)

## Clearing the markers

You can clear all markers using the [`clearMarkers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayerController/clearMarkers.html) method.

N>
* You can get the current markers count from [`MapShapeLayerController.markersCount`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerController/markersCount.html).
* You can refer this [`snippet`](https://help.syncfusion.com/flutter/maps/markers#for-tile-layer) to update the markers dynamically for tile layer.

{% tabs %}
{% highlight Dart %}

List<Model> _data;
MapShapeLayerController _controller;
MapShapeSource _dataSource;

@override
void initState() {
    _data = <Model>[
      Model(-14.235004, -51.92528),
      Model(51.16569, 10.451526),
      Model(-25.274398, 133.775136),
      Model(20.593684, 78.96288),
      Model(61.52401, 105.318756)
    ];

    _dataSource = MapShapeSource.asset(
       'assets/world_map.json',
        shapeDataField: 'name',
    );
    _controller = MapShapeLayerController();
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
              child: Column(
                children: [
                  SfMaps(
                    layers: <MapLayer>[
                      MapShapeLayer(
                        source: _dataSource,
                        initialMarkersCount: 5,
                        markerBuilder: (BuildContext context, int index){
                          return MapMarker(
                            latitude: _data[index].latitude,
                            longitude: _data[index].longitude,
                            child: Icon(Icons.add_location),
                          );
                        },
                        controller: _controller,
                      ),
                    ],
                  ),
                  RaisedButton(
                    child: Text('Clear marker'),
                    onPressed: () {
                      _controller.clearMarkers();
                    },
                  ),
                ],
              ),
            ),
          )
      ),
   );
}

class Model {
  Model(this.latitude, this.longitude);

  final double latitude;
  final double longitude;
}

{% endhighlight %}
{% endtabs %}
