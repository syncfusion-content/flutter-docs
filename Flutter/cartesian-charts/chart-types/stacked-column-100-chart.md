---
layout: post
title: 100% Stacked column in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about 100% stacked Column chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# 100% Stacked column in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter 100% stacked column chart quickly, you can check this video.

<style>#flutter100stackedcolumnChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutter100stackedcolumnChartTutorial' src='https://www.youtube.com/embed/NCUDBD_ClHo'></iframe>

To render a 100% stacked column chart, create an instance of [`StackedColumn100Series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/XyDataSeries-class.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties can be used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.
* [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries/borderRadius.html) -  used to add the rounded corners to the rectangle.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            StackedColumn100Series<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y
                            ),
                            StackedColumn100Series<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y2
                            ),
                            StackedColumn100Series<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y3
                            ),
                            StackedColumn100Series<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y4
                            )
                        ]
                    )
                )      
            )
        );
    }

{% endhighlight %}

![Stacked 100 column chart](cartesian-chart-types-images/stacked_column_100.png)

## Column width and spacing

The `spacing` property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The `width` property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            StackedColumn100Series<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                width: 0.8, // Width of the columns
                                spacing: 0.2 // Spacing between the columns
                            ),
                            StackedColumn100Series<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y2,
                                width: 0.8, // Width of the columns
                                spacing: 0.2 // Spacing between the columns
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked 100 column width and spacing](cartesian-chart-types-images/stacked_column_100_size.png)

#### See Also

 * [color palette](./cartesian-charts/series-customization#color-palette) 
 * [color mapping](./cartesian-charts/series-customization#color-mapping-for-data-points)
 * [animation](./cartesian-charts/series-customization#animation)
 * [gradient](./cartesian-charts/series-customization#gradient-fill)
 * [empty points](./cartesian-charts/series-customization#empty-points)
 * [Sorting](./cartesian-charts/series-customization##sorting)