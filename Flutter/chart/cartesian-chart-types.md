---
layout: post
title: Syncfusion Cartesian Chart types
description: Leart what are the different types of Charts available in Flutter Charts.
platform: flutter
control: Chart
documentation: ug
---

# Cartesian chart types

## Line chart

To render a line chart, create an instance of [`LineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the line.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<SalesData> chartData = [
            SalesData(2010, 35),
            SalesData(2011, 28),
            SalesData(2012, 34),
            SalesData(2013, 32),
            SalesData(2014, 40)
        ];

        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders line chart
                            LineSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

    class SalesData {
        SalesData(this.year, this.sales);
            final double year;
            final double sales;
    }

{% endhighlight %}

![Line chart](images/cartesian-chart-types/line.jpg)

### Dashed line

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of [`LineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LineSeries-class.html) is used to render line series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            LineSeries<SalesData, String>(
                                dataSource: chartData,
                                // Dash values for line
                                dashArray: <double>[5,5],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Dashed line chart](images/cartesian-chart-types/dashed_line.jpg)

### Multi-colored line

To render a multi-colored line series, map the individual colors to the data using the [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/pointColorMapper.html) property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            LineSeries<SalesData, String>(
                                dataSource: [
                                    SalesData('Jan', 35, Colors.red),
                                    SalesData('Feb', 28, Colors.green),
                                    SalesData('Mar', 34, Colors.blue),
                                    SalesData('Apr', 32, Colors.pink),
                                    SalesData('May', 40, Colors.black)
                                ],
                                // Bind the color for all the data points from the data source
                                pointColorMapper:(SalesData sales, _) => sales.segmentColor,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

    class SalesData {
        SalesData(this.year, this.sales, this.segmentColor);
        final double year;
        final double sales;
        final Color segmentColor;
    }

{% endhighlight %}

![Multi-colored line](images/cartesian-chart-types/multiColored_line.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the line series further.

## Fast line chart

[`FastLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FastLineSeries-class.html) is a line chart, but it loads faster than [`LineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LineSeries-class.html). You can use this when there are large number of points to be loaded in a chart. To render a fast line chart, create an instance of [`FastLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FastLineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of fast line segment:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the line.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders fast line chart
                            FastLineSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }


{% endhighlight %}

![Fast line chart](images/cartesian-chart-types/fastline.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the fast line series further.

## Area chart

To render an area chart, create an instance of [`AreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The area chart shows the filled area to represent the data, but when there are more than a series, this may hide the other series. To get rid of this, increase or decrease the transparency of the series. 

The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders area chart
                            AreaSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Area chart](images/cartesian-chart-types/area.jpg)

###	Border customization

The borders of the area chart can be customized using the [`borderMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaSeries/borderMode.html) property. The default value of the [`borderMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaSeries/borderMode.html) property is [`top`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaBorderMode-class.html). The other values are [`all`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaBorderMode-class.html) and [`excludeBottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaBorderMode-class.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            AreaSeries<SalesData, double>(
                                dataSource: chartData,
                                color: Colors.deepOrange[300],
                                borderMode: AreaBorderMode.excludeBottom,
                                borderColor: Colors.green,
                                borderWidth: 2,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Area border](images/cartesian-chart-types/area_border.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the area series further.

## Spline chart

To render a spline chart, create an instance of [`SplineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance of spline segment:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Spline border](images/cartesian-chart-types/spline.jpg)

### Dashed spline

The [`dashArray`]() property of the [`SplineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/SplineSeries.html) is used to render spline series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            SplineSeries<SalesData, String>(
                                dataSource: chartData,
                                // Dash values for spline
                                dashArray: <double>[5, 5],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Dashed spline chart](images/cartesian-chart-types/dashed_spline.jpg)

###	Spline rendering types

The [`splineType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/splineType.html) allows you to change the spline curve in series. The following types are used in [`SplineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/SplineSeries.html):

* natural
* monotonic
* cardinal
* clamped

By default, the value of [`splineType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/splineType.html) is [`natural`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineType-class.html).

The following code sample demonstrates how to set the [`splineType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/splineType.html) value to [`cardinal`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineType-class.html). When you set the cardinal type, you can specify the desired line tension of the [`cardinal`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineType-class.html) spline using the [`cardinalSplineTension`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/cardinalSplineTension.html) property. The value of this property ranges from 0 to 1.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                // Type of spline
                                splineType: SplineType.cardinal,
                                cardinalSplineTension: 0.9,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Spline type](images/cartesian-chart-types/cardinal_spline.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the spline series further.

## Column chart

To render a column chart, create an instance of [`ColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries-class.html), and add it to the [`series`]() collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders column chart
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )      
            )
        );
    }

