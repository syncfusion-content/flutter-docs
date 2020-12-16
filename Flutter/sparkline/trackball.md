---
layout: post
title: Syncfusion Flutter Sparkline Trackball 
description: Learn how to enable and customize the trackball available in the Syncfusion Flutter Sparkline widget.
platform: flutter
control: Sparkline
documentation: ug
---

# Syncfusion Flutter Sparkline Trackball 

## Trackball

Trackball feature displays the tooltip for the data points that are closer to the point where you touch on the chart area. This feature, especially, can be used instead of data label feature when you cannot show data labels for all data points due to space constraint. This feature can be enabled using enable property of [`trackball`](). Trackball will be activated using [`activationMode`]() property. Once it is activated, it will appear in the UI and move based on your touch movement until you stop touching on the chart.

You can use the following properties to customize the appearance:

* [`borderWidth`]() – Represent the border width.
* [`borderColor`]() – Represent the border color.
* [`backgroundColor`]() - Represent the background color for track ball.
* [`width`]() - Represent the width of track ball line.
* [`color`]() - Represent the color of track ball line.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child:  SfSparkLineChart(
                    trackball: SparkChartTrackball(activationMode: SparkChartActivationMode.tap),
                    data: <double>[
                        5,
                        6,
                        5,
                        7,
                        4,
                        3,
                        9,
                        5,
                        6,
                        5,
                        7,
                        8,
                        4,
                        5,
                        3,
                        4,
                        11,
                        10,
                        2,
                        12,
                        4,
                        7,
                        6,
                        8
                      ],
               )
             )
           );
         }

    class SalesData {
    SalesData(this.month, this.sales);
    final String month;
    final double sales;
    }

{% endhighlight %}

![Sparkline trackball](images/trackball/spark-trackball.png)

### Activation mode

The [`activationMode`]() property is used to restrict the visibility of trackball based on the touch actions. The default value of this property is [`ActivationMode.tap`]().

[`longPress`]() – Activates trackball only when performing the long press action.
[`tap`]() – Activates trackball only when performing tap action.
[`doubleTap`]() - Activates trackball only when performing double tap action.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child:  SfSparkAreaChart(
                    trackball: SparkChartTrackball(activationMode: SparkChartActivationMode.doubleTap),
                    data: <double>[
                        5,
                        6,
                        5,
                        7,
                        4,
                        3,
                        9,
                        5,
                        6,
                        5,
                        7,
                        8,
                        4,
                        5,
                        3,
                        4,
                        11,
                        10,
                        2,
                        12,
                        4,
                        7,
                        6,
                        8
                      ],
               )
             )
           );
         }

    class SalesData {
    SalesData(this.month, this.sales);
    final String month;
    final double sales;
    }

{% endhighlight %}

