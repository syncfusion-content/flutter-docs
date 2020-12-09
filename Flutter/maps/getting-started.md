---
layout: post
title: Getting Started for Syncfusion Flutter Maps | Syncfusion
description: This section explains the steps required to add the maps widget and its elements such as data labels, markers, bubbles, and legends.
platform: Flutter
control: SfMaps
documentation: ug
---

# Getting Started with Flutter Maps (SfMaps)
This section explains the steps required to add the maps widget with shape layer and its elements such as data labels, tooltip, title, assignable colors based on region, and legends. It also explains about adding tile layer with OpenStreetMap. This section covers only basic features needed to know to get started with Syncfusion maps.

## Add Flutter maps to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter maps dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_maps: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter Maps`](https://pub.dev/packages/syncfusion_flutter_maps/versions) package.

**Get packages**

Run the following command to get the required packages.

{% highlight dart %}

$ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_maps/maps.dart';

{% endhighlight %}
{% endtabs %}

## Initialize maps

After importing the package, initialize the maps widget as a child of any widget.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: SfMaps(),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Add a GeoJSON file for shape layer

The [`layers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps/layers.html) in [`SfMaps`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html) contains collection of [`MapShapeLayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer-class.html). The actual geographical rendering is done in the each [`MapShapeLayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer-class.html). The [`delegate`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/delegate.html) property of the [`MapShapeLayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer-class.html) is of type [`MapShapeLayerDelegate`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate-class.html). The path of the .json file which contains the GeoJSON data has to be set to the [`shapeFile`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeFile.html) property of the [`MapShapeLayerDelegate`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate-class.html).

The [`shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeDataField.html) property of the [`MapShapeLayerDelegate`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate-class.html) is used to refer the unique field name in the .json file to identify each shapes. In 'Mapping the data source' section of this document, this [`shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeDataField.html) will be used to map with respective value returned in [`primaryValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/primaryValueMapper.html) from the data source.

N> You can get the [`australia.json`](https://www.syncfusion.com/downloads/support/directtrac/general/ze/australia-json-910278184.zip) file here. Add this json file to the assets folder of your root directory and refer the json file path in the `pubspec.yaml` file.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.all(15),
      child: SfMaps(
        layers: [
          MapShapeLayer(
            delegate: const MapShapeLayerDelegate(
              shapeFile: 'assets/australia.json',
              shapeDataField: 'STATE_NAME',
            ),
          ),
        ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![maps basic view](images/getting-started/map_basic_view.png)

## Mapping the data source for shape layer

By default, the value specified for the [`shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeDataField.html) in the GeoJSON file will be used in the elements like data labels, tooltip, and legend for their respective shapes. However, it is possible to keep a data source and customize these elements based on the requirement. As mentioned above, [`shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeDataField.html) will be used to map with respective value returned in [`primaryValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/primaryValueMapper.html) from the data source.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
  data = <Model>[
    Model('New South Wales',
     '       New\nSouth Wales'),
    Model('Queensland', 'Queensland'),
    Model('Northern Territory', 'Northern\nTerritory'),
    Model('Victoria', 'Victoria'),
    Model('South Australia', 'South Australia'),
    Model('Western Australia', 'Western Australia'),
    Model('Tasmania', 'Tasmania'),
    Model('Australian Capital Territory', 'ACT')
  ];

  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfMaps(
       layers: <MapShapeLayer>[
         MapShapeLayer(
           delegate: MapShapeLayerDelegate(
             shapeFile: 'assets/australia.json',
             shapeDataField: 'STATE_NAME',
             dataCount: data.length,
             primaryValueMapper: (int index) => data[index].state,
           ),
         ),
       ],
     ),
   );
}

class Model {
  Model(this.state, this.stateCode);

  String state;
  String stateCode;
}

{% endhighlight %}
{% endtabs %}