{% endhighlight %}

![Column chart](images/cartesian-chart-types/column.jpg)

### Side-by-side series placement

By default, all the column series that have the same x and y-axes are placed side by side in a chart. If you want to place a series one over the other (overlapped), set the [`enableSideBySideSeriesPlacement`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/enableSideBySideSeriesPlacement.html) property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html) to false and configure the [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property to differentiate the series. The following code snippet and screenshot illustrate the overlapped placement of column series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        final List<SalesData> chartData = [
            SalesData(2010, 35, 23),
            SalesData(2011, 38, 49),
            SalesData(2012, 34, 12),
            SalesData(2013, 52, 33),
            SalesData(2014, 40, 30)
        ];
        
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        // Columns will be rendered back to back
                        enableSideBySideSeriesPlacement: false,
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            ),
                            ColumnSeries<SalesData, double>(
                                opacity: 0.9,
                                width: 0.4,
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.loss
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Column side by side placement](images/cartesian-chart-types/sidebySidePlacement.jpg)

### Column width and spacing

The [`spacing`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/spacing.html) property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                width: 0.8, // Width of the columns
                                spacing: 0.2 // Spacing between the columns
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Column width and spacing](images/cartesian-chart-types/column_width_spacing.jpg)

### Rounded corners

The [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/borderRadius.html) property is used to add the rounded corners to the rectangle.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
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

![Rounded corners](images/cartesian-chart-types/rounded_column.jpg)

### Track customization

Renders column with track. Track is a rectangular bar rendered from the start to the end of the axis. Column series will be rendered above the track. The [`isTrackVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/isTrackVisible.html) property is used to enable the track. The following properties are used to customize the appearance:

* [`trackColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackColor.html) – Changes the color of the track.
* [`trackBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackBorderWidth.html) – Changes the stroke width of the track.
* [`trackBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackBorderColor.html) – Changes the stroke color of the track.
* [`trackPadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackPadding.html) - Adds padding to the track.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                // Renders the track
                                isTrackVisible: true,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Track](images/cartesian-chart-types/track_column.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the column series further.

## Bar chart

To render a bar chart, create an instance of [`BarSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders bar chart
                            BarSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bar chart](images/cartesian-chart-types/bar.jpg)

### Column width and spacing

The [`spacing`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/spacing.html) property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BarSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                width: 0.6, // Width of the bars
                                spacing: 0.3 // Spacing between the bars
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bar width and spacing](images/cartesian-chart-types/bar_width_spacing.jpg)

### Rounded corners

The [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/borderRadius.html) property is used to add the rounded corners to the rectangle.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BarSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                borderRadius: BorderRadius.all(Radius.circular(15))
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bar rounded corners](images/cartesian-chart-types/rounded_bar.jpg)

### Track customization

You can render the bar chart with track. Track is a rectangular bar rendered from the start to the end of the axis. Bar series will be rendered above the track. The [`isTrackVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/isTrackVisible.html) property is used to enable the track. The following properties are used to customize the appearance:

* [`trackColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackColor.html) – Changes the color of the track.
* [`trackBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackBorderWidth.html) – Changes the stroke width of the track.
* [`trackBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackBorderColor.html) – Changes the stroke color of the track.
* [`trackPadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackPadding.html) - Adds padding to the track.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BarSeries<SalesData, double>(
                                dataSource: chartData,
                                // Renders the track
                                isTrackVisible: true,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bar track](images/cartesian-chart-types/track_bar.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the bar series further.

## Bubble chart

To render a bubble chart, create an instance of [`BubbleSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BubbleSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html).

