---
layout: post
title: Markers in Syncfusion Flutter Maps | Syncfusion
description: This section explains about how to show the markers and customise its appearance in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Markers in the Flutter Maps

It denotes a location with built-in symbols or display a custom widget at a specific latitude and longitude on a map.

## Adding default markers

You can show markers at any position on the map by providing latitude and longitude position to the [MapMarker], which is the widget returns from the [markerBuilder] property in the [MapShapeLayer].

The [markerBuilder] function returns list of markers based on the value specified in the [initialMarkersCount] property. The default value of the [`initialMarkersCount`] property is `null`.

```dart
List<Model> data;

@override
void initState() {
    data = const <Model>[
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
            child: Padding(
              padding: EdgeInsets.only(left: 15, right: 15),
              child: SfMaps(
                layers: <MapLayer>[
                  MapShapeLayer(
                    delegate: MapShapeLayerDelegate(
                      shapeFile: 'assets/world_map.json',
                      shapeDataField: 'name',
                      dataCount: data.length,
                      primaryValueMapper: (index) => data[index].country,
                    ),
                    initialMarkersCount: 5,
                    markerBuilder: (_, int index){
                      return MapMarker(
                        latitude: data[index].latitude,
                        longitude: data[index].longitude,
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
  const Model(this.country, this.latitude, this.longitude);

  final String country;
  final double latitude;
  final double longitude;
}
```

![default marker](images/markers/default_marker.png)

## Adding custom markers

You can show custom marker using the [child] property of the [MapMarker] which returns from [markerBuilder] property in the [MapShapeLayer].

```dart
List<Model> data;
List<Widget> iconsList;

@override
void initState() {
     data = <Model>[
       Model(-14.235004, -51.92528),
       Model(51.16569, 10.451526),
       Model(-25.274398, 133.775136),
       Model(20.593684, 78.96288),
       Model(61.52401, 105.318756)
     ];

     iconsList = <Widget>[
       Icon(Icons.add_location),
       Icon(Icons.airplanemode_active),
       Icon(Icons.add_alarm),
       Icon(Icons.accessibility_new),
       Icon(Icons.account_balance)
     ];

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
                     delegate: MapShapeLayerDelegate(
                       shapeFile: 'assets/world_map.json',
                       shapeDataField: 'name',
                       dataCount: data.length,
                     ),
                     initialMarkersCount: 5,
                     markerBuilder: (_, int index){
                       return MapMarker(
                         latitude: data[index].latitude,
                         longitude: data[index].longitude,
                         child: iconsList[index],
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
```

![custom marker](images/markers/custom_marker.png)

## Markers customization

You can customize the built-in markers appearance using the [iconType], [iconColor], [iconStrokeColor], [iconStrokeWidth], and [size] properties.

```dart
List<Model> data;

@override
void initState() {
    data = <Model>[
      Model(-14.235004, -51.92528),
      Model(51.16569, 10.451526),
      Model(-25.274398, 133.775136),
      Model(20.593684, 78.96288),
      Model(61.52401, 105.318756)
    ];

    super.initState();
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
          child: Container(
            height: 350,
            child: Padding(
              padding: EdgeInsets.only(left: 15, right: 15),
              child: SfMaps(
                layers: <MapLayer>[
                  MapShapeLayer(
                    delegate: MapShapeLayerDelegate(
                      shapeFile: 'assets/world_map.json',
                      shapeDataField: 'name',
                      dataCount: data.length,
                    ),
                    initialMarkersCount: 5,
                    markerBuilder: (_, int index){
                      return MapMarker(
                        latitude: data[index].latitude,
                        longitude: data[index].longitude,
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
```

![marker customization](images/markers/marker_customization.png)

## Adding marker dynamically

You can add marker dynamically using the [insertMarker] function in the [controller] property of [MapShapeLayer]. The [controller] property is used to rebuild the [markerBuilder] function based on the value of [initialMarkersCount] property.

Marker will be inserted at the given index if the index value is less than the [initialMarkersCount] value and marker will be added last if the index value is greater than the [initialMarkersCount] value.

I> You must update the [initialMarkersCount] property for any [controller] functions such as [insertMarker], [updateMarkers], [removeMarkerAt], and [clearMarkers].

