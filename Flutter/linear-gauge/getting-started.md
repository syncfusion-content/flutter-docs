---
layout: post
title: Getting started with Flutter Linear Gauge widget | Syncfusion
description: Learn here about getting started with Syncfusion Flutter Linear Gauge (SfLinearGauge) widget, its elements, and more. 
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Getting started with Flutter Linear Gauge (SfLinearGauge)

This section explains the steps required to add the Linear Gauge and its elements such as axis, range, and pointer and also covers basic features needed to know to get started with the Linear Gauge widget.

To get start quickly with our Flutter Linear Gauge widget, you can check on this video.

<style>#FlutterLinearGaugeVideoTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='FlutterLinearGaugeVideoTutorial' src='https://www.youtube.com/embed/8NmzRA-kM5Y'></iframe>

## Add Linear Gauge to an application

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion<sup>&reg;</sup> Flutter Gauge dependency to your pubspec.yaml file.

{% highlight dart %} 

    dependencies:

    syncfusion_flutter_gauges: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of the [`Syncfusion Flutter Gauge`](https://pub.dev/packages/syncfusion_flutter_gauges/versions) package.

**Get packages**

Run the following command to get the required packages.

{% highlight dart %} 

    $ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% highlight dart %} 

    import 'package:syncfusion_flutter_gauges/gauges.dart';

{% endhighlight %}

## Initialize the Linear Gauge

After the package has been imported, initialize the [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/SfLinearGauge.html) as a child of any widget such as container widget.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
                body: Center(
                        child:SfLinearGauge()
                )
              )      
            );
        }

{% endhighlight %}

![Initialize linear gauge](images/getting-started/default_linear_gauge.png)

## Add axis

The Linear Gauge axis is a scale where a set of values can be plotted. You can specify the minimum and maximum values of the axis using the [`minimum`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/minimum.html) and [`maximum`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/maximum.html) properties as demonstrated in the following code sample.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
                body: Center(
                   child: SfLinearGauge(minimum: 100, maximum: 200)
                )
            )      
        );
    }

{% endhighlight %}

![Add axis to linear gauge](images/getting-started/add_axis.png)

## Update orientation

As you can see in the above image, the default orientation of the Linear Gauge is horizontal. But you can change it with the [`orientation`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/orientation.html) property of the Linear Gauge widget.

{% highlight dart %} 

SfLinearGauge(
              orientation: LinearGaugeOrientation.vertical
            ),

{% endhighlight %}

![Update Orientation of linear gauge](images/getting-started/vertical_orientation.png)

## Add range

A range is a visual element that helps you to quickly visualize where a range falls on the axis track. Multiple ranges with different styles can be added to a Linear gauge. You can also specify the start value, end value, and color for a range as demonstrated in the following code sample.  

{% highlight dart %} 

    SfLinearGauge(
        ranges: <LinearGaugeRange>[
        //First range
        LinearGaugeRange(startValue: 0, endValue: 50, color: Colors.green),
        //Second range
        LinearGaugeRange(startValue: 50, endValue: 100, color: Colors.blue)
      ]
    )

{% endhighlight %}

![Add ranges to a linear gauge](images/getting-started/add_ranges.png)

## Add marker pointer

The Linear Gauge supports two marker pointers - shape pointer and widget pointer. The shape pointer will have a default set of pre-build icons to point a value in an axis track, while the widget pointer facilitates using any Flutter widget to point a value in an axis track. 

The following code sample demonstrates how to add a shape pointer.

{% highlight dart %} 

    SfLinearGauge(
        markerPointers: [LinearShapePointer(value: 50)]
      ),

{% endhighlight %}

![Add shape pointer in linear gauge](images/getting-started/add_shape_pointer.png)

The following code sample demonstrates how to add a widget pointer.

{% highlight dart %} 

    SfLinearGauge(
        markerPointers: [
          LinearWidgetPointer(
            value: 40,
              child: Container(
              height: 20,
              width: 20,
              decoration: BoxDecoration(color: Colors.blueAccent)
            ), 
          ),
        ],
      ),

{% endhighlight %}

![Add widget pointer in linear gauge](images/getting-started/add_widget_pointer.png)

## Add bar pointer

In a Linear Gauge, the bar pointer is used to specify a value in an axis track by drawing a track from the axis’s minimum value to its specified value

{% highlight dart %} 

    SfLinearGauge(
        barPointers: [LinearBarPointer(value: 40)]
      ),

{% endhighlight %}

![Bar pointer added to a linear gauge](images/getting-started/add_bar_pointer.png)

The following code example gives you the complete view of the above configurations.

{% highlight dart %} 

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_gauges/gauges.dart';

   void main() => runApp(ChartApp());
    class LinearGaugeDemo extends StatelessWidget {

    @override
  Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
            body: Center(
              child: SfLinearGauge(
                ranges: <LinearGaugeRange>[ 
                  //First range
                 LinearGaugeRange(
                   startValue: 0,
                   endValue: 50,
                   color: Colors.green
                 ),
                 //Second range
                 LinearGaugeRange(
                   startValue: 50,
                   endValue: 100,
                   color: Colors.blue
                 ),
                ],
                markerPointers: [
                  LinearShapePointer(value: 50),
                  LinearWidgetPointer(
                    value: 40,
                    child: Container(
                      height: 20,
                      width: 20,
                      decoration: BoxDecoration(color: Colors.blueAccent)
                    ),
                  ),
                ],
                barPointers: [LinearBarPointer(value: 40)]
              ),
            )
        )
    );
  }
}

{% endhighlight %}

![A Linear gauge](images/getting-started/all_basic_elements.png)