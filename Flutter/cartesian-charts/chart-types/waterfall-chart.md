---
layout: post
title: Waterfall Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about waterfall chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Waterfall Chart in Flutter Cartesian Charts (SfCartesianChart)

The waterfall chart explains gradual changes in the quantitative value of an entity that is subject to changes by increments or decrements. Using the waterfall chart, you can quickly illustrate changes in revenues.

To render a waterfall chart, create an instance of [`WaterfallSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries-class.html) and add to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties to customize the appearance.

* [`negativePointsColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/negativePointsColor.html) - changes the color of the negative data points in the series. If no color is specified, then the negative data points will be rendered with the series default color.
* [`intermediateSumColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/intermediateSumColor.html) - changes the color of the intermediate sum points in the series. If no color is specified, then the intermediate sum points will be rendered with the series default color.
* [`totalSumColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/totalSumColor.html) - changes the color of the total sum points in the series. If no color is specified, then the total sum points will be rendered with the series default color.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/color.html) - changes the color of the series. If no color is specified, then the series will be rendered with the default palette color.
* [`connectorLineSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/connectorLineSettings.html) - used to customize the waterfall chart connector line. Data points in waterfall chart are connected using the connector line. Provides the options to change the [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/width.html), [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/color.html) and [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallConnectorLineSettings/dashArray.html) of the connector line to customize the appearance.
* [`spacing`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/spacing.html) - used to provide spacing between the data points in waterfall chart. The value ranges from 0 to 1, where 1 represents 100% and 0 represents 0% of the available space.
* [`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/xValueMapper.html) - field in the data source, which is considered as x-value.
* [`yValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/XyDataSeries/yValueMapper.html) - field in the data source, which is considered as y-value.
* [`intermediateSumPredicate`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/intermediateSumPredicate.html) - the boolean value based on which the data point will be considered as an intermediate sum or not. If this has true value, then that point will be considered as an intermediate sum. Else if it has false, then it will be considered as a normal data point in the chart.
* [`totalSumPredicate`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/totalSumPredicate.html) - the boolean value based on which the data point will be considered as the total sum or not. If this has true value, then that point will be considered as a total sum. Else if it has false, then it will be considered as a normal data point in the chart.

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCartesianChart(
                    primaryXAxis:
                        NumericAxis(minimum: 0, interval: 2, maximum: 12),
                    series: <ChartSeries<ChartData, double>>[
              WaterfallSeries<ChartData, double>(
                  dataSource: <ChartData>[
                    ChartData(2, 10),
                    ChartData(3, -3),
                    ChartData(4, 5, true),
                    ChartData(5, 4),
                    ChartData(6, -2),
                    ChartData(7, -5, true),
                    ChartData(8, -10),
                    ChartData(9, 8),
                    ChartData(10, 8),
                    ChartData(11, 5, false),
                  ],
                  negativePointsColor: const Color.fromRGBO(229, 101, 144, 1),
                  intermediateSumColor: const Color.fromRGBO(79, 129, 188, 1),
                  totalSumColor: const Color.fromRGBO(79, 129, 188, 1),
                  color: const Color.fromRGBO(0, 189, 174, 1),
                  xValueMapper: (ChartData data, _) => data.x,
                  yValueMapper: (ChartData data, _) => data.y,
                  intermediateSumPredicate: (ChartData data, _) =>
                      data.isIntermediate,
                  totalSumPredicate: (ChartData data, _) => data.isTotal,
                  connectorLineSettings:
                      WaterfallConnectorLineSettings(width: 2.5))
                           ]
                        )
                )
            )   
        );
    }

    class ChartData {
        ChartData(this.x, this.y, [this.isIntermediate, this.isTotal]);
        final double? x;
        final num? y;
        final bool? isIntermediate;
        final bool? isTotal;
    }

{% endhighlight %}
{% endtabs %}

![waterfall_chart](cartesian-chart-types-images/waterfall_series.png)

#### See Also

* [Color palette](/flutter/cartesian-charts/series-customization#color-palette) 
* [Color mapping](/flutter/cartesian-charts/series-customization#color-mapping-for-data-points)
* [Animation](/flutter/cartesian-charts/series-customization#animation)
* [Gradient](/flutter/cartesian-charts/series-customization#gradient-fill)
* [Empty points](/flutter/cartesian-charts/series-customization#empty-points)
* [Sorting](/flutter/cartesian-charts/series-customization#sorting)
