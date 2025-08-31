---
layout: post
title: Range column Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about range column chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Range column Chart in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter range column chart quickly, you can check this video.

<style>#flutterRangecolumnChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterRangecolumnChartTutorial' src='https://www.youtube.com/embed/uSsKhlRzC2Q'></iframe>

To render a range column chart, create an instance of [`RangeColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeColumnSeries-class.html) and add to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). 

Since the [`RangeColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeColumnSeries-class.html) requires two Y values for a point, your data should contain high and low values. High and low value specifies the maximum and minimum range of the point. 

* [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeSeriesBase/highValueMapper.html) - field in the data source, which is considered as high value for the data points.
* [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeSeriesBase/lowValueMapper.html) - field in the data source, which is considered as low value for the data points. 

{% tabs %}
{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <CartesianSeries>[
                            RangeColumnSeries<ChartData, String>(
                                dataSource: <ChartData>[
                                    ChartData('Jan', 3, 9),
                                    ChartData('Feb', 4, 11),
                                    ChartData('Mar', 6, 13),
                                    ChartData('Apr', 9, 17),
                                    ChartData('May', 12, 20),
                                ],
                                xValueMapper: (ChartData data, _) => data.x,
                                lowValueMapper: (ChartData data, _) => data.low,
                                highValueMapper: (ChartData data, _) => data.high,
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.high, this.low);
            final String x;
            final double high;
            final double low;
    }

{% endhighlight %}
{% endtabs %}

![Range column chart](cartesian-chart-types-images/range_column.jpg)

## Data label

In the range column chart when data label is enabled, by default there will be two values displayed namely, high and low, but in the other types of charts, only y value will be displayed.

{% tabs %}
{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <CartesianSeries>[
                            RangeColumnSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                lowValueMapper: (ChartData data, _) => data.low,
                                highValueMapper: (ChartData data, _) => data.high,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true, 
                                    labelAlignment: ChartDataLabelAlignment.top
                                ),
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Range column datalabel](cartesian-chart-types-images/range_column_datalabel.jpg)

## Transposed range column

The [`isTransposed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/isTransposed.html) property of [`CartesianSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries-class.html) is used to transpose the horizontal and vertical axes, to view the data in a different perspective. Using this feature, you can render range column chart.

{% tabs %}
{% highlight dart hl_lines="7" %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        isTransposed: true,
                        primaryXAxis: CategoryAxis(),
                        series: <CartesianSeries>[
                            RangeColumnSeries<ChartData, String>(
                                dataSource: <ChartData>[
                                    ChartData('Jan', 3, 9),
                                    ChartData('Feb', 4, 11),
                                    ChartData('Mar', 6, 13),
                                    ChartData('Apr', 9, 17),
                                    ChartData('May', 12, 20),
                                ],
                                xValueMapper: (ChartData data, _) => data.x,
                                lowValueMapper: (ChartData data, _) => data.low,
                                highValueMapper: (ChartData data, _) => data.high,
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.high, this.low);
            final String x;
            final double high;
            final double low;
    }

{% endhighlight %}
{% endtabs %}

#### See Also

* [Color palette](/flutter/cartesian-charts/series-customization#color-palette) 
* [Color mapping](/flutter/cartesian-charts/series-customization#color-mapping-for-data-points)
* [Animation](/flutter/cartesian-charts/series-customization#animation)
* [Gradient](/flutter/cartesian-charts/series-customization#gradient-fill)
* [Empty points](/flutter/cartesian-charts/series-customization#empty-points)
* [Sorting](/flutter/cartesian-charts/series-customization#sorting)