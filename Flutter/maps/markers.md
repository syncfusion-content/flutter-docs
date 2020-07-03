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

You can show markers at any position on the map by providing latitude and longitude position to the `MapMarker`, which is the widget returns from the `MapShapeLayer.markerBuilder` property.

The `markerBuilder` callback will be called number of times equal to the value specified in the `initialMarkersCount` property. The default value of the `initialMarkersCount` property is `null`.

{% tabs %}
{% highlight Dart %}

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

{% endhighlight %}
{% endtabs %}

![default marker](images/markers/default_marker.png)

N>
* Refer the `markerBuilder`, for returning the `MapMarker`.
* Refer the `controller`, for dynamically updating the markers.

## Appearance customization

You can customize the built-in markers appearance using the `iconType`, `iconColor`, `iconStrokeColor`, `iconStrokeWidth`, and `size` properties of the `MapMarker`.

N>
* The default value of the `iconType` is `MapIconType.circle`.
* The default value of the `iconStrokeWidth` is `1.0`.
* The default value of the `iconColor` is `Colors.blue`.
* The default value of the `size` is `Size(14.0, 14.0)`.

{% tabs %}
{% highlight Dart %}

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

{% endhighlight %}
{% endtabs %}

<b>Using SfMapsTheme</b>

You can customize the below appearance of the markers.

* **Background color** - Change the background color of the markers using the `SfMapsThemeData.markerIconColor` property.
* **Stroke color** - Change the stroke color of the markers using the `SfMapsThemeData.markerIconStrokeColor` property.
* **Stroke width** - Change the stroke width of the markers using the `SfMapsThemeData.markerIconStrokeWidth` property.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

{% tabs %}
{% highlight Dart %}

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
      body: Center(
          child: Container(
            height: 350,
            child: Padding(
              padding: EdgeInsets.only(left: 15, right: 15),
              child: SfMapsTheme(
                data: SfMapsThemeData(
                  markerIconColor: Colors.green[200],
                  markerIconStrokeColor: Colors.green[900],
                  markerIconStrokeWidth: 2,
                ),
                child: SfMaps(
                  layers: <MapLayer>[
                    MapShapeLayer(
                      delegate: MapShapeLayerDelegate(
                        shapeFile: 'assets/world_map.json',
                        shapeDataField: 'name',
                      ),
                      initialMarkersCount: 5,
                      markerBuilder: (_, int index) {
                        return MapMarker(
                          latitude: data[index].latitude,
                          longitude: data[index].longitude,
                          iconType: MapIconType.triangle,
                          size: Size(18, 18),
                        );
                      },
                    ),
                  ],
                ),
              )
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

You can show custom marker using the `child` property of the `MapMarker` which returns from the `markerBuilder`.

{% tabs %}
{% highlight Dart %}

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

{% endhighlight %}
{% endtabs %}

![custom marker](images/markers/custom_marker.png)

## Adding markers dynamically

You can add markers dynamically using the `insertMarker` method in the `MapShapeLayerController`. The `markerBuilder` will be called for the respective index once `insertMarker` method is called. The `controller` property of `MapShapeLayer` has to be set with the new instance of `MapShapeLayerController`.

Marker will be inserted at the given index if the index value is less than or equal to the current available index and the marker will be added as a last item if the index value is greater than the current available index.

N> You can get the current markers count from `MapShapeLayerController.markersCount`.

{% tabs %}
{% highlight Dart %}

List<Model> data;
MapShapeLayerController controller;
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
                        ),
                        initialMarkersCount: 5,
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
                      controller.insertMarker(5);
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

You can update multiple markers at a same time by passing indices to the `updateMarkers` method in the `MapShapeLayerController`. The `markerBuilder` will be called again for the respective indices once `updateMarkers` method is called.

N> You can get the current markers count from `MapShapeLayerController.markersCount`.

{% tabs %}
{% highlight Dart %}

List<Model> data;
MapShapeLayerController controller;
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
                        ),
                        initialMarkersCount: 5,
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

{% endhighlight %}
{% endtabs %}

![Update markers dynamically](images/markers/update-markers.gif)

## Deleting a marker

You can remove marker at any index using the `removeMarkerAt` method.

N> You can get the current markers count from `MapShapeLayerController.markersCount`.

{% tabs %}
{% highlight Dart %}

List<Model> data;
MapShapeLayerController controller;

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
                        ),
                        initialMarkersCount: 5,
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
                      controller.removeMarkerAt(4);
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

You can clear all markers using the `clearMarkers` method.

N> You can get the current markers count from `MapShapeLayerController.markersCount`.

{% tabs %}
{% highlight Dart %}

List<Model> data;
MapShapeLayerController controller;

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
                        ),
                        initialMarkersCount: 5,
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
