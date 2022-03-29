---
layout: post
title: Multiple Charts in Flutter Cartesian Charts | Syncfusion 
description: Learn here all about Combinational Charts of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Multiple Charts in Flutter Cartesian Charts (SfCartesianChart)


## Multiple series

You can add multiple series to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) property of the [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html) class. By default, all the series are rendered based on the [`PrimaryXAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/primaryXAxis.html) and [`PrimaryYAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/primaryYAxis.html) in [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). If you want to plot different unit or value that is specific to a particular series, specify separate axis for that series using the [`xAxisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/xAxisName.html) and [`yAxisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/yAxisName.html) properties of series.

{% tabs %}
{% highlight Dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = <ChartData>[
           ChartData('Germany', 128, 129, 101),
           ChartData('Russia', 123, 92, 93),
           ChartData('Norway', 107, 106, 90),
           ChartData('USA', 87, 95, 71),
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <CartesianSeries>[
                            ColumnSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y
                            ),
                            ColumnSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y1
                            ),
                            ColumnSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y2
                            )
                        ]
                    )
                )
            )
        );
    }

     class ChartData {
        ChartData(this.x, this.y, this.y1, this.y2);
        final String x;
        final double? y;
        final double? y1;
        final double? y2;
      }

{% endhighlight %}
{% endtabs %}

![Multiple series](images/cartesian-customization/multipleSeriess.jpg)

Also refer [multiple axes](./axis-customization#multiple-axes) for customizing the axis further.

## Combination series

[`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html) allows you to render a combination of different types of series. The column and line type series have been combined in the following code snippet.

{% tabs %}
{% highlight Dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = <ChartData>[
            ChartData('Germany', 129),
            ChartData('Russia', 90),
            ChartData('USA', 107),
            ChartData('Norway', 68),
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <CartesianSeries>[
                            // Render column series
                            ColumnSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y
                            ),
                            // Render line series
                            LineSeries<ChartData, String>(
                                dataSource: chartData,
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

![Combination series](images/cartesian-customization/combinationseries.jpg)

**Limitation of combination chart**

* Cartesian type series cannot be combined with circular series (pie, doughnut, and radial bar).  

>**Note**:
* `chartData` in the above code snippets is a class type list and holds the data for binding to the chart series. Refer [Bind data source](https://help.syncfusion.com/flutter/cartesian-charts/getting-started#bind-data-source) topic for more details.
* You can refer to our [Flutter Combination Chart](https://www.syncfusion.com/flutter-widgets/flutter-charts/chart-types/combination-chart) feature tour page for its groundbreaking feature representations.