Bubble chart requires three fields (X, Y, and Size) to plot a point. Here, [`sizeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/sizeValueMapper.html) is used to map the size of each bubble segment from data source.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke width of the series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         final List<ChartData> chartData = [
            ChartData(2010, 35, 0.32),
            ChartData(2011, 38, 0.21),
            ChartData(2012, 34, 0.38),
            ChartData(2013, 52, 0.29),
            ChartData(2014, 40, 0.34)
        ];

        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders bubble chart
                            BubbleSeries<ChartData, double>(
                                dataSource: chartData,
                                sizeValueMapper: (ChartData sales, _) => sales.size,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.y, this.size);
            final double x;
            final double y;
            final double size;
    }

{% endhighlight %}

![Bubble chart](images/cartesian-chart-types/bubble.jpg)

### Change the min and max radius of bubble

The [`minimumRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BubbleSeries/minimumRadius.html) property is used to change the minimum size of the series and the [`maximumRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BubbleSeries/maximumRadius.html) property is used to change the maximum size of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BubbleSeries<ChartData, double>(
                                dataSource: chartData,
                                sizeValueMapper: (ChartData sales, _) => sales.size,
                                minimumRadius:9, // Minimum radius of bubble
                                maximumRadius: 15, // Maximum radius of bubble
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bubble size](images/cartesian-chart-types/bubble_radius.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the bubble series further.

## Scatter chart

To render a scatter chart, create an instance of [`ScatterSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ScatterSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the scatter segment appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders scatter chart
                            ScatterSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Scatter chart](images/cartesian-chart-types/scatter.jpg)

###	Change shape and size of the scatter

The [`shape`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/shape.html) property is used to change the rendering shape of scatter series. The available shapes are [`circle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`rectangle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`pentagon`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`verticalLine`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`horizontalLine`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`diamond`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`triangle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`image`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), and [`invertedTriangle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html). If [`image`]() shape is specified, then you can assign the image using the [`imageUrl`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/imageUrl.html) property.

The [`height`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/height.html) and [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/width.html) properties of [`markerSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/markerSettings.html) are used to change the height and width of the scatter series, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            ScatterSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y,
                                markerSettings: MarkerSettings(
                                    height: 15,
                                    width: 15,
                                    // Scatter will render in diamond shape
                                    shape: DataMarkerType.diamond
                                )
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Scatter shape](images/cartesian-chart-types/scatter_shape.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the scatter series further.

## Step line chart

To render a step line chart, create an instance of [`StepLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StepLineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of spline segment:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the line.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders step line chart
                            StepLineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Step line chart](images/cartesian-chart-types/stepline.jpg)

### Dashed step line

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of the [`StepLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StepLineSeries-class.html) is used to render step line series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StepLineSeries<ChartData, double>(
                                dataSource: chartData,
                                // Dashes for step line
                                dashArray: <double>[5, 5],
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Step line chart](images/cartesian-chart-types/dashed_stepline.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the step line series further.

## Range column chart

To render a range column chart, create an instance of [`RangeColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeColumnSeries-class.html) and add to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). 

