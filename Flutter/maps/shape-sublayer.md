---
layout: post
title: Shape Sublayer in Syncfusion Flutter maps | Syncfusion
description: This section explains how to add the shape sublayer for tile and shape layer and enable its features.
platform: Flutter
control: SfMaps
documentation: ug
---

# Shape sublayer features in Maps

The shape sublayer is where geographical rendering will happen for the sublayer. This is similar to the main [`shape layer`](https://help.syncfusion.com/flutter/maps/getting-started#add-a-geojson-file-for-shape-layer) rendering. This section explains adding a shape sublayer on the shape layer and tile layer.

## Shape sublayer on tile layer

The [`sublayers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapTileLayer/MapTileLayer.html) in [`MapTileLayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapTileLayer-class.html) contains collection of [`MapSublayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/sublayers.html).The actual geographical rendering is done in the each [`MapShapeSublayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSublayer-class.html). The [`source`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/source.html) property of the [`MapShapeSublayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSublayer-class.html) is of type [`MapShapeSource`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource-class.html). The path of the .json file which contains the GeoJSON data has to be set to the [`MapShapeSource`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource-class.html).

The [`shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/shapeDataField.html) property of the [`MapShapeSource`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource-class.html) is used to refer the unique field name in the .json file to identify each shapes.

{% tabs %}
{% highlight Dart %}

MapShapeSource _sublayerSource;

@override
void initState() {
  super.initState();

  _sublayerSource = MapShapeSource.asset(
      'assets/australia.json',
      shapeDataField: 'name',
  );
}

@override
Widget build(BuildContext context) {
return Scaffold(
    body: Padding(
      padding: const EdgeInsets.only(left: 15, right: 15),
      child: SfMaps(
        layers: [
            MapTileLayer(
              urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
              sublayers: [
                MapShapeSublayer(
                  source: _sublayerSource,
                ),
              ],
            ),
          ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

N>
* Refer the [`MapTileLayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapTileLayer-class.html), for adding tile layer in [`SfMaps`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html).

## Shape sublayer on shape layer

The [`sublayers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/MapShapeLayer.html) in [`MapShapeLayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer-class.html) contains collection of [`MapSublayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapLayer/sublayers.html).The actual geographical rendering is done in the each [`MapShapeSublayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSublayer-class.html). The [`source`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/source.html) property of the [`MapShapeSublayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSublayer-class.html) is of type [`MapShapeSource`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource-class.html). The path of the .json file which contains the GeoJSON data has to be set to the [`MapShapeSource`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource-class.html).

The [`shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource/shapeDataField.html) property of the [`MapShapeSource`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeSource-class.html) is used to refer the unique field name in the .json file to identify each shapes.

{% tabs %}
{% highlight Dart %}

MapShapeSource _shapeSource;
MapShapeSource _sublayerSource;

@override
void initState() {
  super.initState();
  _shapeSource = MapShapeSource.asset(
      "assets/world_map.json",
      shapeDataField: "continent",
  );

  _sublayerSource = MapShapeSource.asset(
      'assets/africa.json',
      shapeDataField: 'name',
  );
}

@override
Widget build(BuildContext context) {
return Scaffold(
    body: Padding(
      padding: const EdgeInsets.only(left: 15, right: 15),
      child: SfMaps(
        layers: [
            MapShapeLayer(
              source: _shapeSource,
              sublayers: [
                MapShapeSublayer(
                  source: _sublayerSource,
                ),
              ],
            ),
          ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

N>
* Refer the [`MapShapeLayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer-class.html), for adding shape layer in [`SfMaps`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html).