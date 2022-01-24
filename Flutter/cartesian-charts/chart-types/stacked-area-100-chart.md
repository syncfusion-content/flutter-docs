---
layout: post
title: 100% Stacked area in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about 100% stacked area chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---


# 100% Stacked area Chart in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter 100% stacked area chart quickly, you can check this video.

<style>#flutter100stackedareaChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutter100stackedareaChartTutorial' src='https://www.youtube.com/embed/NCUDBD_ClHo'></iframe>

To render a 100% stacked area chart, create an instance of `StackingArea100Series` and add to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). You can use the following properties to customize the 100% stacked area appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.
* `borderDrawMode` - specifies the type of the border mode and it defaults to `top`.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <ChartSeries>[
                            StackedArea100Series<ChartData, DateTime>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales1
                            ),
                            StackedArea100Series<ChartData, DateTime>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales2
                            ),
                            StackedArea100Series<ChartData, DateTime>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales3
                            ),
                            StackedArea100Series<ChartData, DateTime>(
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

![Stacked 100Area chart](cartesian-chart-types-images/stacked_area_100.png)

## See also

[color palette](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#color-palette), [color mapping](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#color-mapping-for-data-points), [animation](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#animation), [gradient](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#gradient-fill), [sorting](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#sorting) and [empty points](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#empty-points) for customizing the stacked area 100 series further.