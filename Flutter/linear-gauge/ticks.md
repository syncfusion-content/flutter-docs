---
layout: post
title: Customize ticks in a linear gauge | Linear Gauge widget| Syncfusion
description: Tutorial about the available styles of ticks on Linear Gauge Flutter widget.| Flutter Linear Gauge widget|
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Default Linear Gauge Ticks

The default style of axis ticks are as below.

![Initialize linear gauge for axis](images/getting-started/default_linear_gauge.png)

## Customize Linear Gauge Ticks

There are two type of ticks in the Flutter Linear Gauge namely major and minor ticks. In the above image, the comparatively larger ticks are major ticks and the ticks between the major ticks are minor ticks. The major and minor tick of a `SfLinearGauge` can be customized using the `majorTickStyle` and `minorTickStyle` properties. The following properties can be customized for both the major and the minor ticks:
* `color` – Allows to customize the tick color.
* `thickness` – Allows to customize the thickness of ticks.
* `length` – Specifics the length of ticks.

{% highlight dart %} 

@override
  Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
            body: Center(
              child: SfLinearGauge(
                  majorTickStyle: LinearTickStyle(length: 10, thickness: 2.5, color: Colors.black),
                  minorTickStyle: LinearTickStyle(length: 5, thickness: 1.75, color: Colors.black))
            )
        )
    );
  }

{% endhighlight %}

![Customize the linear gauge axis tick style](images/axis-ticks/axis-tick-style.png)

## Customize minor tick interval

The major ticks are generated based on the `interval` property which is documented in 'Customize the interval between labels' topic. The minor ticks are calculated using the `minorTicksPerInterval` property of `SfLinearGauge`. By default, the value of this property is 1.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(             
               child: SfLinearGauge(minorTicksPerInterval: 4)         
          )
      )
  );
}

{% endhighlight %}

![Customize linear gauge ticks per interval](images/axis-ticks/minor-ticks-per-interval.png)

## Change tick visibility

The `showTicks` property of the axis is used to enable or disable the visibility of both the major and the minor ticks. The default value of this property is true.

![Customize linear gauge ticks visibility](images/axis-ticks/linear-gauge-tick-visibility.png)

## Customize tick placement

The linear axis allows to position the ticks either inside or outside the axis track using the `ticksPosition` property. By default, ticks are positioned inside the axis track.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
                child: SfLinearGauge(
                    tickPosition: LinearElementPosition.outside,
                    labelPosition: LinearLabelPosition.outside
                ),
          )
      )
  );
}

{% endhighlight %}

![Customize linear gauge ticks placement](images/axis-ticks/tick-placement.png)


## Customize tick offset

The ticks can be moved near or far to the axis line using the `tickOffset` property. The default value of tick offset is 0. While setting offset for the ticks, the axis labels are also moved along with the ticks.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
                child: SfLinearGauge(tickOffset: 20),
          )
      )
    );
}

{% endhighlight %}

![Customize linear gauge ticks offset from axis](images/axis-ticks/customize-tick-offset.png)

