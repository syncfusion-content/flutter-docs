---
layout: post
title: Getting started for Syncfusion Flutter Sparkline(SFSparkline)
description:  Learn how to create the syncfusion Flutter sparkline, add series, markers, trackball and other features in Sparkline.
platform: flutter
control: Sparkline
documentation: ug
---

# Getting Started with Flutter Flutter Sparkline(SFSparkline)

This section explains the steps required to populate the sparkline with data, title, data labels, marker and trackball. This section covers only the minimal features needed to know to get started with the sparkline.

## Add Flutter Sparkline Chart to an application

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter Sparkline Chart dependency to your pub spec file.

{% highlight dart %} 

    dependencies:

    syncfusion_flutter_charts: ^xx.x.xx

{% endhighlight %}

> **NOTE** 
Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter Charts`](https://pub.dev/packages/syncfusion_flutter_charts/versions) package.

**Get packages**

Run the following command to get the required packages.

{% highlight dart %} 

    $ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% highlight dart %} 

    import 'package:syncfusion_flutter_charts/charts.dart';

{% endhighlight %}

## Initialize chart 

Once the package has been imported, initialize the sparkline chart as a child of any widget. Here, as we are rendering Line chart, initialize [`SfSparkLineChart`]() widget as a child of Container widget.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    //Initialize chart
                    child: SfSparkLineChart()
                )
            )
        );
    }

{% endhighlight %}

## Bind data source of sparkline

The [`data`]() property is used for binding data to the sparkline. This property takes the list value as input. 

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    //Initialize chart
                    child: SfSparkLineChart(
                         data: <double>[     10,6, 8, -5, 11, 5, -2, 7, -3, 6, 8, 10,  )),
                )
            )
        );
    }

{% endhighlight %}

## Change the type of sparkline

You can change the sparkline type by setting the widget to [`SfSparkLineChart`](), [`SfSparkAreaChart`](), [`SfSparkBarChart`](), [`SfSparkLWinLossChart`](). Here, the sparkline type has been set to [`SfSparkAreaChart`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    //Initialize chart
                    child: SfSparkAreaChart(
                         data: <double>[     10,6, 8, -5, 11, 5, -2, 7, -3, 6, 8, 10,  )),
                )
            )
        );
    }

{% endhighlight %}

## Enable trackball for sparkline

The sparkline displays additional information through trackball when touch the particular location to the sparkline. You can enable trackball by setting the [`trackball`]() property in [`SparkChartTrackball`](). Once it is activated, it will appear in the UI and move based on your touch movement until you stop touching on the chart.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    //Initialize chart
                    child: SfSparkAreaChart(
                         trackball: SparkChartTrackball(activationMode: SparkChartActivationMode.tap,
                         data: <double>[     10,6, 8, -5, 11, 5, -2, 7, -3, 6, 8, 10,  )),
                )
            )
        );
    }

{% endhighlight %}






