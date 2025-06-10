---
layout: post
title:  Accessibility in Flutter treemap widget | Syncfusion
description: Learn here all about the accessibility support in Syncfusion Flutter treemap (SfTreemap) widget and how to customize it.
platform: Flutter
control: SfTreemap
documentation: ug
---

# Accessibility in Flutter Treemap (SfTreemap)

## Screen reader

The [`SfTreemap`](https://pub.dev/documentation/syncfusion_flutter_treemap/latest/treemap/SfTreemap-class.html) can be accessed by the screen readers by wrapping the [`SfTreemap`](https://pub.dev/documentation/syncfusion_flutter_treemap/latest/treemap/SfTreemap-class.html) widget to the [`Semantics`](https://api.flutter.dev/flutter/widgets/Semantics-class.html) widget.

{% tabs %}
{% highlight Dart %}

late List<PopulationModel> _source;
late String _semanticLabel = 'Asia is the most populated continent and Australia is the least populated continent';

@override
void initState() {
   _source = const <PopulationModel>[
      PopulationModel('Asia', 456.07),
      PopulationModel('Africa', 121.61),
      PopulationModel('Europe', 74.64),
      PopulationModel('North America', 57.9),
      PopulationModel('South America', 42.25),
      PopulationModel('Australia', 2.54),
   ];
   super.initState();
}

@override
void dispose() {
  _source.clear();
  super.dispose();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: Semantics(
        label: 'Syncfusion Flutter Treemap',
        value: _semanticLabel,
        child: Column(
          children: [
            Expanded(
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
          ],
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

The [`SfTreemap`](https://pub.dev/documentation/syncfusion_flutter_treemap/latest/treemap/SfTreemap-class.html) has touch target as 48 * 48 for all elements, following standard accessibility guidelines.