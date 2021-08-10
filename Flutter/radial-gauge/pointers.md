---
layout: post
title: Pointers in Flutter Radial Gauge widget | Syncfusion
description: Learn here all about adding and customizing Pointers of Syncfusion Flutter Radial Gauge (SfRadialGauge) widget and more.
platform: Flutter
control: SfRadialGauge
documentation: ug
---

# Pointers in Flutter Radial Gauge (SfRadialGauge)

 Pointer is used to indicate values on an axis. The radial gauge control has four types of pointers:

[`Marker pointer`](https://help.syncfusion.com/flutter/radial-gauge/marker-pointer)
[`Needle pointer`](https://help.syncfusion.com/flutter/radial-gauge/needle-pointer)
[`Range pointer`](https://help.syncfusion.com/flutter/radial-gauge/range-pointer)
[`Widget pointer`](https://help.syncfusion.com/flutter/radial-gauge/widget-pointer)

All the pointers can be customized as needed. You can add multiple pointers to the gauge to point multiple values on the same scale. The value of the pointer is set using the [`value`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugePointer/value.html) property.

![multiple pointers](images/pointers/pointers.png)

## Multiple pointers

In addition to the default pointer, you can add n number of pointers to an axis by adding in the [`pointers`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/pointers.html) property.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
              child: SfRadialGauge(
                axes: <RadialAxis>[RadialAxis(
                  pointers: <GaugePointer>[RangePointer(value: 30, ), 
                   MarkerPointer(value: 70),
                  NeedlePointer(value: 60)]
                )],
              )
            ),
          );
        }

{% endhighlight %}

![multiple pointers](images/pointers/multiple_pointer.jpg)

## Pointer Dragging

Pointers can be dragged over the scale value. It can be achieved by clicking and dragging the pointer. To enable or disable the pointer drag, use the [`enableDragging`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugePointer/enableDragging.html) property.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
              child: SfRadialGauge(
                axes: <RadialAxis>[RadialAxis( 
                 axisLineStyle: AxisLineStyle(thickness: 30, color: Colors.lightBlueAccent), 
                 showTicks: false,
                 pointers: <GaugePointer>[
                   MarkerPointer(value: 30, enableDragging: true, 
                   markerWidth: 30, markerHeight: 30, markerOffset: -15,
                   color: Colors.indigo)
                 ]
                )],
              )
            ),
          );
        }


{% endhighlight %}

![pointer dragging](images/pointers/pointer-interaction.gif)

## Event

[`onValueChangeStart`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugePointer/onValueChangeStart.html) - Occurs whenever the pointer starts to drag.

[`onValueChanging`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugePointer/onValueChanging.html) - Occurs before the current drag value gets updated as pointer value. The [`cancel`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/ValueChangingArgs/cancel.html) argument of [`ValueChangingArgs`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/ValueChangingArgs-class.html) allows to restrict the update of current drag value as pointer value.

[`onValueChanged`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugePointer/onValueChanged.html) - Occurs whenever the pointer value is changed while dragging.

[`onValueChangeEnd`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugePointer/onValueChangeEnd.html) - Occurs once the dragging of the pointer gets completed.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
              child: SfRadialGauge(
                axes: <RadialAxis>[RadialAxis(
                  pointers: <GaugePointer>[ RangePointer(value: 30, 
                  enableDragging: true,
                  onValueChanging: onValueChanging,
                  onValueChanged: onvalueChanged)]
                )],
              )
            ),
          );
        }

void onValueChanging(ValueChangingArgs args){
  if(args.value > 60){
      args.cancel = true;
  }
}

void onvalueChanged(double value){

}

{% endhighlight %}


