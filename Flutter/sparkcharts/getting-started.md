---
layout: post
title: Getting started with Flutter Spark Charts | Sparkline | Syncfusion
description: Learn here about getting started with Syncfusion Flutter Spark Charts widget (Sparkline), its elements, and more.
platform: flutter
control: Sparkline
documentation: ug
---

# Getting started with Flutter Spark Charts

This section explains the steps required to populate the spark charts with data, data labels, marker and trackball. This section covers only the minimal features needed to know to get started with the spark charts.

## Add Flutter Spark charts to an application

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive#choose-your-ide) documentation.

**Add dependency**

Add the Syncfusion<sup>&reg;</sup> Flutter Chart dependency to your pub spec file.

{% tabs %}
{% highlight dart %} 

    dependencies:

    syncfusion_flutter_charts: ^xx.x.xx

{% endhighlight %}
{% endtabs %}

> **NOTE** 
Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter Charts`](https://pub.dev/packages/syncfusion_flutter_charts/versions) package.

**Get packages**

Run the following command to get the required packages.

{% tabs %}
{% highlight dart %} 

    $ flutter pub get

{% endhighlight %}
{% endtabs %}

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight dart %} 

    import 'package:syncfusion_flutter_charts/sparkcharts.dart';

{% endhighlight %}
{% endtabs %}

## Initialize spark charts

Once the package has been imported, initialize the spark charts as a child of any widget. Here, as we are rendering Line chart, initialize [`SfSparkLineChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart-class.html) widget as a child of Container widget.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    //Initialize the spark charts
                    child: SfSparkLineChart()
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

## Bind data source

The `data` property is used for binding data to the spark charts. This property takes the list value as input. 

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    //Initialize the spark line chart
                    child: SfSparkLineChart(
                         data: <double>[
                             10,6, 8, -5, 11, 5, -2, 7, -3, 6, 8, 10
                         ]
                    )
                ),
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![bind datasource](images/getting-started/bind-data.png)

## Spark charts types

You can initialize the required spark charts type by specifying the widget name to 
[`SfSparkLineChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart-class.html)
, [`SfSparkAreaChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart-class.html)
, [`SfSparkBarChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart-class.html)
, [`SfSparkLWinLossChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart-class.html). 
Here, the spark chart type has been set to 
[`SfSparkAreaChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart-class.html).

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    //Initialize the spark area chart
                    child: SfSparkAreaChart(
                        axisLineWidth:0,
                         data: <double>[
                             10,6, 8, -5, 11, 5, -2, 7, -3, 6, 8, 10
                        ]
                    )
                ),
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![chart type](images/getting-started/sparkline-type.png)

## Enable data label

You can add data labels to improve the readability of the chart using the [`labelDisplayMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/labelDisplayMode.html) property.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    //Initialize spark line chart
                    child: SfSparkLineChart(
                        //Enable data label
                        labelDisplayMode: SparkChartLabelDisplayMode.all,
                        data: <double>[
                            10,6, 8, -5, 11, 5, -2, 7, -3, 6, 8, 10
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![datalabel](images/getting-started/sparkline-datalabel.png)

## Enable trackball for spark chart

The spark charts displays additional information through trackball when touched on a specific location of the chart area. You can enable trackball by setting the [`trackball`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/trackball.html) property in [`SparkChartTrackball`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartTrackball-class.html). Once it is activated, it will appear in the UI and move based on your touch movement until you stop touching on the chart.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfSparkLineChart(
                        //Enable the trackball
                        trackball: SparkChartTrackball(
                            activationMode: SparkChartActivationMode.tap
                        ),
                        data: <double>[
                            10,6, 8, -5, 11, 5, -2, 7, -3, 6, 8, 10
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![trackball](images/getting-started/sparkline-trackball.png)