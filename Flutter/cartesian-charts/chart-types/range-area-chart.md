---
layout: post
title: Range area Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about range area Chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Range area Chart in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter range area chart quickly, you can check this video.

<style>#flutterRangeareaChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterRangeareaChartTutorial' src='https://www.youtube.com/embed/uSsKhlRzC2Q'></iframe>

To render a range area chart, create an instance of `RangeAreaSeries` and add to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). 

Since the [`RangeAreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeAreaSeries-class.html) requires two Y values for a point, your data should contain high and low values. High and low value specifies the maximum and minimum range of the point. 

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
                        primaryXAxis: DateTimeAxis(),
                        series: <CartesianSeries>[
                            RangeAreaSeries<ChartData, DateTime>(
                                dataSource: chartData,
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
            final DateTime x;
            final double high;
            final double low;
    }

{% endhighlight %}
{% endtabs %}

![Range area chart](cartesian-chart-types-images/range_area.png)

###	Border customization

The borders of the range area chart can be customized using the [`borderDrawMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeAreaSeries/borderDrawMode.html) property. The default value of the [`RangeAreaBorderMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeAreaBorderMode.html) property is `all` and the other value is `excludeSides`.

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
                            RangeAreaSeries<ChartData, DateTime>(
                                dataSource: chartData,
                                color: Color.fromARGB(224, 242, 241,1),
                                borderDrawMode: RangeAreaBorderMode.excludeSides,
                                borderColor: Colors.green,
                                borderWidth: 2,
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

{% endhighlight %}
{% endtabs %}

![Range area border](cartesian-chart-types-images/range_area_border.png)

#### See Also

* [Color palette](/flutter/cartesian-charts/series-customization#color-palette) 
* [Color mapping](/flutter/cartesian-charts/series-customization#color-mapping-for-data-points)
* [Animation](/flutter/cartesian-charts/series-customization#animation)
* [Gradient](/flutter/cartesian-charts/series-customization#gradient-fill)
* [Empty points](/flutter/cartesian-charts/series-customization#empty-points)
* [Sorting](/flutter/cartesian-charts/series-customization#sorting)