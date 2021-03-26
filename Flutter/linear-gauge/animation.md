---
layout: post
title: Animation in a linear gauge | Linear Gauge widget| Syncfusion
description: Tutorial about deatils of the annimation on Linear Gauge Flutter widget | Flutter Linear Gauge widget documentation|
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Flutter Linear Gauge Animation

All Linear Gauge elements such as `axis` along with `ticks` and `labels`, `range`, `bar pointer`, `shape marker pointer` and `widget marker pointer` can be animated separately. 

## Animate axis

The `animateAxis` and `animationDuration` properties in `SfLinearGauge` is used to  animate the axis track along with the ticks and labels. The axis will have a fade-in with opacity animation when this `animateAxis` is set to true. By default, the `animateAxis` is set to false. 

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

![Animate axis in linear gauge](images/animation/animation_axis_range/animation_axis.gif)

## Animate range

The `animateRange` and `animationDuration` properties in `SfLinearGauge` is used to  animate the axis track along with the ticks and labels. The range will be have a fade-in with opacity animation when this `animateRange` is set to true. By default, the `animateRange` is set to false. 

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

  ![Animate range in linear gauge](images/animation/animation_axis_range/animation_range.gif)

## Pointer animation

The animation behavior is common for all the pointers in Linear Gauge. There are three pointers - shape, widget and bar pointer. 

All the above three pointers have the below properties for animation. 

*  `enableAnimation` - Enable or disable the animation for bar pointer. The default value is `true`
*  `animationDuration` - Sets the animation duration. The default value is 1000
*  `animationType` - Sets the animation type. 

The `animationType` supports the below animations. The default animation type is `animationType.ease`.

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

### Animate Marker Pointers (Shape and Widget Pointers)

Both the shape and widget marker pointers will have the same set of properties and behave similarly for animation. So we have demonstrated the `LinearShapePointer` only but the same is applicable for `LinearWidgetPointer` too. 

### Marker pointer with `bounceOut` animation

![Animate marker pointer in linear gauge](images/animation/shape-pointer/bounceout.gif)





