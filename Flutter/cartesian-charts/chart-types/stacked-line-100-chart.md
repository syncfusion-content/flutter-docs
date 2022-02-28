---
layout: post
title: 100% Stacked line in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about 100% stacked line chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# 100% Stacked line Chart in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter 100% stacked line chart quickly, you can check this video.

<style>#flutter100stackedlineChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutter100stackedlineChartTutorial' src='https://www.youtube.com/embed/NCUDBD_ClHo'></iframe>

To render a 100% stacked line chart, create an instance of [`StackedLine100Series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedLine100Series-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties can be used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) - changes the stroke width of the line.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            StackedLine100Series<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales
                            ),
                            StackedLine100Series<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales2
                            ),
                            StackedLine100Series<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales3
                            ),
                            StackedLine100Series<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales4
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Stacked 100 line chart](cartesian-chart-types-images/stacked_line_100.png)

## Dashed line

The `dashArray` property of `StackedLine100Series` is used to render line series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            StackedLine100Series<ChartData, String>(
                                dataSource: chartData,
                                dashArray: <double>[5,5],
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales
                            ),
                            StackedLine100Series<ChartData, String>(
                                dataSource: chartData,
                                dashArray: <double>[5,5],
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales2
                            ),
                            StackedLine100Series<ChartData, String>(
                                dataSource: chartData,
                                dashArray: <double>[5,5],
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales3
                            ),
                            StackedLine100Series<ChartData, String>(
                                dataSource: chartData,
                                dashArray: <double>[5,5],
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales4
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Dashed line chart](cartesian-chart-types-images/stacked_line_100_dashes.png)

#### See Also

* [Color palette](./series-customization#color-palette) 
* [Color mapping](./series-customization#color-mapping-for-data-points)
* [Animation](./series-customization#animation)
* [Empty points](./series-customization#empty-points)  
* [Sorting](./series-customization##sorting) 