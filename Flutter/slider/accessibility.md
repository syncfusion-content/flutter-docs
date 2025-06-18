---
layout: post
title:  Accessibility in Flutter Slider widget | Syncfusion
description: Learn here all about the accessibility support in Syncfusion Flutter Slider (SfSlider) widget and how to customize the text.
platform: Flutter
control: SfSlider
documentation: ug
---

# Accessibility in Flutter Slider (SfSlider)

## Keyboard support

This feature allows you to focus on the [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html) widget using the TAB key and adjust its values with the keyboard arrow keys. The left and down arrow keys can be used to decrease the thumb value, while the right and up arrow keys can be used to increase it.

## Screen reader

The [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html) can be accessed by screen readers. By default, it will read the current value. You can change the reading format using the [`semanticFormatterCallback`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/semanticFormatterCallback.html) property.

For Android, you can adjust the value of the thumb by moving the focus to it and then pressing the volume buttons to increase or decrease the value.

For iOS, you can adjust the value of the thumb by moving the focus to it and then swiping up or down to increase or decrease the value respectively.

### Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 40.0;

@override
Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
              min: 0.0,
              max: 100.0,
              value: _value,
              interval: 20,
              showTicks: true,
              showLabels: true,
              semanticFormatterCallback: (dynamic value){
                return 'The selected value is $value';
              },
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
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

double _value = 40.0;

@override
Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
              min: 0.0,
              max: 100.0,
              value: _value,
              interval: 20,
              showTicks: true,
              showLabels: true,
              semanticFormatterCallback: (dynamic value){
                return 'The selected value is $value';
              },
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
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

You can customize the color of the [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html) elements using the following APIs for the sufficient contrast.

* [`Track`](https://help.syncfusion.com/flutter/slider/track#track-color)
* [`Major ticks`](https://help.syncfusion.com/flutter/slider/ticks#major-ticks-color)
* [`Minor ticks`](https://help.syncfusion.com/flutter/slider/ticks#minor-ticks-color)
* [`Labels`](https://help.syncfusion.com/flutter/slider/labels-and-divider#show-labels)
* [`Dividers`](https://help.syncfusion.com/flutter/slider/labels-and-divider#show-dividers)
* [`Thumb`](https://help.syncfusion.com/flutter/slider/thumb-and-overlay#thumb-color)
* [`Thumb overlay`](https://help.syncfusion.com/flutter/slider/thumb-and-overlay#thumb-overlay-color)

## Large fonts

The font size of the [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html) will be automatically scaled based on the device settings. Additionally, you can change the font size of the [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html) elements using the following APIs:

* [`Label style`](https://help.syncfusion.com/flutter/slider/labels-and-divider#label-style)
* [`Tooltip label style`](https://help.syncfusion.com/flutter/slider/tooltip#tooltip-label-style)

## Easier touch targets

The [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html) has touch target as 48 * 48 as per the standard for all the elements.