N>
* Refer the [`MapShapeLayerDelegate.primaryValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/primaryValueMapper.html), for mapping the data of the data source collection with the respective [`MapShapeLayerDelegate.shapeDataField`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeDataField.html) in .json file.
* Refer the [`MapShapeLayerDelegate.bubbleSizeMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/bubbleSizeMapper.html), for customizing the bubble size.
* Refer the [`MapShapeLayerDelegate.bubbleColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/bubbleColorValueMapper.html), for customizing the bubble colors.
* Refer the [`MapShapeLayerDelegate.dataLabelMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/dataLabelMapper.html), for customizing the data label text.
* Refer the [`MapShapeLayerDelegate.shapeTooltipTextMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeTooltipTextMapper.html), for customizing the shape tooltip text.
* Refer the [`MapShapeLayerDelegate.bubbleTooltipTextMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/bubbleTooltipTextMapper.html), for customizing the bubble tooltip text.
* Refer the [`MapShapeLayerDelegate.shapeColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeColorValueMapper.html), for customizing the bubble colors.

## Add shape layer maps elements

Add the basic maps elements such as title, data labels, legend, and tooltip as shown in the below code snippet.

* **Title** - You can add a title to the maps to provide a quick information about the data plotted in the map using the [`SfMaps.title`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps/title.html) property.

* **Data labels** - You can show data labels using the [`MapShapeLayer.showDataLabels`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/showDataLabels.html) property and also, it is possible to show data labels only for the particular shapes/or show custom text using the [`MapShapeLayerDelegate.dataLabelMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/dataLabelMapper.html) property.

* **Legend** - You can show legend using the [`MapShapeLayer.showLegend`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/showLegend.html) property. The icons color of the legend is applied based on the colors returned in the [`MapShapeLayerDelegate.shapeColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeColorValueMapper.html) property. It is possible to customize the legend icons color and texts using the [`MapShapeLayerDelegate.shapeColorMappers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeColorMappers.html) property.

* **Tooltip** - You can enable tooltip for the shapes using the [`MapShapeLayer.enableShapeTooltip`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/enableShapeTooltip.html) property and also, it is possible to enable tooltip only for the particular shapes/or show custom text using the [`MapShapeLayerDelegate.shapeTooltipTextMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeTooltipTextMapper.html) property.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    data = <Model>[
      Model('New South Wales', Color.fromRGBO(255, 215, 0, 1.0),
          '       New\nSouth Wales'),
      Model('Queensland', Color.fromRGBO(72, 209, 204, 1.0), 'Queensland'),
      Model('Northern Territory', Colors.red.withOpacity(0.85),
          'Northern\nTerritory'),
      Model('Victoria', Color.fromRGBO(171, 56, 224, 0.75), 'Victoria'),
      Model('South Australia', Color.fromRGBO(126, 247, 74, 0.75),
          'South Australia'),
      Model('Western Australia', Color.fromRGBO(79, 60, 201, 0.7),
          'Western Australia'),
      Model('Tasmania', Color.fromRGBO(99, 164, 230, 1), 'Tasmania'),
      Model('Australian Capital Territory', Colors.teal, 'ACT')
    ];
    super.initState();
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          height: 520,
          child: Padding(
            padding: EdgeInsets.all(15),
            child: SfMaps(
              title: const MapTitle(text: 'Australia map'),
              layers: <MapShapeLayer>[
                MapShapeLayer(
                  delegate: MapShapeLayerDelegate(
                    shapeFile: 'assets/australia.json',
                    shapeDataField: 'STATE_NAME',
                    dataCount: data.length,
                    primaryValueMapper: (int index) => data[index].state,
                    dataLabelMapper: (int index) => data[index].stateCode,
                    shapeColorValueMapper: (int index) => data[index].color,
                    shapeTooltipTextMapper: (int index) => data[index].stateCode,
                  ),
                  showDataLabels: true,
                  showLegend: true,
                  enableShapeTooltip: true,
                  tooltipSettings: MapTooltipSettings(color: Colors.grey[700],
                      strokeColor: Colors.white, strokeWidth: 2
                  ),
                  strokeColor: Colors.white,
                  strokeWidth: 0.5,
                  dataLabelSettings: MapDataLabelSettings(
                      textStyle: TextStyle(
                          color: Colors.black,
                          fontWeight: FontWeight.bold,
                          fontSize:
                          Theme
                              .of(context)
                              .textTheme
                              .caption
                              .fontSize)),
                ),
              ],
            ),
          ),
        ),
      ),
   );
}

class Model {
  Model(this.state, this.color, this.stateCode);

  String state;
  Color color;
  String stateCode;
}

{% endhighlight %}
{% endtabs %}

![Maps getting started](images/getting-started/maps_getting_started.png)

## Add tile layer

The [`MapTileLayer`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapTileLayer-class.html) needs to be added in the [`layers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps/layers.html) collection in [`SfMaps`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html). The URL of the providers must be set in the [`MapTileLayer.urlTemplate`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapTileLayer/urlTemplate.html) property.

Kindly refer the [tile layer](https://help.syncfusion.com/flutter/maps/tile-layer#setting-url-template) section for more information.

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

![Maps tile layer getting started](images/getting-started/getting_started_tile_layer.png)