```dart
List<Model> data;
MapShapeLayerController controller;
int markerCount = 5;
Random random = Random();

@override
void initState() {
    data = <Model>[
      Model(-14.235004, -51.92528),
      Model(51.16569, 10.451526),
      Model(-25.274398, 133.775136),
      Model(20.593684, 78.96288),
      Model(61.52401, 105.318756)
    ];

    controller = MapShapeLayerController();
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
                        delegate: MapShapeLayerDelegate(
                          shapeFile: 'assets/world_map.json',
                          shapeDataField: 'name',
                          dataCount: data.length,
                        ),
                        initialMarkersCount: markerCount,
                        markerBuilder: (_, int index){
                          return MapMarker(
                            latitude: data[index].latitude,
                            longitude: data[index].longitude,
                            child: Icon(Icons.add_location),
                          );
                        },
                        controller: controller,
                      ),
                    ],
                  ),
                  RaisedButton(
                    child: Text('Add marker'),
                    onPressed: () {
                      data.add(Model(
                          -180 + random.nextInt(360).toDouble(),
                          -55 + random.nextInt(139).toDouble()));
                      controller.insertMarker(markerCount++);
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
```

## Updating the existing marker

You can update multiple markers at a same time by passing multiple indices to the [updateMarkers] function in the [controller] property.

I> You must update the [initialMarkersCount] property for any [controller] functions such as [insertMarker], [updateMarkers], [removeMarkerAt], and [clearMarkers].

```dart
List<Model> data;
MapShapeLayerController controller;
int markerCount = 5;
Random random = Random();
Widget markerWidget;

@override
void initState() {
    data = <Model>[
      Model(-14.235004, -51.92528),
      Model(51.16569, 10.451526),
      Model(-25.274398, 133.775136),
      Model(20.593684, 78.96288),
      Model(61.52401, 105.318756)
    ];

    controller = MapShapeLayerController();
    markerWidget =  Icon(Icons.add_location);
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
                        delegate: MapShapeLayerDelegate(
                          shapeFile: 'assets/world_map.json',
                          shapeDataField: 'name',
                          dataCount: data.length,
                        ),
                        initialMarkersCount: markerCount,
                        markerBuilder: (_, int index){
                          return MapMarker(
                            latitude: data[index].latitude,
                            longitude: data[index].longitude,
                            child: markerWidget,
                          );
                        },
                        controller: controller,
                      ),
                    ],
                  ),
                  RaisedButton(
                    child: Text('Update marker'),
                    onPressed: () {
                      List<int> updateList = <int>[1, 2];
                      markerWidget = Icon(Icons.airplanemode_active);
                      controller.updateMarkers(updateList);
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
```

## Deleting marker

You can remove marker at any index using the [removeMarkerAt] function in the [controller] property.

I> You must update the [initialMarkersCount] property for any [controller] functions such as [insertMarker], [updateMarkers], [removeMarkerAt], and [clearMarkers].

```dart
List<Model> data;
MapShapeLayerController controller;
int markerCount = 5;
Random random = Random();

@override
void initState() {
    data = <Model>[
      Model(-14.235004, -51.92528),
      Model(51.16569, 10.451526),
      Model(-25.274398, 133.775136),
      Model(20.593684, 78.96288),
      Model(61.52401, 105.318756)
    ];
    controller = MapShapeLayerController();
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
                        delegate: MapShapeLayerDelegate(
                          shapeFile: 'assets/world_map.json',
                          shapeDataField: 'name',
                          dataCount: data.length,
                        ),
                        initialMarkersCount: markerCount,
                        markerBuilder: (_, int index){
                          return MapMarker(
                            latitude: data[index].latitude,
                            longitude: data[index].longitude,
                            child: Icon(Icons.add_location),
                          );
                        },
                        controller: controller,
                      ),
                    ],
                  ),
                  RaisedButton(
                    child: Text('Remove marker'),
                    onPressed: () {
                      controller.removeMarkerAt(2);
                      markerCount--;
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
```

## Clearing the markers

You can clear all markers using the [clearMarkers] function in the [controller] property.

I> You must update the [initialMarkersCount] property for any [controller] functions such as [insertMarker], [updateMarkers], [removeMarkerAt], and [clearMarkers].

```dart
List<Model> data;
MapShapeLayerController controller;
int markerCount = 5;
Random random = Random();

@override
void initState() {
    data = <Model>[
      Model(-14.235004, -51.92528),
      Model(51.16569, 10.451526),
      Model(-25.274398, 133.775136),
      Model(20.593684, 78.96288),
      Model(61.52401, 105.318756)
    ];

    controller = MapShapeLayerController();
    super.initState();
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
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
                        delegate: MapShapeLayerDelegate(
                          shapeFile: 'assets/world_map.json',
                          shapeDataField: 'name',
                          dataCount: data.length,
                        ),
                        initialMarkersCount: markerCount,
                        markerBuilder: (_, int index){
                          return MapMarker(
                            latitude: data[index].latitude,
                            longitude: data[index].longitude,
                            child: Icon(Icons.add_location),
                          );
                        },
                        controller: controller,
                      ),
                    ],
                  ),
                  RaisedButton(
                    child: Text('Clear marker'),
                    onPressed: () {
                      controller.clearMarkers();
                      markerCount = 0;
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
```
