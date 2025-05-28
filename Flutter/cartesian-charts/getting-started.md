---
layout: post
title: Getting started with Flutter Cartesian Charts widget | Syncfusion
description:  Learn here about getting started with Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget, its elements, and more.
platform: flutter
control: Chart
documentation: ug
---

# Getting started with Flutter Cartesian Charts (SfCartesianChart)

This section explains the steps required to populate the chart with data, title, data labels, legend, and tooltips. This section covers only the minimal features needed to know to get started with the chart.

To get start quickly with our Flutter chart widget, you can check out this video.

<style>#flutterChartVideoTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterChartVideoTutorial' src='https://www.youtube.com/embed/JAAnmOfoqg8'></iframe>

## Add Flutter Charts to an application

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive#choose-your-ide) documentation.

**Add dependency**

Add the Syncfusion<sup>&reg;</sup> Flutter Chart dependency to your pub spec file.

{% tabs %}
{% highlight dart %} 

    dependencies:

    syncfusion_flutter_charts: ^xx.x.xx

{% endhighlight %}
{% endtabs %}

>**Note**: Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter Charts`](https://pub.dev/packages/syncfusion_flutter_charts/versions) package.

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

    import 'package:syncfusion_flutter_charts/charts.dart';

{% endhighlight %}
{% endtabs %}

## Initialize chart

Once the package has been imported, initialize the chart as a child of any widget. SfCartesianChart is used to render all kinds of charts which need to be plotted in Cartesian coordinates. Here, as we are plotting line chart, initialize SfCartesianChart widget as a child of Container widget.

{% tabs %}
{% highlight dart hl_lines="2 7" %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    //Initialize chart
                    child: SfCartesianChart()
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Initialize Charts in Flutter.](images/getting-started/flutter-charts-initialize.jpg)

## Bind data source

Based on your data, initialize the appropriate axis type and series type. In the series, you need to map the data source and the fields for x and y data points. Here, line series is rendered with category axis that is demonstrated in the following code snippet.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        // Initialize category axis
                        primaryXAxis: CategoryAxis(),
                        series: <CartesianSeries>[
                            // Initialize line series
                            LineSeries<ChartData, String>(
                                dataSource: [
                                    // Bind data source
                                    ChartData('Jan', 35),
                                    ChartData('Feb', 28),
                                    ChartData('Mar', 34),
                                    ChartData('Apr', 32),
                                    ChartData('May', 40)
                                ],
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y
                            )
                        ]
                    )
                )
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.y);
        final String x;
        final double? y;
    }

{% endhighlight %}
{% endtabs %}

![Bind data source in Flutter Charts.](images/getting-started/flutter-charts-data-source.jpg)

#### See Also

* [Bind data from the list to the Flutter Cartesian chart](https://support.syncfusion.com/kb/article/10935/how-to-bind-data-from-the-list-to-the-flutter-cartesian-chart-sfcartesianchart).

* [Bind data from the array to the Flutter Cartesian chart](https://support.syncfusion.com/kb/article/10932/how-to-bind-data-from-the-array-to-the-flutter-cartesian-chart-sfcartesianchart).

To know more about how to create Flutter Charts from JSON data, you can watch this video.

<style>#flutterChartVideoTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterChartVideoTutorial' src='https://www.youtube.com/embed/eUyp_-MHLYg'></iframe>

## Add title

You can add a [`title`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/title.html) to the chart to provide quick information to users about the data plotted in the chart. The title to chart can be set as demonstrated in the following code snippet.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        // Chart title text
                        title: ChartTitle(text: 'Half yearly sales analysis'),
                        // Initialize category axis
                        primaryXAxis: CategoryAxis(),
                        series: <CartesianSeries>[
                            // Initialize line series
                            LineSeries<ChartData, String>(
                            dataSource: [
                                // Bind data source
                                ChartData('Jan', 35),
                                ChartData('Feb', 28),
                                ChartData('Mar', 34),
                                ChartData('Apr', 32),
                                ChartData('May', 40)
                            ],
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y)
                        ]
                    )
                )
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.y);
        final String x;
        final double? y;
    }

{% endhighlight %}
{% endtabs %}

![Title in Flutter Charts.](images/getting-started/flutter-charts-title.jpg)

## Enable data labels

You can add data labels to improve the readability of the chart using the [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings-class.html) property.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        title: ChartTitle(text: 'Half yearly sales analysis'),
                        // Initialize category axis
                        primaryXAxis: CategoryAxis(),
                        series: <CartesianSeries>[
                            // Initialize line series
                            LineSeries<ChartData, String>(
                                dataSource: [
                                    // Bind data source
                                    ChartData('Jan', 35),
                                    ChartData('Feb', 28),
                                    ChartData('Mar', 34),
                                    ChartData('Apr', 32),
                                    ChartData('May', 40)
                                ],
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                // Render the data label
                                dataLabelSettings:DataLabelSettings(isVisible : true)
                            )
                        ]
                    )
                )
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.y);
        final String x;
        final double? y;
    }

{% endhighlight %}
{% endtabs %}

![Data label in Flutter Charts.](images/getting-started/flutter-charts-data-label.jpg)

## Enable legend

The legend provides information about the series rendered in the chart.

You can use legend in chart by setting the [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/Legend/isVisible.html) property to true in [`legend`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/Legend-class.html).

Additionally, the [`series.name`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/name.html) property can be used to set the label for each series. The labels will be displayed in corresponding legends.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        // Enables the legend
                        legend: Legend(isVisible: true), 
                        // Initialize category axis
                        primaryXAxis: CategoryAxis(),
                        series: <CartesianSeries>[
                            // Initialize line series
                            LineSeries<ChartData, String>(
                                dataSource: [
                                    // Bind data source
                                    ChartData('Jan', 35),
                                    ChartData('Feb', 28),
                                    ChartData('Mar', 34),
                                    ChartData('Apr', 32),
                                    ChartData('May', 40)
                                ],
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                            )
                        ]
                    )
                )      
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.y);
        final String x;
        final double? y;
    }

{% endhighlight %}
{% endtabs %}

![Legend in Flutter Charts.](images/getting-started/flutter-charts-legend.png)

## Enable tooltip

The tooltip is used when you cannot display information using the data labels due to space constraints.

The [`tooltipBehavior`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/tooltipBehavior.html) property in chart is used to enable and customize the tooltip for all the series whereas the [`enableTooltip`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/enableTooltip.html) property in series is used to toggle the tooltip visibility of each series. The tooltip can be enabled, as demonstrated in the following code snippet.

{% tabs %}
{% highlight dart %} 

    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
      _tooltipBehavior =  TooltipBehavior(enable: true);
      super.initState(); 
    }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            appBar: AppBar(
                title: Text('afadff'),
            ),
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        // Enables the tooltip for all the series in chart
                        tooltipBehavior: _tooltipBehavior,
                        // Initialize category axis
                        primaryXAxis: CategoryAxis(),
                        series: <CartesianSeries>[
                            // Initialize line series
                            LineSeries<ChartData, String>(
                                // Enables the tooltip for individual series
                                enableTooltip: true, 
                                dataSource: [
                                    // Bind data source
                                    ChartData('Jan', 35),
                                    ChartData('Feb', 28),
                                    ChartData('Mar', 34),
                                    ChartData('Apr', 32),
                                    ChartData('May', 40)
                                ],
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y
                            )
                        ]
                    )
                )
            )
        );
    }

     class ChartData {
        ChartData(this.x, this.y);
        final String x;
        final double? y;
    }

{% endhighlight %}
{% endtabs %}

![Tooltip in Flutter Charts.](images/getting-started/flutter-charts-tooltip.png)

You can find the complete getting started example from this [`link`](https://support.syncfusion.com/kb/article/9941/how-to-integrate-syncfusion-charts-in-flutter-web-application-sfcartesianchart).

>**Note**: You can refer to our [`Flutter Charts`](https://www.syncfusion.com/flutter-widgets/flutter-charts) feature tour page for its groundbreaking feature representations. You can also explore our [`Flutter Charts example`](https://flutter.syncfusion.com/#/cartesian-charts/chart-types/line/default-line-chart) that shows how to render various chart types as well as how to easily configure with built-in support for creating stunning visual effects.

#### See Also

* [Integrate Syncfusion<sup>&reg;</sup> Flutter charts in Flutter web Application](https://support.syncfusion.com/kb/article/9941/how-to-integrate-syncfusion-charts-in-flutter-web-application-sfcartesianchart).
