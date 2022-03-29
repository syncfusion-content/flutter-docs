---
layout: post
title: Column Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about column chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Column Chart in Flutter Cartesian Charts (SfCartesianChart)

To render a column chart, create an instance of [`ColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/XyDataSeries-class.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties can be used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.

{% tabs %}
{% highlight Dart %} 
    
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
                        series: <ChartSeries<ChartData, int>>[
                            // Renders column chart
                            ColumnSeries<ChartData, int>(
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
        ChartData(this.x, this.y, this.y1);
        final int x;
        final double y;
    }

{% endhighlight %}
{% endtabs %}

![Column chart](cartesian-chart-types-images/column.jpg)

## Side-by-side series placement

By default, all the column series that have the same x and y-axes are placed side by side in a chart. If you want to place a series one over the other (overlapped), set the [`enableSideBySideSeriesPlacement`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/enableSideBySideSeriesPlacement.html) property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html) to false and configure the [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property to differentiate the series. The following code snippet and screenshot illustrate the overlapped placement of column series.

{% tabs %}
{% highlight dart hl_lines="16" %} 
    
    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData(2010, 35, 23),
            ChartData(2011, 38, 49),
            ChartData(2012, 34, 12),
            ChartData(2013, 52, 33),
            ChartData(2014, 40, 30)
        ];
        
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        // Columns will be rendered back to back
                        enableSideBySideSeriesPlacement: false,
                        series: <ChartSeries<ChartData, int>>[
                            ColumnSeries<ChartData, int>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y
                            ),
                            ColumnSeries<ChartData, DateTime>(
                                opacity: 0.9,
                                width: 0.4,
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y1
                            )
                        ]
                    )
                )   
            )
        );
    }
    class ChartData {
        ChartData(this.x, this.y, this.y1);
        final int x;
        final double y;
        final double y1;
    }

{% endhighlight %}
{% endtabs %}

![Column side by side placement](cartesian-chart-types-images/sidebySidePlacement.jpg)

## Column width and spacing

The [`spacing`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/spacing.html) property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% tabs %}
{% highlight dart hl_lines="20 22" %} 
    
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
                        series: <ChartSeries<ChartData, int>>[
                            ColumnSeries<ChartData, int>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                // Width of the columns
                                width: 0.8, 
                                // Spacing between the columns
                                spacing: 0.2 
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Column width and spacing](cartesian-chart-types-images/column_width_spacing.jpg)

## Rounded corners

The [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/borderRadius.html) property is used to add the rounded corners to the rectangle.

{% tabs %}
{% highlight dart hl_lines="20" %} 
    
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
                        series: <ChartSeries<ChartData, int>>[
                            ColumnSeries<ChartData, int>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                // Sets the corner radius
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

![Rounded corners](cartesian-chart-types-images/rounded_column.jpg)

#### See Also

* [Rendering each data points with different border radius in column charts](https://www.syncfusion.com/kb/12074/how-to-set-different-border-radius-for-each-rect-series-data-points-by-extending-the).

* [Adding rounded corners for the specific sides in column charts](https://www.syncfusion.com/kb/12059/how-to-add-rounded-corners-for-specific-sides-in-the-rect-series-types-sfcartesianchart).

* [Render a customized column chart](https://www.syncfusion.com/kb/13033/how-to-render-a-customized-column-chart-sfcartesianchart).

## Track customization

Renders column with track. Track is a rectangular bar rendered from the start to the end of the axis. Column series will be rendered above the track. The [`isTrackVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/isTrackVisible.html) property is used to enable the track. The following properties can be used to customize the appearance:

* [`trackColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackColor.html) - changes the color of the track.
* [`trackBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackBorderWidth.html) - changes the stroke width of the track.
* [`trackBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackBorderColor.html) - changes the stroke color of the track.
* [`trackPadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackPadding.html) - adds padding to the track.

{% tabs %}
{% highlight dart hl_lines="18" %} 
    
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
                        series: <ChartSeries<ChartData, int>>[
                            ColumnSeries<ChartData, double>(
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

![Track](cartesian-chart-types-images/track_column.jpg)

#### See Also

* [Color palette](/flutter/cartesian-charts/series-customization#color-palette) 
* [Color mapping](/flutter/cartesian-charts/series-customization#color-mapping-for-data-points)
* [Animation](/flutter/cartesian-charts/series-customization#animation)
* [Gradient](/flutter/cartesian-charts/series-customization#gradient-fill)
* [Empty points](/flutter/cartesian-charts/series-customization#empty-points)
* [Sorting](/flutter/cartesian-charts/series-customization#sorting)

>**Note**: You can refer to our [Flutter Column Chart](https://www.syncfusion.com/flutter-widgets/flutter-charts/chart-types/column-chart) feature tour page for its groundbreaking feature representations.