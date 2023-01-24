---
layout: post
title: Getting started with Flutter Radial Gauge widget | Syncfusion
description: Learn here about getting started with Syncfusion Flutter Radial Gauge (SfRadialGauge) control, its elements, and more. 
platform: Flutter
control: SfRadialGauge
documentation: ug
---

# Getting started with Flutter Radial Gauge (SfRadialGauge)

This section explains the steps required to add the Flutter [Radial Gauge](https://www.syncfusion.com/flutter-widgets/flutter-radial-gauge) and its elements such as title, axis, range, pointer and annotation. This section covers only basic features needed to know to get started with Syncfusion radial gauge. 

To get start quickly with our Flutter radial gauge widget, you can check on this video.

<style>#flutterRadialGaugeVideoTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterRadialGaugeVideoTutorial' src='https://www.youtube.com/embed/2NuipO7j2tA'></iframe>

## Add Flutter Radial Gauge to an application

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter Gauge dependency to your pubspec.yaml file.

{% highlight dart %} 

    dependencies:

    syncfusion_flutter_gauges: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter Gauge`](https://pub.dev/packages/syncfusion_flutter_gauges/versions) package.

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

## Initialize the radial gauge

After the package has been imported, initialize the [SfRadialGauge](https://www.syncfusion.com/flutter-widgets/flutter-radial-gauge) as a child of any widget such as container widget.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
                body: Center(
                    child: Container(
                        child:SfRadialGauge()
                        )
                    )
                )      
            );
        }

{% endhighlight %}

![Initialize radial gauge](images/getting-started/default_gauge.png)

## Add title

You can add a title to the radial gauge to provide information to users about the designed gauge. The title can be set to gauge as demonstrated in following code snippet. 

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
                body: Center(
                    child: Container(
                        child: SfRadialGauge(
                            title:GaugeTitle(text: 'Speedometer', textStyle: TextStyle(
                            fontSize: 20.0,fontWeight: FontWeight.bold))
                        )
                    )
                )
            )      
        );
    }

{% endhighlight %}

![title to radial gauge](images/getting-started/gauge_title.png)

## Add axis

Axes contain a list of axis elements, where you can add any number of radial axes inside the gauge. You can specify the minimum and maximum values of axis using the [`minimum`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/minimum.html) and [`maximum`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/maximum.html) properties as demonstrated in the following code snippet.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
                body: Center(
                    child: Container(
                    child: SfRadialGauge(
                        axes: <RadialAxis>[
                            RadialAxis(minimum: 0, maximum: 150)]
                        )
                    )
                )
            )      
        );
    }

{% endhighlight %}

![Axis to radial gauge](images/getting-started/gauge_axis.png)

## Add range

Ranges contain a list of range elements, where you can add any number of ranges inside the axis. You can specify the start value, end value, and color for range using the [`startValue`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/startValue.html), [`endValue`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/endValue.html), and [`color`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/color.html) properties as demonstrated in the following code.   

{% highlight dart %} 

    axes: <RadialAxis>[
        RadialAxis(minimum: 0,maximum: 150,
                ranges: <GaugeRange>[
                    GaugeRange(startValue: 0,endValue: 50,color: Colors.green,startWidth: 10,endWidth:10),
                    GaugeRange(startValue: 50,endValue: 100,color: Colors.orange,startWidth: 10,endWidth: 10),
                    GaugeRange(startValue: 100,endValue: 150,color: Colors.red,startWidth: 10,endWidth: 10)]
                )]

{% endhighlight %}

![range support to radial gauge](images/getting-started/gauge_range.png)

## Add pointer

Pointers contains a list of pointer elements, where you can add any number of gauge pointers such as [`needlePointer`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/NeedlePointer-class.html), [`rangePointer`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RangePointer-class.html), [`markerPointer`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer-class.html), and [`widgetPointer`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/WidgetPointer-class.html) inside the axis to indicate the value.

{% highlight dart %} 

    axes: <RadialAxis>[
        RadialAxis(minimum: 0,maximum: 150,
        pointers: <GaugePointer>[NeedlePointer(value:90)]
        )]

{% endhighlight %}

![gauge pointers to radial gauge](images/getting-started/gauge_pointer.png)

## Add annotation

You can add any number of widgets such as text or image as an annotation inside the axis. The position of annotation can be customized using the [`angle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAnnotation/angle.html) and [`positionFactor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAnnotation/positionFactor.html) properties as demonstrated in the following code.

{% highlight dart %} 

    axes: <RadialAxis>[
        RadialAxis(minimum: 0,maximum: 150,
        annotations: <GaugeAnnotation>[
            GaugeAnnotation(widget: Container(child:
            Text('90.0',style: TextStyle(fontSize: 25,fontWeight: FontWeight.bold))),
            angle: 90,positionFactor: 0.5)]
            )]

{% endhighlight %}

![annotation support to the radial gauge](images/getting-started/gauge_annotation.png)

The following code example gives you the complete code of above configurations.

{% highlight dart %} 

    import 'package:flutter/material.dart';
    import 'package:syncfusion_flutter_gauges/gauges.dart';

    void main() => runApp(ChartApp());

    class ChartApp extends StatelessWidget {

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
                body: Center(
                    child: Container(
                        child: SfRadialGauge(
                            axes: <RadialAxis>[
                                RadialAxis(minimum: 0,maximum: 150,
                                ranges: <GaugeRange>[
                                    GaugeRange(startValue: 0,endValue: 50,color: Colors.green,startWidth: 10,endWidth: 10),
                                    GaugeRange(startValue: 50,endValue: 100,color: Colors.orange,startWidth: 10,endWidth: 10),
                                    GaugeRange(startValue: 100,endValue: 150,color: Colors.red,startWidth: 10,endWidth: 10)],
                                    pointers: <GaugePointer>[NeedlePointer(value:90)],
                                    annotations: <GaugeAnnotation>[
                                        GaugeAnnotation(widget: Container(child:
                                        Text('90.0',style: TextStyle(fontSize: 25,fontWeight:FontWeight.bold))),
                                        angle: 90,positionFactor: 0.5)]
                                )]
                            )
                        )
                    )
                )
            );
        }
    }

{% endhighlight %}