---
layout: post
title:  Accessibility in Flutter Linear Gauge widget | Syncfusion
description: Learn here all about the accessibility support in Syncfusion Flutter Linear Gauge (SfLinearGauge) widget and how to customize it.
platform: Flutter
control: SfLinearGauge
documentation: ug
---

# Accessibility in Flutter Linear Gauge (SfLinearGauge)

## Screen reader

The [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html) can be made accessible to screen readers by wrapping it with the [`Semantics`](https://api.flutter.dev/flutter/widgets/Semantics-class.html) widget.

{% tabs %}
{% highlight Dart %}

double _value = 50;

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Semantics(
      label: 'Syncfusion Flutter Linear Gauge',
      value: _value.toString(),
      child:
          SfLinearGauge(markerPointers: [LinearShapePointer(value: _value)]),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Sufficient contrast

You can customize the color of the [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html) elements using the following APIs to ensure sufficient contrast.

* [`Axis solid color`](https://help.syncfusion.com/flutter/linear-gauge/axis#apply-solid-color)
* [`Axis gradient`](https://help.syncfusion.com/flutter/linear-gauge/axis#apply-gradient)
* [`Ticks`](https://help.syncfusion.com/flutter/linear-gauge/ticks#customize-tick-style)
* [`Labels`](https://help.syncfusion.com/flutter/linear-gauge/labels#customize-label-styles)
* [`Range`](https://help.syncfusion.com/flutter/linear-gauge/getting-started#add-range)
* [`Radial gradient`](https://help.syncfusion.com/flutter/linear-gauge/range#apply-radial-gradient-to-a-range)
* [`Linear gradient`](https://help.syncfusion.com/flutter/linear-gauge/range#apply-linear-gradient-to-a-range)
* [`Sweep gradient`](https://help.syncfusion.com/flutter/linear-gauge/range#apply-sweep-gradient-to-a-range)
* [`Bar pointer`](https://help.syncfusion.com/flutter/linear-gauge/bar-pointer#change-the-color-of-bar-pointer)
* [`Marker`](https://help.syncfusion.com/flutter/linear-gauge/shape-marker-pointer#customize-color)

## Large fonts

You can adjust the font size of the [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html) elements using the following API:

* [`Labels`](https://help.syncfusion.com/flutter/linear-gauge/labels#customize-label-styles)

## Easily touch targets

The [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html) follows accessibility standards by providing touch target of 48 * 48 pixels for all interactive elements.
