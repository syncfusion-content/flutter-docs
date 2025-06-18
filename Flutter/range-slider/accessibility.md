---
layout: post
title: Accessibility in Flutter Range Slider widget | Syncfusion
description: Learn here all about the accessibility support in Syncfusion Flutter Range Slider (SfRangeSlider) widget.
platform: Flutter
control: SfRangeSlider
documentation: ug
---

# Accessibility in Flutter Range Slider (SfRangeSlider)

## Keyboard support

This feature allows you to focus on the [`SfRangeSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider-class.html) widget using the TAB key and adjust its values with the keyboard arrow keys. By default, the start thumb receives focus first. You can press the TAB key again to move focus to the end thumb. The left and down arrow keys can be used to decrease the value of the focused thumb, while the right and up arrow keys can be used to increase it.

N> In [`SfRangeSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider-class.html), keyboard accessibility is not supported when [`dragMode`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector/dragMode.html) is set to `SliderDragMode.betweenThumbs`, as focus can only be applied to one thumb at a time.

## Screen reader

The [`SfRangeSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider-class.html) can be accessed by screen readers. The default reading format for start thumb is `The start value is ${values.start}` and end thumb is `the end value is ${values.end}`. You can change the reading format using the [`semanticFormatterCallback`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/semanticFormatterCallback.html) property.

For Android, you can adjust the value of each thumb by moving the focus to it and then pressing the volume buttons to increase or decrease the value.

For iOS, you can adjust the value of each thumb by moving the focus to it and then swiping up or down to increase or decrease the value respectively.

### Horizontal

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(40.0, 60.0);

@override
Widget build(BuildContext context) {
   return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfRangeSlider(
              min: 0.0,
              max: 100.0,
              values: _values,
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
            ),
          )
      ),
   );
}

{% endhighlight %}
{% endtabs %}

### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(40.0, 60.0);

@override
Widget build(BuildContext context) {
   return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfRangeSlider.vertical(
              min: 0.0,
              max: 100.0,
              values: _values,
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
            ),
          )
      ),
   );
}

{% endhighlight %}
{% endtabs %}

## Sufficient contrast

You can customize the color of the [`SfRangeSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider-class.html) elements using the following APIs for the sufficient contrast.

* [`Track`](https://help.syncfusion.com/flutter/range-slider/track#track-color)
* [`Major ticks`](https://help.syncfusion.com/flutter/range-slider/ticks#major-ticks-color)
* [`Minor ticks`](https://help.syncfusion.com/flutter/range-slider/ticks#minor-ticks-color)
* [`Labels`](https://help.syncfusion.com/flutter/range-slider/labels-and-divider#show-labels)
* [`Dividers`](https://help.syncfusion.com/flutter/range-slider/labels-and-divider#show-dividers)
* [`Thumb`](https://help.syncfusion.com/flutter/range-slider/thumb-and-overlay#thumb-color)
* [`Thumb overlay`](https://help.syncfusion.com/flutter/range-slider/thumb-and-overlay#thumb-overlay-color)

## Large fonts

The font size of the [`SfRangeSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider-class.html) will be automatically scaled based on the device settings. Also, you can change the font size of the [`SfRangeSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider-class.html) elements using the following APIs:

* [`Label style`](https://help.syncfusion.com/flutter/range-slider/labels-and-divider#label-style)
* [`Tooltip label style`](https://help.syncfusion.com/flutter/range-slider/tooltip#tooltip-label-style)

## Easily touch targets

The [`SfRangeSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider-class.html) has touch target as 48 * 48 as per the standard for all the elements.
