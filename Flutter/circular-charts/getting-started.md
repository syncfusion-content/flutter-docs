---
layout: post
title: Getting started with Flutter Circular Charts widget | Syncfusion
description: Learn here about getting started with Syncfusion Flutter Circular Charts (SfCircularChart) widget, its elements, and more.
platform: flutter
control: Chart
documentation: ug
---

#  Getting started with Flutter Circular Charts (SfCircularChart)

This section explains the steps required to populate the chart with data, title, data labels, legend, and tooltips. This section covers only the minimal features needed to know to get started with the chart.

To get start quickly with our Flutter chart widget, you can check on this video.

<style>#flutterChartVideoTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterChartVideoTutorial' src='https://www.youtube.com/embed/VJxPp7-2nGk'></iframe>

## Add Flutter Charts to an application

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter Chart dependency to your pub spec file.

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

Once the package has been imported, initialize the chart as a child of any widget. SfCircularChart can be used to render pie, doughnut and radial bar charts. Here, as we are rendering pie chart, initialize SfCircularChart widget as a child of Container widget.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    //Initialize chart
                    child: SfCircularChart()
                )
            )
        );
    }

{% endhighlight %}

> **NOTE**: An empty chart will be displayed. This is the charts default behavior.

## Bind data source

Based on your data, initialize the series type. In the series, you need to map the data source and the fields for x and y data points. Here, pie series is rendered that is demonstrated in the following code snippet.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData('David', 25),
            ChartData('Steve', 38),
            ChartData('Jack', 34),
            ChartData('Others', 52)
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                        // Render pie chart
                        PieSeries<ChartData, String>(
                            dataSource: chartData,
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y
                        )
                    ])
                )
            )
        );
    }

    class ChartData {
      ChartData(this.x, this.y, [this.color]);
        final String x;
        final double y;
        final Color? color;
    }

{% endhighlight %}

![Bind data source](images/getting-started/data_source.jpg)

## Add title

You can add a [`title`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/title.html) to the chart to provide quick information to users about the data plotted in the chart. The title to chart can be set as demonstrated in the following code snippet.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    width: 480,
                    height: 560,
                    child: SfCircularChart(
                        // Chart title text
                        title: ChartTitle(text: 'Half yearly sales analysis'),
                        series: <CircularSeries>[
                        // Render pie chart
                            PieSeries<ChartData, String>(
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

{% endhighlight %}

![Title to chart](images/getting-started/title_chart.jpg)

## Enable data labels

You can add data labels to improve the readability of the chart using the [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/dataLabelSettings.html) property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
        body: Center(
            child: Container(
                child: SfCircularChart(series: <CircularSeries>[
      // Initialize line series
      PieSeries<ChartData, String>(
          dataSource: [
            // Bind data source
            ChartData('Jan', 35),
            ChartData('Feb', 28),
            ChartData('Mar', 34),
            ChartData('Apr', 32),
            ChartData('May', 40)
          ],
          xValueMapper: (ChartData sales, _) => sales.x,
          yValueMapper: (ChartData sales, _) => sales.y,
          // Render the data label
          dataLabelSettings: DataLabelSettings(isVisible: true))
            ]))));
        }
    }

    class ChartData {
    ChartData(this.x, this.y, [this.color]);
    final String x;
    final double y;
    final Color? color;
    }

{% endhighlight %}

![DataLabel to chart](images/getting-started/datalabel.png)

## Enable legend

The legend provides information about the series rendered in the chart.

You can use legend in chart by setting the [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/Legend/isVisible.html) property to true in [`SfCircularChart.legend`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/Legend-class.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        // Enables the legend
                        legend: Legend(isVisible: true), 
                        series: <ChartSeries>[
                            // Initialize line series
                            PieSeries<SalesData, String>(
                                dataSource: [
                                    // Bind data source
                                    SalesData('Jan', 35),
                                    SalesData('Feb', 28),
                                    SalesData('Mar', 34),
                                    SalesData('Apr', 32),
                                    SalesData('May', 40)
                                ],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                name: 'Sales'
                            )
                        ]
                    )
                )      
            )
        );
    }

{% endhighlight %}

![Legend in chart](images/getting-started/legend.png)

## Enable tooltip

The tooltip is used when you cannot display information using the data labels due to space constraints.

The [`tooltipBehavior`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/tooltipBehavior.html) property in chart is used to enable and customize the tooltip for all the series whereas the [`enableTooltip`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/enableTooltip.html) property in series is used to toggle the tooltip visibility of each series. The tooltip can be enabled as demonstrated in the following code snippet.

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
                title: Text(widget.title),
            ),
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        // Enables the tooltip for all the series in chart
                        tooltipBehavior: _tooltipBehavior,
                        series: <CircularSeries>[
                            // Initialize line series
                            PieSeries<ChartData, String>(
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
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                                )
                            ]
                        )
                    )
                )
            );
        }
    }

    class ChartData {
    ChartData(this.x, this.y, [this.color]);
    final String x;
    final double y;
    final Color? color;
    }

{% endhighlight %}

![Tooltip in chart](images/getting-started/tooltip.png)

You can find the complete getting started example from this [`link`](https://www.syncfusion.com/downloads/support/directtrac/general/ze/circular_chart_example1927608018).