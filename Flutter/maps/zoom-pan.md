---
layout: post
title: Zooming and Panning  in Flutter Maps widget | Syncfusion
description: Learn here all about the Zooming and Panning feature of Syncfusion Flutter Maps (SfMaps) widget and more.
platform: Flutter
control: SfMaps
documentation: ug
---

# Zooming and Panning in Flutter Maps (SfMaps)

It is possible to zoom in and out for any layer to take a closer look at a specific region by pinching the map, scrolling the mouse wheel or track pad, or using the toolbar on the web. Pan the map to navigate across the regions. You can also customize the zoom level and the center point of the initial rendering.

The procedure for zooming and panning for both layers is very similar.

**Shape layer**

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;
late MapShapeSource _dataSource;

@override
void initState() {
  super.initState();
  _dataSource = MapShapeSource.asset(
    'assets/world_map.json',
    shapeDataField: 'continent',
  );
  _zoomPanBehavior = MapZoomPanBehavior();
}

@override
Widget build(BuildContext context) {
    return Scaffold(
        body: SfMaps(
            layers: [
                MapShapeLayer(
                    source: _dataSource,
                    zoomPanBehavior: _zoomPanBehavior,
                ),
            ],
        ),
    );
}

{% endhighlight %}
{% endtabs %}

**Tile layer**

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = MapZoomPanBehavior();
}

@override
Widget build(BuildContext context) {
    return FutureBuilder(
        future: getBingUrlTemplate(
            'https://dev.virtualearth.net/REST/V1/Imagery/Metadata/AerialWithLabels?output=json&uriScheme=https&include=ImageryProviders&key=YOUR_KEY'),
        builder: (context, snapshot) {
            if (snapshot.hasData) {
                return SfMaps(
                    layers: [
                        MapTileLayer(
                            urlTemplate: snapshot.data as String,
                            zoomPanBehavior: _zoomPanBehavior,
                        ),
                    ],
                );
           }
        return CircularProgressIndicator();
        }
    );
}

{% endhighlight %}
{% endtabs %}

![Bing maps aerial default](images/zoom-pan/bing_maps_aerial.png)

## Customizing the center latitude and longitude

The [`MapZoomPanBehavior.focalLatLng`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/focalLatLng.html) is the focal point of the map layer based on which zooming happens. It represents the focal latitude and longitude position of the map layer. You can also get the current focalLatLng after interaction using the [MapZoomPanBehavior.focalLatLng](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/focalLatLng.html) property.

To enable panning, set the instance of [`MapZoomPanBehavior`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior-class.html) to [`MapTileLayer.zoomPanBehavior`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/zoomPanBehavior.html). By default, it will be `true`. 

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = MapZoomPanBehavior(
        focalLatLng: MapLatLng(27.1751, 50.0421),
    );
}

@override
Widget build(BuildContext context) {
    return FutureBuilder(
        future: getBingUrlTemplate(
            'https://dev.virtualearth.net/REST/V1/Imagery/Metadata/AerialWithLabels?output=json&uriScheme=https&include=ImageryProviders&key=YOUR_KEY'),
        builder: (context, snapshot) {
            if (snapshot.hasData) {
                return SfMaps(
                    layers: [
                        MapTileLayer(
                            urlTemplate: snapshot.data as String,
                            zoomPanBehavior: _zoomPanBehavior,
                        ),
                    ],
                );
           }
        return CircularProgressIndicator();
        }
    );
}

{% endhighlight %}
{% endtabs %}

![Bing maps aerial focalLatLng](images/zoom-pan/bing_maps_focallatlng.png)

## Update the center latitude and longitude programmatically

You can change the center latitude and longitude of the shape layer programmatically using the [`MapZoomPanBehavior.focalLatLng`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/focalLatLng.html) property.

N> It is applicable for both shape layer and tile layer.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;
late MapShapeSource _dataSource;

@override
void initState() {
  super.initState();
  _dataSource = MapShapeSource.asset(
     'assets/world_map.json',
      shapeDataField: 'continent',
  );

  _zoomPanBehavior = MapZoomPanBehavior(
    focalLatLng: MapLatLng(27.1751, 78.0421),
    zoomLevel: 4,
  );
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: Column(
        children: [
          Container(
            height: 600,
            child: SfMaps(
              layers: [
                MapShapeLayer(
                  source: _dataSource,
                  zoomPanBehavior: _zoomPanBehavior,
                ),
              ],
            ),
          ),
          SizedBox(height: 20),
          RaisedButton(
            child: Text('Change focalLatLng'),
            onPressed: () {
               _zoomPanBehavior.focalLatLng = MapLatLng(56.1304, -106.3468);
            },
          ),
        ],
     ),
  );
}

