---
layout: post
title: Candle Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about candle chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Candle Chart in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter candle chart quickly, you can check this video.

<style>#flutterCandleChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterCandleChartTutorial' src='https://www.youtube.com/embed/g5cniDExpRw'></iframe>

[Flutter Candle series](https://www.syncfusion.com/flutter-widgets/flutter-charts/chart-types/candle-chart) is similar to HiLo Open Close series, used to represent the low, high, open and closing price over time.

To render a Candle chart, create an instance of [` CandleSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties can be used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.
* [`showIndicationForSameValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/showIndicationForSameValues.html)- used to show indication of the data point with a thin line when its high and low values are same and also when all the values of high, low, open and close are same for the data point. By default is set to be `false`.
* [`enableSolidCandles`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/enableSolidCandles.html)- used to enable/disable the solid candles. By default is set to be `false`. The fill color of the candle will be defined by its opening and closing values.
* [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/lowValueMapper.html) - used to get the low values from the series.
* [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/highValueMapper.html) - used to get the high values from the series.
* [`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/openValueMapper.html) - used to get the open values from the series.
* [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/closeValueMapper.html) - used to get the close values from the series.
* [`bearFillColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/bearColor.html) - bearFillColor will be applied when the opening value is less than the closing value.
* [`bullFillColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/bullColor.html) - bullFillColor will be applied when the opening value is greater than closing value.



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
                            // Renders CandleSeries
                            CandleSeries<ChartData, DateTime>(
                                dataSource: financialData,
                                xValueMapper: (ChartData data, _) => data.x,
                                lowValueMapper: (ChartData data, _) => data.low,
                                highValueMapper: (ChartData data, _) => data.high, 
                                openValueMapper: (ChartData data, _) => data.open,
                          closeValueMapper: (ChartData data, _) => data.close,

                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![candle chart](cartesian-chart-types-images/candle.png)

#### See Also 

* [Rendering flutter candlestick chart](https://support.syncfusion.com/kb/article/10683/how-to-render-flutter-candlestick-chart-using-the-charts-widget-sfcartesianchart).

* [Display volume data of financial series](https://support.syncfusion.com/kb/article/11479/display-volume-data-of-financial-series-in-flutter-cartesian-chart)

## Indication for same values

In the Candle series, there is a feature for the datapoints indication when their high and low values are same or open and close values or high, low, open and close values are same for a datapoint. For using this indication feature, [`showIndicationForSameValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/showIndicationForSameValues.html) property can be set to `true`.

The following are the types of indication when the combination of high, low, open and close values are same for a datapoint.

* In the Candle chart, if the open and close values are same then a horizontal line will be drawn at that value by default.
* If the high and low values are same and with [`showIndicationForSameValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/showIndicationForSameValues.html) property set to true then, a thin vertical line is drawn and if API is set to false, the line will not be drawn. 


{% tabs %}
{% highlight dart hl_lines="8" %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: SfCartesianChart(
                        series: <CartesianSeries>[
                          CandleSeries<ChartData, double>(
                            showIndicationForSameValues: true,
                            dataSource: <ChartData>[
                                ChartData( // Open and close values are same
                                    x: 5,
                                    open: 86.3593,
                                    high: 88.1435,
                                    low: 84.3914,
                                    close: 86.3593),
                                ChartData( // High and low values are same
                                    x: 10,
                                    open: 85.4425,
                                    high: 86.4885,
                                    low: 86.4885,
                                    close: 87.001),
                                ChartData( //High, low, open, and close values all are same
                                    x: 15,
                                    open: 86.4885,
                                    high: 86.4885,
                                    low: 86.4885,
                                    close: 86.4885),
                            ],
                            xValueMapper: (ChartData data, _) => data.x,
                            highValueMapper: (ChartData data, _) => data.high,
                            lowValueMapper: (ChartData data, _) => data.low,
                            openValueMapper: (ChartData data, _) => data.open,
                            closeValueMapper: (ChartData data, _) => data.close)
                        ]
                    ),
                )   
            );
        }

{% endhighlight %}
{% endtabs %}

![Candle Indication](cartesian-chart-types-images/candle_indication.jpg)

#### See Also

* [Color palette](/flutter/cartesian-charts/series-customization#color-palette) 
* [Color mapping](/flutter/cartesian-charts/series-customization#color-mapping-for-data-points)
* [Animation](/flutter/cartesian-charts/series-customization#animation)
* [Empty points](/flutter/cartesian-charts/series-customization#empty-points)
* [Sorting](/flutter/cartesian-charts/series-customization#sorting)  