---
layout: post
title:  Accessibility in Flutter Radial Gauge widget | Syncfusion
description: Learn here all about the accessibility support in Syncfusion Flutter Radial Gauge (SfRadialGauge) widget and how to customize it.
platform: Flutter
control: SfRadialGauge
documentation: ug
---

# Accessibility in Flutter Radial Gauge (SfRadialGauge)

## Screen reader

The [`SfRadialGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge-class.html) can be accessed by the screen readers by wrapping the [`SfRadialGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge-class.html) widget to the [`Semantics`](https://api.flutter.dev/flutter/widgets/Semantics-class.html) widget.

{% tabs %}
{% highlight Dart %}

double _value = 50;

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Semantics(
      label: 'Syncfusion Flutter Radial Gauge',
      value: _value.toString(),
      child: SfRadialGauge(axes: <RadialAxis>[
        RadialAxis(pointers: <GaugePointer>[NeedlePointer(value: _value)])
      ]),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Sufficient contrast

You can customize the color of the [`SfRadialGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge-class.html) elements using the following APIs for the sufficient contrast.

* [`Title`](https://help.syncfusion.com/flutter/radial-gauge/radial-gauge-title#text-alignment)
* [`Axis labels`](https://help.syncfusion.com/flutter/radial-gauge/axes#label-style-customization)
* [`Ticks`](https://help.syncfusion.com/flutter/radial-gauge/axes#tick-customization)
* [`Annotation`](https://help.syncfusion.com/flutter/radial-gauge/annotation#alignment-of-annotation)
* [`Marker pointer`](https://help.syncfusion.com/flutter/radial-gauge/marker-pointer#marker-customization)
* [`Text pointer`](https://help.syncfusion.com/flutter/radial-gauge/marker-pointer#text-pointer)
* [`Knob`](https://help.syncfusion.com/flutter/radial-gauge/needle-pointer#knob-customization)
* [`Tail`](https://help.syncfusion.com/flutter/radial-gauge/needle-pointer#tail-customization)
* [`Range pointer`](https://help.syncfusion.com/flutter/radial-gauge/ranges#range-customization)

## Large fonts

You can change the font size of the [`SfRadialGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge-class.html) elements using the following APIs:

* [`Title`](https://help.syncfusion.com/flutter/radial-gauge/radial-gauge-title#text-alignment)
* [`Axis labels`](https://help.syncfusion.com/flutter/radial-gauge/axes#label-style-customization)
* [`Annotation`](https://help.syncfusion.com/flutter/radial-gauge/annotation#alignment-of-annotation)

## Easier touch targets

The [`SfRadialGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge-class.html) has touch target as 48 * 48 as per the standard for all the elements.