{% endhighlight %}
{% endtabs %}

## Customizing the zoom level

You can set the current zoom level of the map layer by using [`MapZoomPanBehavior.zoomLevel`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/zoomLevel.html) property.

The default [MapZoomPanBehavior.zoomLevel](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/zoomLevel.html) value is 1 which will show the whole map in the viewport for [MapShapeLayer](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer-class.html) and the possible bounds for the [MapShapeLayer](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer-class.html) based on the [MapZoomPanBehavior.focalLatLng](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/focalLatLng.html). You can also get the current zoom level after interaction using the [MapZoomPanBehavior.zoomLevel](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/zoomLevel.html) property.

To enable zooming, set the instance of [`MapZoomPanBehavior`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior-class.html) to [`MapTileLayer.zoomPanBehavior`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/zoomPanBehavior.html). By default, it will be `true`. 

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = MapZoomPanBehavior(
        focalLatLng: MapLatLng(27.1751, 78.0421),
        zoomLevel: 5,
    );
}

@override
Widget build(BuildContext context) {
    return FutureBuilder(
        future: getBingUrlTemplate(
            'https://dev.virtualearth.net/REST/V1/Imagery/Metadata/AerialWithLabels?output=json&uriScheme=https&include=ImageryProviders&key=YOUR_KEY'),
        builder: (context, snapshot) {
            if (snapshot.hasData) {
                return SfMaps(
                    layers: [
                        MapTileLayer(
                            urlTemplate: snapshot.data as String,
                            zoomPanBehavior: _zoomPanBehavior,
                        ),
                    ],
                );
           }
        return CircularProgressIndicator();
        }
    );
}

{% endhighlight %}
{% endtabs %}

![Bing maps aerial zoomlevel](images/zoom-pan/bing_maps_zoomlevel.png)

## Update the zoom level programmatically

You can change the zoom level of the shape layer programmatically using the [`MapZoomPanBehavior.zoomLevel`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/zoomLevel.html) property.

N> It is applicable for both shape layer and tile layer.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;
late MapShapeSource _dataSource;

