---
layout: post
title: Animation in Flutter Radial Gauge widget | Syncfusion
description: Learn here all about adding and customizing animation of Syncfusion Flutter Radial Gauge (SfRadialGauge) widget and more.
platform: Flutter
control: SfRadialGauge
documentation: ug
---

# Animation in Flutter Radial Gauge (SfRadialGauge)

## Initial animation

The radial gauge allows all of its elements to be animated with [`enableLoadingAnimation`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge/enableLoadingAnimation.html) property. The default value for this property is false. The duration of the animation can be controlled by [`animationDuration`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge/animationDuration.html) property of the gauge.

{% highlight dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: SfRadialGauge(
          enableLoadingAnimation: true, 
          animationDuration: 4500,
          axes: <RadialAxis>[
            RadialAxis(
              minimum: 0,
              maximum: 150,
              ranges: <GaugeRange>[
                GaugeRange(startValue: 0, endValue: 50, color: Colors.green, startWidth: 10, endWidth: 10),
                GaugeRange(startValue: 50, endValue: 100, color: Colors.orange, startWidth: 10, endWidth: 10),
                GaugeRange(startValue: 100, endValue: 150, color: Colors.red, startWidth: 10, endWidth: 10)
              ],
              pointers: <GaugePointer>[
                NeedlePointer(value: 90)
              ],
              annotations: <GaugeAnnotation>[
                GaugeAnnotation(
                  widget: Container(
                    child: Text('90.0', style: TextStyle(fontSize: 25, fontWeight: FontWeight.bold))
                  ),
                  angle: 90,
                  positionFactor: 0.5
                )
              ]
            )
          ]
        ),
      ),
    );
  }

{% endhighlight %}

![gauge loading animation](images/animation/initial_Animation.gif)

## Pointer Animation

The [`enableAnimation`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugePointer/enableAnimation.html) property of pointer allows you to enable or disable animation for pointers. The gauge pointer supports the following animation types:

* `bounceOut`
* `ease`
* `easeInCir`
* `easeOutBack`
* `elasticOut`
* `linear`
* `slowMiddle`

The animation type can be changed using the [`animationType`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugePointer/animationType.html) property of pointer. By default, the animation type is linear.

{% highlight dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: SfRadialGauge(
          axes: <RadialAxis>[
            RadialAxis(
              axisLineStyle: AxisLineStyle(thickness: 30), 
              showTicks: false,
              pointers: <GaugePointer>[
                NeedlePointer(
                  value: 60, 
                  enableAnimation: true,
                  needleStartWidth: 0,
                  needleEndWidth: 5, 
                  needleColor: Color(0xFFDADADA),
                  knobStyle: KnobStyle(
                    color: Colors.white, 
                    borderColor: Color(0xFFDADADA),
                    knobRadius: 0.06,
                    borderWidth: 0.04
                  ),
                  tailStyle: TailStyle(
                    color: Color(0xFFDADADA), 
                    width: 5,
                    length: 0.15
                  )
                ),
                RangePointer(
                  value: 60, 
                  width: 30, 
                  enableAnimation: true, 
                  color: Colors.orange
                )
              ]
            )
          ],
        )
      ),
    );
  }

{% endhighlight %}

![pointer animation](images/animation/animation.gif)