Since the [`RangeColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeColumnSeries-class.html) requires two Y values for a point, your data should contain high and low values. High and low value specifies the maximum and minimum range of the point. 

* ['highValueMapper'](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/highValueMapper.html) - Field in the data source, which is considered as high value for the data points.
* [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/lowValueMapper.html) - Field in the data source, which is considered as low value for the data points. 

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            RangeColumnSeries<ChartData, double>(
                                dataSource: <ChartData>[
                                    ChartData('Jan', 3, 9),
                                    ChartData('Feb', 4, 11),
                                    ChartData('Mar', 6, 13),
                                    ChartData('Apr', 9, 17),
                                    ChartData('May', 12, 20),
                                ],
                                xValueMapper: (ChartData sales, _) => sales.x,
                                lowValueMapper: (ChartData sales, _) => sales.low,
                                highValueMapper: (ChartData sales, _) => sales.high,
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

![Range column chart](images/cartesian-chart-types/range_column.jpg)

### Data label

In the range column chart when data label is enabled, by default there will be two values displayed namely, high and low, but in the other types of charts, only y value will be displayed.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            RangeColumnSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                lowValueMapper: (ChartData sales, _) => sales.low,
                                highValueMapper: (ChartData sales, _) => sales.high,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true, 
                                    position: CartesianLabelPosition.top
                                ),
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Range column datalabel](images/cartesian-chart-types/range_column_datalabel.jpg)



## Stacked line chart

To render a stacked line chart, create an instance of [`StackedLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedLineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of stacked line series:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) – Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the line.


{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedLineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedLineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                             StackedLineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedLineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked line chart](images/cartesian-chart-types/stacked_line.jpg)

### Grouping series

You can group and stack the similar stacked series types using the [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedLineSeries/groupName.html) property of stacked series. The stacked series that contains the same [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedLineSeries/groupName.html) will be stacked in a single group.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked line grouping](images/cartesian-chart-types/stacked_line_grouping.jpg)

### Display cumulative values

You can show the cumulative data label values using the [`showCumulativeValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showCumulativeValues.html) property. If the series are grouped using [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedLineSeries/groupName.html), then cumulative values will be shown based on grouping.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked line cumulative](images/cartesian-chart-types/stacked_line_cumulative.jpg)

## Stacked area chart

To render a stacked area chart, create an instance of [`StackedAreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of stacked line series:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) – Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.


{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedAreaSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedAreaSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedAreaSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked area](images/cartesian-chart-types/stacked_area.jpg)

### Grouping series

You can group and stack the similar stacked series types using the [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries/groupName.html) property of stacked series. The stacked series that contains the same [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries/groupName.html) will be stacked in a single group.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked area grouping](images/cartesian-chart-types/stacked_area_grouping.jpg)

### Display cumulative values

You can show the cumulative data label values using the [`showCumulativeValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showCumulativeValues.html) property. If the series are grouped using [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries/groupName.html), then cumulative values will be shown based on grouping.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked area cumulative](images/cartesian-chart-types/stacked_area_cumulative.jpg)

## Stacked column chart

To render a stacked column chart, create an instance of [`StackedColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of stacked line series:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) – Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.


{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedColumnSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedColumnSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                             StackedColumnSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedColumnSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked column](images/cartesian-chart-types/stacked_column.jpg)

### Grouping series

You can group and stack the similar stacked series types using the [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries/groupName.html) property of stacked series. The stacked series that contains the same [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries/groupName.html) will be stacked in a single group.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked column grouping](images/cartesian-chart-types/stacked_column_grouping.jpg)

### Display cumulative values

You can show the cumulative data label values using the [`showCumulativeValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showCumulativeValues.html) property. If the series are grouped using [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries/groupName.html), then cumulative values will be shown based on grouping.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked column cumulative](images/cartesian-chart-types/stacked_column_cumulative.jpg)

## Stacked bar chart

To render a stacked bar chart, create an instance of [`StackedBarSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedBarSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of stacked line series:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) – Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedBarSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedBarSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                             StackedBarSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedBarSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked bar](images/cartesian-chart-types/stacked_bar.jpg)

### Grouping series

You can group and stack the similar stacked series types using the [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedBarSeries/groupName.html) property of stacked series. The stacked series that contains the same [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedBarSeries/groupName.html) will be stacked in a single group.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked bar grouping](images/cartesian-chart-types/stacked_bar_grouping.jpg)

### Display cumulative values

You can show the cumulative data label values using the [`showCumulativeValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showCumulativeValues.html) property. If the series are grouped using [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedBarSeries/groupName.html), then cumulative values will be shown based on grouping.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked bar cumulative](images/cartesian-chart-types/stacked_bar_cumulative.jpg)
