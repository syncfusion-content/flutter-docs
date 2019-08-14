---
layout: post
title: Getting Started for Syncfusion Flutter Charts
description: Learn how to create the Flutter chart, add series, legend in Chart.
platform: flutter
control: Chart
documentation: ug
---

# Getting Started

This section explains you the steps required to populate the Chart with data, title, add data labels, legend and tooltips to the Chart. This section covers only the minimal features that you need to know to get started with the Chart.

## Adding flutter charts to your app

Create a simple project, using the instructions given in [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app).

**Add dependency**

Add the Syncfusion Flutter Chart dependency to your pub spec file.

{% highlight dart %} 

    dependencies:

    syncfusion_flutter_charts: ^1.0.0-beta.3

{% endhighlight %}

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

**Initialize chart**

Once the packages has been imported, initialize the chart as a child of any widget. Here, add the chart widget as a child of the container widget.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart() //Initialize chart
                )
            )
        );
    }

{% endhighlight %}

![Initialize chart](images/getting-started/default.jpg)

## Bind data source

Based on your data, initialize the appropriate axis type and series type. In the series, you need to map the data source and the fields for x and y data points. We have rendered line series with category axis that we have depicted with the below code snippet. 

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(), // Initialize category axis.
                        series: <ChartSeries>[
                            // Initialize line series.
                            LineSeries<SalesData, String>(
                                dataSource: [
                                    // Bind data source.
                                    SalesData('Jan', 35),
                                    SalesData('Feb', 28),
                                    SalesData('Mar', 34),
                                    SalesData('Apr', 32),
                                    SalesData('May', 40)
                                ],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

    class SalesData{
        SalesData(this.year, this.sales);
        final String year;
        final double sales;
    }

{% endhighlight %}

![Bind data source](images/getting-started/data_source.jpg)

## Add title

You can add a [`title`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/title.html) to the chart to provide quick information to the user about the data plotted in the chart. The title in chart can be set as below.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        title: ChartTitle(text: 'Half yearly sales analysis'),
                        primaryXAxis: CategoryAxis(), // Initialize category axis.
                        series: <ChartSeries>[
                            // Initialize line series.
                            LineSeries<SalesData, String>(
                            dataSource: [
                                // Bind data source.
                                SalesData('Jan', 35),
                                SalesData('Feb', 28),
                                SalesData('Mar', 34),
                                SalesData('Apr', 32),
                                SalesData('May', 40)
                            ],
                            xValueMapper: (SalesData sales, _) => sales.year,
                            yValueMapper: (SalesData sales, _) => sales.sales)
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Title to chart](images/getting-started/title_chart.jpg)

## Enable data labels

You can add data labels to improve the readability of the chart. This can be achieved using [`SfCartesianChart.dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dataLabelSettings.html) property as shown below.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        title: ChartTitle(text: 'Half yearly sales analysis'),
                        primaryXAxis: CategoryAxis(), // Initialize category axis.
                        series: <ChartSeries>[
                            // Initialize line series.
                            LineSeries<SalesData, String>(
                                dataSource: [
                                    // Bind data source.
                                    SalesData('Jan', 35),
                                    SalesData('Feb', 28),
                                    SalesData('Mar', 34),
                                    SalesData('Apr', 32),
                                    SalesData('May', 40)
                                ],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                dataLabelSettings:DataLabelSettings(isVisible : true)
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![DataLabel to chart](images/getting-started/datalabel.jpg)

## Enable legend

Legend provides information about the series rendered in the chart.

You can use legend for the chart by setting the [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/Legend/isVisible.html) property to true in [`SfCartesianChart.legend`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/Legend-class.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        legend: Legend(isVisible: true), 
                        primaryXAxis: CategoryAxis(), // Initialize category axis.
                        series: <ChartSeries>[
                            // Initialize line series.
                            LineSeries<SalesData, String>(
                                dataSource: [
                                    // Bind data source.
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

Additionally, you need to set label for each series using [`series.name`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/name.html) property, which will be displayed in corresponding legend.


![Legend in chart](images/getting-started/legend.jpg)

## Enable tooltip

The tooltip is useful when you cannot display information by using the data labels due to space constraints. The tooltip can be enabled as depicted below.

The [`tooltipBehavior`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/tooltipBehavior.html) property in chart is used to enable and customize the tooltip for all the series whereas the [`enableTooltip`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/enableTooltip.html) property in series used to toggle the tooltip visibility of each series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            appBar: AppBar(
                title: Text(widget.title),
            ),
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        tooltipBehavior: TooltipBehavior(enable: true),//Used to customize the tooltip for all the series
                        primaryXAxis: CategoryAxis(), // Initialize category axis.
                        series: <ChartSeries>[
                            // Initialize line series.
                            LineSeries<SalesData, String>(
                                enableTooltip: true, //Enables the tooltip for individual series. 
                                dataSource: [
                                    // Bind data source.
                                    SalesData('Jan', 35),
                                    SalesData('Feb', 28),
                                    SalesData('Mar', 34),
                                    SalesData('Apr', 32),
                                    SalesData('May', 40)
                                ],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Tooltip in chart](images/getting-started/tooltip.jpg)