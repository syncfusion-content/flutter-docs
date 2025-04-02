---
layout: post
title: HiLo Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about hiLo chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# HiLo Chart in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter hilo chart quickly, you can check this video.

<style>#flutterHiloChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterHiloChartTutorial' src='https://www.youtube.com/embed/uSsKhlRzC2Q'></iframe>

HiLo Series illustrates the price movements in stock using the high and low values.

To render a HiLo chart, create an instance of [`HiloSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HiloSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties can be used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.
* [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/lowValueMapper.html) - used to get the low values from the series.
* [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/highValueMapper.html) - used to get the high values from the series.

{% tabs %}
{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <CartesianSeries>[
                            // Renders Hilo chart
                            HiloSeries<ChartData, DateTime>(
                                dataSource: financialData,
                                xValueMapper: (ChartData data, _) => data.x,
                                lowValueMapper: (ChartData data, _) => data.low,
                                highValueMapper: (ChartData data, _) => data.high
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![hiLo chart](cartesian-chart-types-images/hilo_chart.png)

#### See Also

* [Color palette](/flutter/cartesian-charts/series-customization#color-palette) 
* [Color mapping](/flutter/cartesian-charts/series-customization#color-mapping-for-data-points)
* [Animation](/flutter/cartesian-charts/series-customization#animation)
* [Empty points](/flutter/cartesian-charts/series-customization#empty-points) 
* [Sorting](/flutter/cartesian-charts/series-customization#sorting)