---
layout: post
title: Area Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about area chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Area Chart in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter area chart quickly, you can check this video.

<style>#flutterAreaChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterAreaChartTutorial' src='https://www.youtube.com/embed/E_odUnOsBtQ'></iframe>

To render an area chart, create an instance of [`AreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The area chart shows the filled area to represent the data, but when there are more than a series, this may hide the other series. To get rid of this, increase or decrease the transparency of the series. 

The following properties can be used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.

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
                            // Renders area chart
                            AreaSeries<ChartData, int>(
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

![Area chart](cartesian-chart-types-images/area.jpg)

##	Border customization

The borders of the area chart can be customized using the [`borderDrawMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaSeries/borderDrawMode.html) property. The default value of the [`borderDrawMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaSeries/borderDrawMode.html) property is [`BorderDrawMode.top`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BorderDrawMode.html). The other values are [`BorderDrawMode.all`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BorderDrawMode.html) and [`BorderDrawMode.excludeBottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BorderDrawMode.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <ChartSeries>[
                            AreaSeries<ChartData, DateTime>(
                                dataSource: chartData,
                                color: Colors.deepOrange[300],
                                borderMode: AreaBorderMode.excludeBottom,
                                borderColor: Colors.green,
                                borderWidth: 2,
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

![Area border](cartesian-chart-types-images/area_border.jpg)

## Area with gradients

The [`gradient`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/gradient.html) property is used to define the gradient colors. The colors from this property is used for series.


{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData(1924, 400),
            ChartData(1925, 410),
            ChartData(1926, 405),
            ChartData(1927, 410),
            ChartData(1928, 350),
            ChartData(1929, 370),
            ChartData(1930, 500),
            ChartData(1931, 390),
            ChartData(1932, 450),
            ChartData(1933, 440),
            ChartData(1934, 350),
            ChartData(1935, 370),
            ChartData(1936, 480),
            ChartData(1937, 410),
            ChartData(1938, 530),
            ChartData(1939, 520),
            ChartData(1940, 390),
            ChartData(1941, 360),
            ChartData(1942, 405),
            ChartData(1943, 400),
        ];
        final List<Color> color = <Color>[];
        color.add(Colors.blue[50]!);
        color.add(Colors.blue[200]!);
        color.add(Colors.blue);

        final List<double> stops = <double>[];
        stops.add(0.0);
        stops.add(0.5);
        stops.add(1.0);

        final LinearGradient gradientColors =
            LinearGradient(colors: color, stops: stops);
        
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: NumericAxis(labelFormat: '{value}mm')
                        series: <ChartSeries>[
                            // Renders area chart
                            AreaSeries<ChartData, int>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                 gradient: gradientColors
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Area gradients](cartesian-chart-types-images/area_gradient.png)

## Area with empty points

Data points with a null value are considered empty points. Empty data points are ignored and are not plotted in the chart. By using [`emptyPointSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/emptyPointSettings.html) property in series, you can decide the action taken for empty points. Available [`modes`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointSettings/mode.html) are [`EmptyPointMode.gap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode.html), [`EmptyPointMode.zero`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode.html), [`EmptyPointMode.drop`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode.html) and [`EmptyPointMode.average`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode.html). Default mode of the empty point is [`EmptyPointMode.gap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData(1924, 400),
            ChartData(1925, 410),
            ChartData(1926, 405),
            ChartData(1927, 410),
            ChartData(1928, 350),
            ChartData(1929, 370),
            ChartData(1930, 500),
            ChartData(1931, 390),
            ChartData(1932, null),
            ChartData(1933, null),
            ChartData(1934, null),
            ChartData(1935, null),
            ChartData(1936, null),
            ChartData(1937, 410),
            ChartData(1938, 530),
            ChartData(1939, 520),
            ChartData(1940, 390),
            ChartData(1941, 360),
            ChartData(1942, 405),
            ChartData(1943, 400),
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <ChartSeries>[
                            AreaSeries<ChartData, DateTime>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,emptyPointSettings:
                                EmptyPointSettings(mode: EmptyPointMode.zero)
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Area with empty points](cartesian-chart-types-images/area_emptypoints.png)



## Vertical area chart

The [`isTransposed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/isTransposed.html) property of [`CartesianSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries-class.html) is used to transpose the horizontal and vertical axes, to view the data in a different perspective. Using this feature, you can render vertical area chart.

{% highlight dart hl_lines="7" %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        isTransposed: true,
                        primaryXAxis: DateTimeAxis(),
                        series: <ChartSeries>[
                            AreaSeries<ChartData, DateTime>(
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

![Vertical area chart](cartesian-chart-types-images/vertical_area.png)

#### See Also

* [color palette](/flutter/cartesian-charts/series-customization#color-palette) 
* [color mapping](/flutter/cartesian-charts/series-customization#color-mapping-for-data-points)
* [animation](/flutter/cartesian-charts/series-customization#animation)
* [gradient](/flutter/cartesian-charts/series-customization#gradient-fill)
* [empty points](/flutter/cartesian-charts/series-customization#empty-points)


>**Note**: You can refer to our [Flutter Area Chart](https://www.syncfusion.com/flutter-widgets/flutter-charts/chart-types/area-chart) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Area Chart example](https://flutter.syncfusion.com/#/cartesian-charts/chart-types/area/default-area-chart) that shows how to easily configure with built-in support for creating stunning visual effects.