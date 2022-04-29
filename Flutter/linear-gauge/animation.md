---
layout: post
title: Animation in Flutter Linear Gauge widget | Syncfusion
description: Learn here all about adding and customizing animation of Syncfusion Flutter Linear Gauge (SfLinearGauge) widget and more.
platform: Flutter
control: SfLinearGauge
documentation: ug
---

# Animation in Flutter Linear Gauge (SfLinearGauge)

All Linear Gauge elements such as axis along with ticks and labels, range, bar pointer, shape marker pointer and widget marker pointer can be animated separately. 

## Animate axis

The [`animateAxis`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/animateAxis.html) and [`animationDuration`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/animationDuration.html) properties in [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html) is used to  animate the axis track along with the ticks and labels. The axis will have a fade-in with opacity animation when this [`animateAxis`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/animateAxis.html) is set to true. By default, the [`animateAxis`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/animateAxis.html) is set to false. 

{% highlight dart %}

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            animateAxis: true,
            animationDuration: 3000
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![Animate axis in linear gauge](images/animation/animation-axis-range/animation-axis.gif)

## Animate range

The [`animateRange`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/animateRange.html) and [`animationDuration`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/animationDuration.html) properties in [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html) is used to  animate the axis track along with the ticks and labels. The range will be have a fade-in with opacity animation when this [`animateRange`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/animateRange.html) is set to true. By default, the [`animateRange`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/animateRange.html) is set to false. 

{% highlight dart %}

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            animateRange: true,
            animationDuration: 3000
          ),
        ),
      ),
    );
  }

  {% endhighlight %}

  ![Animate range in linear gauge](images/animation/animation-axis-range/animation-range.gif)

## Pointer animation

The animation behavior is common for all the three pointers in Linear Gauge - shape, widget and bar pointer. 

All the above three pointers have the below properties for animation. 

*  [`enableAnimation`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/enableAnimation.html) - Enable or disable the animation for bar pointer. The default value is `true`
*  [`animationDuration`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/animationDuration.html) - Sets the animation duration. The default value is 1000
*  [`animationType`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/animationType.html) - Sets the animation type. 

The [`animationType`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/animationType.html) supports the below animations. The default animation type is `animationType.ease`.

* `bounceOut`
* `ease`
* `easeInCir`
* `easeOutBack`
* `elasticOut`
* `linear`
* `slowMiddle`

### Animate bar pointer

The below code example demonstrates updating the animation for bar pointer.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            barPointers: [
              LinearBarPointer(
                value: 50,
                animationDuration: 2000,
                animationType: LinearAnimationType.bounceOut
              ),
            ],
          ),
        ),
      ),
    );
  }

{% endhighlight %}

### Animate marker pointers (Shape and Widget Pointers)

Both the shape and widget marker pointers will have the same set of properties and behave similarly for animation. So we have demonstrated the [`LinearShapePointer`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer-class.html) only but the same is applicable for [`LinearWidgetPointer`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearWidgetPointer-class.html) too. 

### Marker pointer with `bounceOut` animation

![Animate marker pointer in linear gauge](images/animation/shape-pointer/bounceout.gif)





