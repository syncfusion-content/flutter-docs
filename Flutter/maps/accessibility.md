---
layout: post
title:  Accessibility in Flutter maps widget | Syncfusion
description: Learn here all about the accessibility support in Syncfusion Flutter maps (SfMaps) widget and how to customize it.
platform: Flutter
control: SfMaps
documentation: ug
---

# Accessibility in Flutter Maps (SfMaps)

## Screen reader

The [`SfMaps`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html) widget can be accessed by the screen readers by wrapping it with the [`Semantics`](https://api.flutter.dev/flutter/widgets/Semantics-class.html) widget.

{% tabs %}
{% highlight Dart %}

  late List<PopulationModel> _data;
  late MapShapeSource _dataSource;
  late String _semanticLabel = 'Asia is the most populated continent and Australia is the least populated continent';

  @override
  void initState() {
    _data = const <PopulationModel>[
        PopulationModel('Asia', 456.07),
        PopulationModel('Africa', 121.61),
        PopulationModel('Europe', 74.64),
        PopulationModel('North America', 57.9),
        PopulationModel('South America', 42.25),
        PopulationModel('Australia', 2.54),
    ];

    _dataSource = MapShapeSource.asset(
        'assets/world_map.json',
        shapeDataField: 'continent',
        dataCount: _data.length,
        primaryValueMapper: (int index) => _data[index].continent,
    );
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Semantics(
          label: 'Syncfusion Flutter Maps',
          value: _semanticLabel,
          child: SfMaps(
            layers: <MapLayer>[
              MapShapeLayer(source: _dataSource)
            ]
          ),
        ),
      ),
    );
  }

class PopulationModel {
  const PopulationModel(this.continent, this.populationInCrores);

  final String continent;
  final double populationInCrores;
}

{% endhighlight %}
{% endtabs %}

## Sufficient contrast

You can customize the color of the [`SfMaps`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html) elements using the following APIs to ensure sufficient contrast:

* [`Shape`](https://help.syncfusion.com/flutter/maps/shape#shape-color)
* [`Bubble`](https://help.syncfusion.com/flutter/maps/bubble#color)
* [`Data labels`](https://help.syncfusion.com/flutter/maps/data-labels#appearance-customization)
* [`Legend`](https://help.syncfusion.com/flutter/maps/legend#icon-and-text-customization)
* [`Tooltip`](https://help.syncfusion.com/flutter/maps/tooltip#appearance-customization)
* [`Sublayer`](https://help.syncfusion.com/flutter/maps/shape-sublayer#color-and-stroke-color)
* [`Line layer`](https://help.syncfusion.com/flutter/maps/vector-layers/line-layer#color)
* [`Arc layer`](https://help.syncfusion.com/flutter/maps/vector-layers/arc-layer#color)
* [`Polyline layer`](https://help.syncfusion.com/flutter/maps/vector-layers/polyline-layer#color)
* [`Polygon layer`](https://help.syncfusion.com/flutter/maps/vector-layers/polygon-layer#fill-color)
* [`Circle layer`](https://help.syncfusion.com/flutter/maps/vector-layers/circle-layer#fill-color)

## Large fonts

The font size of the [`SfMaps`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html) will automatically scale based on the device settings.

Additionally, you can manually adjust the font size of the [`SfMaps`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html) elements using these APIs:

* [`Data label style`](https://help.syncfusion.com/flutter/maps/data-labels#appearance-customization)
* [`Legend text style`](https://help.syncfusion.com/flutter/maps/legend#text-style)
* [`Tooltip label style`](https://help.syncfusion.com/flutter/maps/tooltip#tooltip-for-the-shapes)

## Easier touch targets

The [`SfMaps`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/SfMaps-class.html) widget provides touch targets of 48 × 48 pixels as per accessibility standards for all applicable elements.