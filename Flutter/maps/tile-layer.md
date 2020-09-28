---
layout: post
title: Tile Layer in Syncfusion Flutter maps | Syncfusion
description: This section explains how to use the tile layer in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Tile layer features in maps

An interactive tile layer which renders the tiles returned from web map tile services such as Bing Maps, OpenStreetMaps, Google Maps, TomTom, etc.

## Add URL Template

The [`layers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps/layers.html) in [`SfMaps`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html) contains collection of `MapTileLayer`. The URL of the providers must be set in the `urlTemplate` property of the `MapTileLayer`.

The `urlTemplate` property accepts the URL in WMTS format i.e. {z} — zoom level, {x} and {y} — tile coordinates. This URL might vary slightly depends on the providers. The formats can be,
    https://exampleprovider/{z}/{x}/{y}.png,
    https://exampleprovider/z={z}/x={x}/y={y}.png,
    https://exampleprovider/z={z}/x={x}/y={y}.png?key=subscription_key, etc. 
    
We will replace the {z}, {x}, {y} internally based on the current center point and the zoom level. Some of the providers may need subscription key to access them. Please include them in the [urlTemplate] itself as mentioned in above example.

Regarding the cache and clearing it, please check the APIs in [imageCache](https://api.flutter.dev/flutter/painting/imageCache.html).

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

## Markers

You can also able to add markers to denote the locations. It is possible to use the built-in symbols or display a custom widget at a specific latitude and longitude on a map.