---
layout: post
title: Bar Chart in Flutter Cartesian Charts Widget | Syncfusion 
description: Learn here all about bar chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget, it's elements and more details.
platform: flutter
control: Chart
documentation: ug
---

# Bar Chart in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter bar chart quickly, you can check this video.

<style>#flutterBarChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterBarChartTutorial' src='https://www.youtube.com/embed/MHQzCN_jD1Q'></iframe>

To render a bar chart, create an instance of [`BarSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties can be used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.

{% tabs %}
{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData(1, 35),
            ChartData(2, 23),
            ChartData(3, 34),
            ChartData(4, 25),
            ChartData(5, 40)
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders bar chart
                            BarSeries<ChartData, double>(
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

![Bar chart in Flutter Cartesian Charts.](cartesian-chart-types-images/flutter-bar-chart.jpg)

## Bar width and spacing

The [`spacing`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/spacing.html) property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% tabs %}
{% highlight dart hl_lines="13 15" %} 
    
    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData(1, 35),
            ChartData(2, 23),
            ChartData(3, 34),
            ChartData(4, 25),
            ChartData(5, 40)
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BarSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                // Width of the bars
                                width: 0.6, 
                                // Spacing between the bars
                                spacing: 0.3 
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Bar width and spacing in Flutter Cartesian Charts.](cartesian-chart-types-images/flutter-bar-chart-width-spacing.jpg)

## Rounded corners

The [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/borderRadius.html) property is used to add the rounded corners to the rectangle.

{% tabs %}
{% highlight dart hl_lines="12" %} 
    
    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData(1, 35),
            ChartData(2, 23),
            ChartData(3, 34),
            ChartData(4, 25),
            ChartData(5, 40)
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BarSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                borderRadius: BorderRadius.all(Radius.circular(15))
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Bar rounded corners in Flutter Cartesian Charts.](cartesian-chart-types-images/flutter-rounded-bar-chart.jpg)

## Track customization

You can render the bar chart with track. Track is a rectangular bar rendered from the start to the end of the axis. Bar series will be rendered above the track. The [`isTrackVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/isTrackVisible.html) property is used to enable the track. The following properties can be used to customize the appearance:

* [`trackColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackColor.html) - changes the color of the track.
* [`trackBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackBorderWidth.html) - changes the stroke width of the track.
* [`trackBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackBorderColor.html) - changes the stroke color of the track.
* [`trackPadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackPadding.html) - Adds padding to the track.

{% tabs %}
{% highlight dart hl_lines="11" %} 
    
    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData(1, 35),
            ChartData(2, 23),
            ChartData(3, 34),
            ChartData(4, 25),
            ChartData(5, 40)
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BarSeries<ChartData, double>(
                                dataSource: chartData,
                                // Renders the track
                                isTrackVisible: true,
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

![Bar track in Flutter Cartesian Charts.](cartesian-chart-types-images/flutter-track-bar-chart.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the bar series further.

>**Note**: You can refer to our [Flutter Bar Chart](https://www.syncfusion.com/flutter-widgets/flutter-charts/chart-types/bar-chart) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter Bar Chart example](https://flutter.syncfusion.com/#/cartesian-charts/chart-types/bar/default-bar-chart) that shows how to easily configure with built-in support for creating stunning visual effects.

#### See Also

* [Create vertical bar chart](https://support.syncfusion.com/kb/article/10833/how-to-create-vertical-bar-chart-in-flutter-using-cartesian-charts-widget-sfcartesianchart).

* [Create horizontal bar chart](https://support.syncfusion.com/kb/article/10822/how-to-create-horizontal-bar-chart-in-flutter-using-cartesian-charts-widget).
