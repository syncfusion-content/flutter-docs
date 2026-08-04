---
layout: post
title: Accessibility in Flutter treemap widget | Syncfusion
description: Learn here all about the accessibility support in Syncfusion Flutter treemap (SfTreemap) widget and how to customize it.
platform: flutter
control: SfTreemap
documentation: ug
---

# Accessibility in Flutter Treemap (SfTreemap)

## Screen reader

The [`SfTreemap`](https://pub.dev/documentation/syncfusion_flutter_treemap/latest/treemap/SfTreemap-class.html) can be accessed by screen readers by wrapping the [`SfTreemap`](https://pub.dev/documentation/syncfusion_flutter_treemap/latest/treemap/SfTreemap-class.html) widget with the [`Semantics`](https://api.flutter.dev/flutter/widgets/Semantics-class.html) widget.

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_treemap/treemap.dart';

class TreemapAccessibilityExample extends StatefulWidget {
  const TreemapAccessibilityExample({super.key});

  @override
  State<TreemapAccessibilityExample> createState() =>
      _TreemapAccessibilityExampleState();
}

class _TreemapAccessibilityExampleState
    extends State<TreemapAccessibilityExample> {
  late List<PopulationModel> _source;
  final String _semanticLabel =
      'Asia is the most populated continent and Australia is the least populated continent';

  @override
  void initState() {
    _source = <PopulationModel>[
      const PopulationModel('Asia', 456.07),
      const PopulationModel('Africa', 121.61),
      const PopulationModel('Europe', 74.64),
      const PopulationModel('North America', 57.9),
      const PopulationModel('South America', 42.25),
      const PopulationModel('Australia', 2.54),
    ];
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Semantics(
        label: 'Syncfusion Flutter Treemap',
        value: _semanticLabel,
        child: SfTreemap(
          dataCount: _source.length,
          weightValueMapper: (int index) {
            return _source[index].populationInCrores;
          },
          levels: [
            TreemapLevel(
              groupMapper: (int index) {
                return _source[index].continent;
              },
            ),
          ],
        ),
      ),
    );
  }
}

class PopulationModel {
  const PopulationModel(this.continent, this.populationInCrores);

  final String continent;
  final double populationInCrores;
}

{% endhighlight %}
{% endtabs %}

## Sufficient contrast

You can customize the color of the [`SfTreemap`](https://pub.dev/documentation/syncfusion_flutter_treemap/latest/treemap/SfTreemap-class.html) elements using the following APIs for the sufficient contrast.

* [`Level`](https://help.syncfusion.com/flutter/treemap/color-customization#level-color)
* [`Labels`](https://help.syncfusion.com/flutter/treemap/labels)
* [`Legend`](https://help.syncfusion.com/flutter/treemap/legend#icon-and-text-customization)
* [`Tooltip`](https://help.syncfusion.com/flutter/treemap/tooltip#appearance-customization)

## Large fonts

The font size of the [`SfTreemap`](https://pub.dev/documentation/syncfusion_flutter_treemap/latest/treemap/SfTreemap-class.html) will be automatically scaled based on the device settings. Additionally, you can change the font size of the [`SfTreemap`](https://pub.dev/documentation/syncfusion_flutter_treemap/latest/treemap/SfTreemap-class.html) elements using the following APIs:

* [`Label style`](https://help.syncfusion.com/flutter/treemap/labels#add-labels)
* [`Legend text style`](https://help.syncfusion.com/flutter/treemap/legend#text-style)
* [`Tooltip label style`](https://help.syncfusion.com/flutter/treemap/tooltip#tooltip-for-the-tiles)

## Easier touch targets

The [`SfTreemap`](https://pub.dev/documentation/syncfusion_flutter_treemap/latest/treemap/SfTreemap-class.html) has touch targets of 48 × 48 pixels for all elements, following standard accessibility guidelines.