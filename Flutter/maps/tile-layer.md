---
layout: post
title: Tile Layer in Syncfusion Flutter maps | Syncfusion
description: This section describes how the tile layer and its features are used in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Tile layer features in maps

An interactive tile layer which renders the tiles returned from web map tile services such as Bing Maps, OpenStreetMaps, Google Maps, TomTom, etc.

## Add URL Template

The [`layers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps/layers.html) in [`SfMaps`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html) contains collection of `MapTileLayer`. The URL of the providers must be set in the `urlTemplate` property of the `MapTileLayer`.

The `urlTemplate` property accepts the URL in WMTS format i.e. {z} — zoom level, {x} and {y} — tile coordinates. This URL might vary slightly depends on the providers. The formats can be,
    https://example_provider/{z}/{x}/{y}.png,
    https://example_provider/z={z}/x={x}/y={y}.png,
    https://example_provider/z={z}/x={x}/y={y}.png?key=subscription_key, etc. We will replace the {z}, {x}, {y} internally based on the current center point and the zoom level. 

Some of the providers may need subscription key to access them. Please include them in the `urlTemplate` itself as mentioned in above example.Please note that the format may vary between the each map providers. You can check the exact URL format needed for the providers in their official websites.

For Bing maps, an additional step is required. The format of the required URL varies from the other tile services. Hence, we have added a top-level [getBingUrlTemplate] method which returns the URL in the required format. You can use the URL returned from this method to pass it to the [urlTemplate] property.

Some of the providers provide different map types. For example, Bing Maps provide map types like Road, Aerial, AerialWithLabels etc. These types too can be passed in the [urlTemplate] itself as shown in the above example. You can check the official websites of the tile providers to know about the available types and the code for it.

{% tabs %}
{% highlight Dart %}


@override
Widget build(BuildContext context) {
    return SfMaps(
        layers: [
            MapTileLayer(
                urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
            ),
        ],
    );
}
 
{% endhighlight %}
{% endtabs %}

## Customizing the focalLatLng

You can able to set the initial focalLatLng by setting the `MapTileLayer.initialFocalLatLng` property. It represents the initial focal latitude and longitude position of the map layer.

Based on the size of the [SfMaps](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html) widget, [initialFocalLatLng] and [initialZoomLevel] number of initial tiles needed in the view port alone will be rendered. While zooming and panning, new tiles will be requested and rendered on demand based on the current zoom level and focal point. The current focal point can be obtained from the [MapZoomPanBehavior.focalLatLng]. 

This property cannot be changed dynamically. Defaults to `MapLatLng(0.0, 0.0)`.

You can also able to set the initial focalLatLng by setting the `MapZoomPanBehavior.focalLatLng` property.

{% tabs %}
{% highlight Dart %}


@override
Widget build(BuildContext context) {
    return SfMaps(
        layers: [
            MapTileLayer(
                urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
                initialFocalLatLng: MapLatLng(27.1751, 78.0421),
            ),
        ],
    );
}
 
{% endhighlight %}
{% endtabs %}

## Customizing the zoom level

You can able to set the initial zoom level by setting the `MapTileLayer.initialFocalLatLng` property. This property cannot be changed dynamically. By default, it will be 1. The current zoom level can be obtained from the [MapZoomPanBehavior.zoomLevel].

You can also able to set the initial zoom level by setting the `MapZoomPanBehavior.zoomLevel` property.

{% tabs %}
{% highlight Dart %}


@override
Widget build(BuildContext context) {
    return SfMaps(
        layers: [
            MapTileLayer(
                urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
                initialFocalLatLng: MapLatLng(27.1751, 78.0421),
                initialZoomLevel: 2,
            ),
        ],
    );
}
 
{% endhighlight %}
{% endtabs %}

## Markers

You can also able to add markers in tile layer. Kindly refer the [markers](https://help.syncfusion.com/flutter/maps/markers#adding-markers) section.

## Tile layer controller

Provides options for adding, removing, deleting, updating markers collection and converting pixel points to latitude and longitude.

{% tabs %}
{% highlight Dart %}

MapTileLayerController _tileLayerController;

@override
void initState() {
    super.initState();
    _tileLayerController = MapTileLayerController();
}

@override
Widget build(BuildContext context) {
    return SfMaps(
        layers: [
            MapTileLayer(
                urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
                initialFocalLatLng: MapLatLng(27.1751, 78.0421),
                initialZoomLevel: 2,
                controller: _tileLayerController,
            ),
        ],
    );
}
 
{% endhighlight %}
{% endtabs %}
