---
layout: post
title: Zoom Pan in Syncfusion Flutter maps | Syncfusion
description: This section explains how to perform zooming and panning in shape and tile layer in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Zooming and Panning features in maps

Zoom in the any layer for a closer look at a specific region by pinching or double tapping the map, scrolling the mouse wheel or track pad, or using the toolbar on the web. Pan the map to navigate across the regions. You can also customize the zoom level and the center point of the initial rendering.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = MapZoomPanBehavior();
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

## Customizing the focalLatLng

The `MapZoomPanBehavior.focalLatLng` is the focal point of the map layer based on which zooming happens.It represents the focal latitude and longitude position of the map layer.You can also get the current focalLatLng after interaction using the [MapZoomPanBehavior.focalLatLng] property.

This properties can be changed dynamically. Defaults to `MapLatLng(0.0, 0.0)`.

To perform panning, enable the `MapZoomPanBehavior.enablePanning`property. By default it will be `true`.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = MapZoomPanBehavior(
        focalLatLng: MapLatLng(27.1751, 78.0421),
    );
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

N>
* Current map layer `onWillPan` should return `true`.

## Customizing the zoom level

You can able to set the current zoom level of the map layer by using `MapZoomPanBehavior.zoomLevel`property. Current zoom level of the map layer.

The default [zoomLevel] value is 1 which will show the whole map in the viewport for [MapShapeLayer] and the possible bounds for the [MapTileLayer] based on the [focalLatLng]. You can also get the current zoom level after interaction using the [MapZoomPanBehavior.zoomLevel] property.

This properties can be changed dynamically.

To perform zooming, enable the `MapZoomPanBehavior.enablePinching`property. By default it will be `true`.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = MapZoomPanBehavior(
        focalLatLng: MapLatLng(27.1751, 78.0421),
        zoomLevel: 4,
    );
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

N>
* Current map layer `onWillZoom` should return `true`.

## Customizing min and max zoom level

You can able to set the min and max zoom level of the map layer by setting the value to `MapZoomPanBehavior.minZoomLevel` and `MapZoomPanBehavior.maxZoomLevel`properties. The minimum and maximum zooming levels can be restricted using these properties respectively. The default values of `MapZoomPanBehavior.minZoomLevel` and `MapZoomPanBehavior.maxZoomLevel` are 0 and 15 respectively.

However, for [MapTileLayer.maxZoomLevel] may slightly vary depends on the providers. Kindly check the respective official website of the map tile providers to know about the maximum zoom level it supports.

{% tabs %}
{% highlight Dart %}

MapZoomPanBehavior _zoomPanBehavior;

@override
void initState() {
    super.initState();
    _zoomPanBehavior = MapZoomPanBehavior(
        focalLatLng: MapLatLng(27.1751, 78.0421),
        zoomLevel: 4,
        minZoomLevel: 3,
        maxZoomLevel: 10,
    );
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

## Toolbar

Toolbar with the options for changing the visible bound for the web platform. By default, the [MapZoomPanBehavior.showToolbar] property is enabled.

N>
* Refer [MapZoomPanBehavior.toolbarSettings] for customizing the appearance of the toolbar. You can able to customize its positions, direction, icon color, item hover color and item background color.

## Overriding the zoom pan behavior

### onZooming

Whenever zooming happens, this method is called. Subclasses can override this method to do any custom operations based on the details provided in the [MapZoomDetails].

[MapZoomDetails] contains following properties,
    * [MapZoomDetails.previousVisibleBounds] - provides the visible bounds before the current zooming operation completes i.e. current visible bounds.
    * [MapZoomDetails.newVisibleBounds] - provides the new visible bounds when the current zoom completes. Hence, if the
    `super.onZooming(details)` is not called, there will be no changes in the UI.
    * [MapZoomDetails.previousZoomLevel] - provides the zoom level before the current zooming operation completes i.e. current zoom level.
    * [MapZoomDetails.newZoomLevel] - provides the new zoom level when the current zoom completes. Hence, if the
    `super.onZooming(details)` is not called, there will be no changes in the UI.
    * [MapZoomDetails.globalFocalPoint] - The global focal point of the pointers in contact with the screen.
    * [MapZoomDetails.localFocalPoint] - The local focal point of the pointers in contact with the screen.

N>
* When `super.onZooming(details)` is not called, zooming will not happen.

### onPanning

Whenever panning happens, this method is called. Subclasses can override this method to do any custom operations based on the details provided in the [MapPanDetails]. 
  
[MapPanDetails] contains following properties,
    * [MapPanDetails.previousVisibleBounds] - provides the visible bounds before the current panning operation completes i.e. current visible bounds.
    * [MapPanDetails.newVisibleBounds] - provides the new visible bounds when the current pan completes. Hence, if the
    `super.onPanning(details)` is not called, there will be no changes in the UI.
    * [MapPanDetails.zoomLevel] - provides the current zoom level.
    * [MapPanDetails.delta] - The difference in pixels between touch start and current touch position.
    * [MapPanDetails.globalFocalPoint] - The global focal point of the pointers in contact with the screen.
    * [MapPanDetails.localFocalPoint] - The local focal point of the pointers in contact with the screen.

N>
* When `super.onPanning(details)` is not called, panning will not happen.

### reset

When this method is called, the map will be reset to the [MapZoomPanBehavior.minZoomLevel].

### handleEvent

Override this method to handle pointer events that hit this render object. 

N>
* When `super.handleEvent(event, entry)` is not called, handle event will not happen.

### paint

Paint this render object into the given context at the given offset.



