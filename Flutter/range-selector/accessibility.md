---
layout: post
title:  Accessibility in Flutter Range Selector widget | Syncfusion
description: Learn here all about the accessibility support in Syncfusion Flutter Range Selector (SfRangeSelector) widget.
platform: Flutter
control: SfRangeSelector
documentation: ug
---

# Accessibility in Flutter Range Selector (SfRangeSelector)

## Keyboard support

This feature allows users to navigate to the [`SfRangeSelector`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html) widget using the TAB key and adjust its values using the keyboard arrow keys. The left and down arrow keys can be used to decrease the selection value, while the right and up arrow keys can be used to increase it.

N> In [`SfRangeSelector`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html), keyboard accessibility is not supported when [`dragMode`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector/dragMode.html) is set to `SliderDragMode.betweenThumbs`, as focus can only be applied to one thumb at a time.

## Screen reader

The [`SfRangeSelector`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html) can be accessed by screen readers. The default reading format for start thumb is `The start value is ${values.start}` and end thumb is `the end value is ${values.end}`. You can change the reading format using the [`semanticFormatterCallback`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector/semanticFormatterCallback.html) property.

For Android, you can adjust the value of each thumb by moving the focus to the thumb and then pressing the volume buttons to increase or decrease the value.

For iOS, you can adjust the value of each thumb by moving the focus to the thumb and then swiping up or down to increase or decrease the value respectively.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(40.0, 60.0);

@override
Widget build(BuildContext context) {
   return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfRangeSelector(
              min: 0.0,
              max: 100.0,
              initialValues: _values,
              interval: 20,
              showTicks: true,
              showLabels: true,
              semanticFormatterCallback: (dynamic value, SfThumb thumb){
                return 'The $thumb value is $value';
              },
              onChanged: (SfRangeValues newValues) {
                setState(() {
                  _values = newValues;
                });
              },
              child: Container(
                height: 200,
                color: Colors.pink[200],
              ),
            ),
          )
      ),
   );
}

{% endhighlight %}
{% endtabs %}

## Sufficient contrast

You can customize the color of the [`SfRangeSelector`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html) elements using the following APIs for the sufficient contrast.

* [`Track`](https://help.syncfusion.com/flutter/range-selector/track#track-color)
* [`Major ticks`](https://help.syncfusion.com/flutter/range-selector/ticks#major-ticks-color)
* [`Minor ticks`](https://help.syncfusion.com/flutter/range-selector/ticks#minor-ticks-color)
* [`Labels`](https://help.syncfusion.com/flutter/range-selector/labels-and-divider#show-labels)
* [`Dividers`](https://help.syncfusion.com/flutter/range-selector/labels-and-divider#show-dividers)
* [`Thumb`](https://help.syncfusion.com/flutter/range-selector/thumb-and-overlay#thumb-color)
* [`Thumb overlay`](https://help.syncfusion.com/flutter/range-selector/thumb-and-overlay#thumb-overlay-color)
* [`Active region color`](https://help.syncfusion.com/flutter/range-selector/basic-features#active-region-color)
* [`Inactive region color`](https://help.syncfusion.com/flutter/range-selector/basic-features#inactive-region-color)

## Large fonts

The font size of the [`SfRangeSelector`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html) will be automatically scaled based on the device settings. Also, you can change the font size of the [`SfRangeSelector`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html) elements using the following APIs:

* [`Label style`](https://help.syncfusion.com/flutter/range-selector/labels-and-divider#label-style)
* [`Tooltip label style`](https://help.syncfusion.com/flutter/range-selector/tooltip#tooltip-label-style)

## Easier touch targets

The [`SfRangeSelector`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html) has touch target as 48 * 48 as per the standard for all the elements.
