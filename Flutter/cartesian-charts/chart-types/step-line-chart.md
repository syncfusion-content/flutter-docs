---
layout: post
title: Step line Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about step line chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Step line Chart in Flutter Cartesian Charts (SfCartesianChart)

To render a step line chart, create an instance of [`StepLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StepLineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties can be used to customize the appearance of the step line chart:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/color.html) - changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/opacity.html) - controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/width.html) - changes the stroke width of the line.

{% tabs %}
{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         final List<ChartData> chartData = [
            ChartData(DateTime(2010), 32),
            ChartData(DateTime(2011), 40),
            ChartData(DateTime(2012), 34),
            ChartData(DateTime(2013), 52),
            ChartData(DateTime(2014), 42),
            ChartData(DateTime(2015), 38),
            ChartData(DateTime(2016), 41),
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <CartesianSeries>[
                            // Renders step line chart
                            StepLineSeries<ChartData, DateTime>(
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

{% endhighlight %}
{% endtabs %}

![Step line chart](cartesian-chart-types-images/stepline.jpg)

## Dashed step line

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of the [`StepLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StepLineSeries-class.html) is used to render step line series with dashes. The odd value is considered as rendering the size and the even value is considered as gap.

{% tabs %}
{% highlight dart hl_lines="21" %} 
    
    @override
    Widget build(BuildContext context) {
         final List<ChartData> chartData = [
            ChartData(DateTime(2010), 32),
            ChartData(DateTime(2011), 40),
            ChartData(DateTime(2012), 34),
            ChartData(DateTime(2013), 52),
            ChartData(DateTime(2014), 42),
            ChartData(DateTime(2015), 38),
            ChartData(DateTime(2016), 41),
        ];
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <CartesianSeries>[
                            StepLineSeries<ChartData, DateTime>(
                                dataSource: chartData,
                                // Dashes for step line
                                dashArray: <double>[5, 5],
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
{% endtabs %}

![Step line chart](cartesian-chart-types-images/dashed_stepline.jpg)

#### See Also

* [Color palette](/flutter/cartesian-charts/series-customization#color-palette) 
* [Color mapping](/flutter/cartesian-charts/series-customization#color-mapping-for-data-points)
* [Animation](/flutter/cartesian-charts/series-customization#animation)
* [Gradient](/flutter/cartesian-charts/series-customization#gradient-fill)
* [Empty points](/flutter/cartesian-charts/series-customization#empty-points)
* [Sorting](/flutter/cartesian-charts/series-customization#sorting)