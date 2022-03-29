---
layout: post
title: Line Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about line chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Line Chart in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter line chart quickly, you can check this video.

<style>#flutterLineChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterLineChartTutorial' src='https://www.youtube.com/embed/zhcxdh4-Jt8'></iframe>

To render a line chart, create an instance of [`LineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties can be used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) - changes the stroke width of the line.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData(2010, 35),
            ChartData(2011, 28),
            ChartData(2012, 34),
            ChartData(2013, 32),
            ChartData(2014, 40)
        ];

        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders line chart
                            LineSeries<ChartData, int>(
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
        final int x;
        final double y;
    }

{% endhighlight %}
{% endtabs %}

![Line chart](cartesian-chart-types-images/line.jpg)

## Dashed line

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of [`LineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LineSeries-class.html) is used to render line series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% tabs %}
{% highlight dart hl_lines="18" %}
    
    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData(2010, 35),
            ChartData(2011, 28),
            ChartData(2012, 34),
            ChartData(2013, 32),
            ChartData(2014, 40)
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            LineSeries<ChartData, int>(
                                dataSource: chartData,
                                // Dash values for line
                                dashArray: <double>[5, 5],
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y)
                        ]
                    )
                )
            )
        );
  }


{% endhighlight %}
{% endtabs %}

![Dashed line chart](cartesian-chart-types-images/dashed_line.jpg)

#### See Also

* [Applying dashed pattern for line chart](https://www.syncfusion.com/kb/12349/how-to-create-dash-pattern-line-chart-in-flutter-using-cartesian-charts-widget).

## Multi-colored line

To render a multi-colored line series, map the individual colors to the data using the [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/pointColorMapper.html) property.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            LineSeries<ChartData, String>(
                                dataSource: [
                                    ChartData('Jan', 35, Colors.red),
                                    ChartData('Feb', 28, Colors.green),
                                    ChartData('Mar', 34, Colors.blue),
                                    ChartData('Apr', 32, Colors.pink),
                                    ChartData('May', 40, Colors.black)
                                ],
                                // Bind the color for all the data points from the data source
                                pointColorMapper:(ChartData data, _) => data.color,
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
        ChartData(this.x, this.y, this.color);
        final String x;
        final double y;
        final Color color;
    }

{% endhighlight %}
{% endtabs %}

![Multi-colored line](cartesian-chart-types-images/multiColored_line.jpg)

#### See Also

* [Color palette](/flutter/cartesian-charts/series-customization#color-palette) 
* [Color mapping](/flutter/cartesian-charts/series-customization#color-mapping-for-data-points)
* [Animation](/flutter/cartesian-charts/series-customization#animation)
* [Gradient](/flutter/cartesian-charts/series-customization#gradient-fill)
* [Empty points](/flutter/cartesian-charts/series-customization#empty-points)
* [Sorting](/flutter/cartesian-charts/series-customization#sorting) 