@override
void initState() {
  _dataSource = MapShapeSource.asset(
     'assets/world_map.json',
     shapeDataField: 'continent',
  );
  _zoomPanBehavior = MapZoomPanBehavior(
     focalLatLng: MapLatLng(27.1751, 78.0421),
     zoomLevel: 2,
  );
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Column(
      children: [
        Container(
          height: 600,
          child: SfMaps(
            layers: [
              MapShapeLayer(
                source: _dataSource,
                zoomPanBehavior: _zoomPanBehavior,
              ),
            ],
          ),
        ),
        SizedBox(height: 20),
        RaisedButton(
          child: Text('Change zoomLevel'),
          onPressed: () {
            _zoomPanBehavior.zoomLevel = 7;
          },
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Customizing min and max zoom level

You can set the min and max zoom level of the map layer by setting the value to [`MapZoomPanBehavior.minZoomLevel`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/minZoomLevel.html) and [`MapZoomPanBehavior.maxZoomLevel`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/maxZoomLevel.html) properties. The minimum and maximum zooming levels can be restricted using these properties respectively. The default values of [`MapZoomPanBehavior.minZoomLevel`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/minZoomLevel.html) and [`MapZoomPanBehavior.maxZoomLevel`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/maxZoomLevel.html) are 1 and 15 respectively.

However, for [MapTileLayer](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapTileLayer-class.html), [MapZoomPanBehavior.maxZoomLevel](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/maxZoomLevel.html) may slightly vary depends on the providers. Kindly check the respective official website of the map tile providers to know about the maximum zoom level it supports.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = MapZoomPanBehavior(
        focalLatLng: MapLatLng(27.1751, 78.0421),
        zoomLevel: 5,
        minZoomLevel: 3,
        maxZoomLevel: 10,
    );
}

@override
Widget build(BuildContext context) {
    return FutureBuilder(
        future: getBingUrlTemplate(
            'https://dev.virtualearth.net/REST/V1/Imagery/Metadata/AerialWithLabels?output=json&uriScheme=https&include=ImageryProviders&key=YOUR_KEY'),
        builder: (context, snapshot) {
            if (snapshot.hasData) {
                return SfMaps(
                    layers: [
                        MapTileLayer(
                            urlTemplate: snapshot.data as String,
                            zoomPanBehavior: _zoomPanBehavior,
                        ),
                    ],
                );
           }
        return CircularProgressIndicator();
        }
    );
}

{% endhighlight %}
{% endtabs %}

## Double tap zooming

Double tap zooming can be enabled using [`enableDoubleTapZooming`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/enableDoubleTapZooming.html) property. The default value of the [`enableDoubleTapZooming`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/enableDoubleTapZooming.html) is `false`.

N> It is applicable for both tile layer and shape layer.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
  _zoomPanBehavior = MapZoomPanBehavior(enableDoubleTapZooming: true);
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfMaps(
       layers: [
         MapTileLayer(
           urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
           zoomPanBehavior: _zoomPanBehavior,
         ),
       ],
     ),
  );
}

{% endhighlight %}
{% endtabs %}

![Double tap zooming](images/zoom-pan/double_tap_zoom.gif)

## Toolbar

The toolbar can be used to perform zoom in, zoom out, and reset operations in the web and desktop platforms. By default, the [MapZoomPanBehavior.showToolbar](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/showToolbar.html) property is `true`.

## Toolbar customization

You can customize the toolbar items using the following properties:

* Position - Used to position the toolbar item at the four corners of the map visual bounds using the [`position`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapToolbarSettings/position.html) property. The default value of the [`position`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapToolbarSettings/position.html) property is `MapToolbarPosition.topRight`. The possible values are `topRight`, `topLeft`, `bottomLeft`, and `bottomRight`.
* Icon color - used to set color to the three icons using the [`iconColor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapToolbarSettings/iconColor.html) property.
* Item background color - Used to set background color of the toolbar icons using the [`itemBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapToolbarSettings/itemBackgroundColor.html) property.
* Item hover color - Used to set color while hover over the icon using the [`itemHoverColor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapToolbarSettings/itemHoverColor.html) property.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
  _zoomPanBehavior = MapZoomPanBehavior(
    focalLatLng: MapLatLng(27.1751, 78.0421),
    zoomLevel: 3,
    showToolbar: true,
    toolbarSettings: MapToolbarSettings(
      position: MapToolbarPosition.topLeft,
      iconColor: Colors.red,
      itemBackgroundColor: Colors.green,
      itemHoverColor: Colors.blue,
    ),
  );
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Container(
      height: 350,
      width: 350,
      child: SfMaps(
        layers: [
          MapTileLayer(
            urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
            zoomPanBehavior: _zoomPanBehavior,
          ),
        ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Toolbar customization](images/zoom-pan/toolbar_customization.gif)

## Zooming callback

Whenever zooming happens, this callback is called. If it returns false, zooming will not happen.

[MapZoomDetails](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails-class.html) contains following properties.
    * [MapZoomDetails.previousVisibleBounds](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/previousVisibleBounds.html) - provides the visible bounds before the current zooming operation completes i.e. current visible bounds.
    * [MapZoomDetails.newVisibleBounds](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/newVisibleBounds.html) - provides the new visible bounds when the current zoom completes. Hence, if it returns false, there will be no changes in the UI.
    * [MapZoomDetails.previousZoomLevel](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/previousZoomLevel.html) - provides the zoom level before the current zooming operation completes i.e. current zoom level.
    * [MapZoomDetails.newZoomLevel](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/newZoomLevel.html) - provides the new zoom level when the current zoom completes. Hence, if it returns false, there will be no changes in the UI.
    * [MapZoomDetails.globalFocalPoint](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/globalFocalPoint.html) - The global focal point of the pointers in contact with the screen.
    * [MapZoomDetails.localFocalPoint](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/localFocalPoint.html) - The local focal point of the pointers in contact with the screen.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = MapZoomPanBehavior()
}

@override
Widget build(BuildContext context) {
    return FutureBuilder(
        future: getBingUrlTemplate(
            'https://dev.virtualearth.net/REST/V1/Imagery/Metadata/AerialWithLabels?output=json&uriScheme=https&include=ImageryProviders&key=YOUR_KEY'),
        builder: (context, snapshot) {
            if (snapshot.hasData) {
                return SfMaps(
                    layers: [
                        MapTileLayer(
                            urlTemplate: snapshot.data as String,
                            zoomPanBehavior: _zoomPanBehavior,
                            onWillZoom: (MapZoomDetails detail) {
                                return true;
                            },
                        ),
                    ],
                );
           }
        return CircularProgressIndicator();
        }
    );
}

{% endhighlight %}
{% endtabs %}

## Panning callback

Whenever panning happens, this callback is called. If it returns false, panning will not happen.
 
[MapPanDetails](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails-class.html) contains following properties.
    * [MapPanDetails.previousVisibleBounds](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/previousVisibleBounds.html) - provides the visible bounds before the current panning operation completes i.e. current visible bounds.
    * [MapPanDetails.newVisibleBounds](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/newVisibleBounds.html) - provides the new visible bounds when the current pan completes. Hence, if it returns false, there will be no changes in the UI.
    * [MapPanDetails.zoomLevel](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/zoomLevel.html) - provides the current zoom level.
    * [MapPanDetails.delta](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/delta.html) - The difference in pixels between touch start and current touch position.
    * [MapPanDetails.globalFocalPoint](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/globalFocalPoint.html) - The global focal point of the pointers in contact with the screen.
    * [MapPanDetails.localFocalPoint](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/localFocalPoint.html) - The local focal point of the pointers in contact with the screen.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = MapZoomPanBehavior();
}

@override
Widget build(BuildContext context) {
    return FutureBuilder(
        future: getBingUrlTemplate(
            'https://dev.virtualearth.net/REST/V1/Imagery/Metadata/AerialWithLabels?output=json&uriScheme=https&include=ImageryProviders&key=YOUR_KEY'),
        builder: (context, snapshot) {
            if (snapshot.hasData) {
                return SfMaps(
                    layers: [
                        MapTileLayer(
                            urlTemplate: snapshot.data as String,
                            zoomPanBehavior: _zoomPanBehavior,
                            onWillPan: (MapPanDetails detail) {
                                return true;
                            },
                        ),
                    ],
                );
           }
        return CircularProgressIndicator();
        }
    );
}

{% endhighlight %}
{% endtabs %}

## Overriding the zoom pan behavior

### Zooming

Whenever zooming happens, this method is called. Subclasses can override this method to do any custom operations based on the details provided in the [MapZoomDetails](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails-class.html).

[MapZoomDetails](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails-class.html) contains following properties,
    * [MapZoomDetails.previousVisibleBounds](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/previousVisibleBounds.html) - provides the visible bounds before the current zooming operation completes i.e. current visible bounds.
    * [MapZoomDetails.newVisibleBounds](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/newVisibleBounds.html) - provides the new visible bounds when the current zoom completes. Hence, if the
    `super.onZooming(details)` is not called, there will be no changes in the UI.
    * [MapZoomDetails.previousZoomLevel](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/previousZoomLevel.html) - provides the zoom level before the current zooming operation completes i.e. current zoom level.
    * [MapZoomDetails.newZoomLevel](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/newZoomLevel.html) - provides the new zoom level when the current zoom completes. Hence, if the
    `super.onZooming(details)` is not called, there will be no changes in the UI.
    * [MapZoomDetails.globalFocalPoint](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/globalFocalPoint.html) - The global focal point of the pointers in contact with the screen.
    * [MapZoomDetails.localFocalPoint](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomDetails/localFocalPoint.html) - The local focal point of the pointers in contact with the screen.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = _CustomZoomPanBehavior();
}

@override
Widget build(BuildContext context) {
    return FutureBuilder(
        future: getBingUrlTemplate(
            'https://dev.virtualearth.net/REST/V1/Imagery/Metadata/AerialWithLabels?output=json&uriScheme=https&include=ImageryProviders&key=YOUR_KEY'),
        builder: (context, snapshot) {
            if (snapshot.hasData) {
                return SfMaps(
                    layers: [
                        MapTileLayer(
                            urlTemplate: snapshot.data as String,
                            zoomPanBehavior: _zoomPanBehavior,
                        ),
                    ],
                );
           }
        return CircularProgressIndicator();
        }
    );
}

class _CustomZoomPanBehavior extends MapZoomPanBehavior {

  @override
  void onZooming(MapZoomDetails details) {
    super.onZooming(details);
    // Add the code here.
  }
}

{% endhighlight %}
{% endtabs %}

N>
* When `super.onZooming(details)` is not called, zooming will not happen.

### Panning

Whenever panning happens, this method is called. Subclasses can override this method to do any custom operations based on the details provided in the [MapPanDetails](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails-class.html). 
  
[MapPanDetails](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails-class.html) contains following properties,
    * [MapPanDetails.previousVisibleBounds](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/previousVisibleBounds.html) - provides the visible bounds before the current panning operation completes i.e. current visible bounds.
    * [MapPanDetails.newVisibleBounds](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/newVisibleBounds.html) - provides the new visible bounds when the current pan completes. Hence, if the
    `super.onPanning(details)` is not called, there will be no changes in the UI.
    * [MapPanDetails.zoomLevel](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/zoomLevel.html) - provides the current zoom level.
    * [MapPanDetails.delta](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/delta.html) - The difference in pixels between touch start and current touch position.
    * [MapPanDetails.globalFocalPoint](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/globalFocalPoint.html) - The global focal point of the pointers in contact with the screen.
    * [MapPanDetails.localFocalPoint](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapPanDetails/localFocalPoint.html) - The local focal point of the pointers in contact with the screen.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = _CustomZoomPanBehavior();
}

@override
Widget build(BuildContext context) {
    return FutureBuilder(
        future: getBingUrlTemplate(
            'https://dev.virtualearth.net/REST/V1/Imagery/Metadata/AerialWithLabels?output=json&uriScheme=https&include=ImageryProviders&key=YOUR_KEY'),
        builder: (context, snapshot) {
            if (snapshot.hasData) {
                return SfMaps(
                    layers: [
                        MapTileLayer(
                            urlTemplate: snapshot.data as String,
                            zoomPanBehavior: _zoomPanBehavior,
                        ),
                    ],
                );
           }
        return CircularProgressIndicator();
        }
    );
}

class _CustomZoomPanBehavior extends MapZoomPanBehavior {

  @override
  void onPanning(MapPanDetails details) {
    super.onPanning(details);
    // Add the code here
  }
}

{% endhighlight %}
{% endtabs %}

N>
* When `super.onPanning(details)` is not called, panning will not happen.

### Reset

You can [`reset`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/reset.html) the map to the [MapZoomPanBehavior.minZoomLevel](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapZoomPanBehavior/minZoomLevel.html) by calling this method.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = MapZoomPanBehavior();
}

@override
Widget build(BuildContext context) {
    return Column(
        children: [
            FutureBuilder(
                future: getBingUrlTemplate(
                    'https://dev.virtualearth.net/REST/V1/Imagery/Metadata/AerialWithLabels?output=json&uriScheme=https&include=ImageryProviders&key=YOUR_KEY'),
                builder: (context, snapshot) {
                    if (snapshot.hasData) {
                        return SfMaps(
                            layers: [
                                MapTileLayer(
                                    urlTemplate: snapshot.data as String,
                                    zoomPanBehavior: _zoomPanBehavior,
                                ),
                            ],
                        );
                    }
                    return CircularProgressIndicator();
                },
            ),
            FlatButton(
                onPressed: () {
                    _zoomPanBehavior.reset();
                },
                child: Text('Reset Zoom Level'),
            ),
        ],
    );
}

{% endhighlight %}
{% endtabs %}

### HandleEvent

You can override this method to handle pointer events that hit this render object.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = _CustomZoomPanBehavior();
}

@override
Widget build(BuildContext context) {
    return FutureBuilder(
        future: getBingUrlTemplate(
            'https://dev.virtualearth.net/REST/V1/Imagery/Metadata/AerialWithLabels?output=json&uriScheme=https&include=ImageryProviders&key=YOUR_KEY'),
        builder: (context, snapshot) {
            if (snapshot.hasData) {
                return SfMaps(
                    layers: [
                        MapTileLayer(
                            urlTemplate: snapshot.data as String,
                            zoomPanBehavior: _zoomPanBehavior,
                        ),
                    ],
                );
           }
        return CircularProgressIndicator();
        }
    );
}

class _CustomZoomPanBehavior extends MapZoomPanBehavior {

  @override
  void handleEvent(PointerEvent event, HitTestEntry entry) {
    super.handleEvent(event, entry);
    // Add the code here
  }
}

{% endhighlight %}
{% endtabs %}

### Paint

You can paint this render object into the given context at the given offset.

{% tabs %}
{% highlight Dart %}

late MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = _CustomZoomPanBehavior();
}

@override
Widget build(BuildContext context) {
    return FutureBuilder(
        future: getBingUrlTemplate(
            'https://dev.virtualearth.net/REST/V1/Imagery/Metadata/AerialWithLabels?output=json&uriScheme=https&include=ImageryProviders&key=YOUR_KEY'),
        builder: (context, snapshot) {
            if (snapshot.hasData) {
                return SfMaps(
                    layers: [
                        MapTileLayer(
                            urlTemplate: snapshot.data as String,
                            zoomPanBehavior: _zoomPanBehavior,
                        ),
                    ],
                );
           }
        return CircularProgressIndicator();
        }
    );
}

class _CustomZoomPanBehavior extends MapZoomPanBehavior {

  @override
  void paint(PaintingContext context, Offset offset) {
    super.paint(context, offset);
    // Add the code here
  }
 
}

{% endhighlight %}
{% endtabs %}

N> You can refer to our [Flutter Maps](https://www.syncfusion.com/flutter-widgets/flutter-maps) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Maps Zoom & Pan example](https://flutter.syncfusion.com/#/maps/shape-layer/zooming) that shows how to configure a Maps in Flutter.
