---
layout: post
title: Syncfusion Cartesian Chart types
description: What are the different types of Charts available in Essential Flutter Chart.
platform: flutter
control: Chart
documentation: ug
---

# Cartesian chart types

## Line chart

To render a line chart, create an instance of [`LineSeries`]() and add to the [`series`]() collection property of [`SfCartesianChart`](). You can use the following properties to customize the appearance.

* [`color`]() – used to change the color of the line.
* [`opacity`]() - used to control the transparency of the chart series.
* [`width`]() – used to change the stroke width of the line.

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
                child:SfCartesianChart(series: <ChartSeries>[
                    LineSeries<SalesData, double>(
                        dataSource: chartData,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales),
                ])
            )
        ));
    }

    class SalesData {
     SalesData(this.year, this.sales);
        final double year;
        final double sales;
    }

{% endhighlight %}

![Line chart](images/getting-started/livechart.png)

### Dashed line

The [`dashArray`]() property of the [`LineSeries`]() is used to render line series with dashes.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                series: <ChartSeries>[
                 LineSeries<SalesData, String>(
                  dataSource: chartData,
                  dashArray: <double>[5,5],
                  xValueMapper: (SalesData sales, _) => sales.year,
                  yValueMapper: (SalesData sales, _) => sales.sales),
                ])
            )
        ));
    }

{% endhighlight %}

![Dashed line chart](images/getting-started/livechart.png)

### Multi-colored line

To render a multicolored line series, map the individual colors to the data by using the [`pointColorMapper`]() property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
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
                  pointColorMapper:(SalesData sales, _) => sales.segmentColor,
                  xValueMapper: (SalesData sales, _) => sales.year,
                  yValueMapper: (SalesData sales, _) => sales.sales),
            ])
            )
        ));
    }

    class SalesData {
        SalesData(this.year, this.sales, this.segmentColor);
            final double year;
            final double sales;
            final Color segmentColor;
    }

{% endhighlight %}

![Multi-colored line](images/getting-started/livechart.png)

## Area chart

To render an area chart, create an instance of [`AreaSeries`]() and add to the [`series`]() collection property of [`SfCartesianChart`](). You can use the following properties to customize the appearance.

* [`color`]() – used to change the color of the series.
* [`opacity`]() - used to control the transparency of the chart series.
* [`borderWidth`]() – used to change the stroke width of the series.
* [`borderColor`]() – used to change the stroke color of the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                 AreaSeries<SalesData, double>(
                    dataSource: chartData,
                    xValueMapper: (SalesData sales, _) => sales.year,
                    yValueMapper: (SalesData sales, _) => sales.sales),
                ])
            )
        ));
    }

{% endhighlight %}

![Area chart](images/getting-started/livechart.png)

###	Border customization

The borders of the area chart can be customized using the [`borderMode`]() property. The default value of [`borderMode`]() property is [`top`](). The other values are [`all`]() and [`excludeBottom`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                 AreaSeries<SalesData, double>(
                    dataSource: chartData,
                    borderMode: AreaBorderMode.excludeBottom,
                    xValueMapper: (SalesData sales, _) => sales.year,
                    yValueMapper: (SalesData sales, _) => sales.sales),
                ])
            )
        ));
    }

{% endhighlight %}

![Area border](images/getting-started/livechart.png)

## Spline chart

To render a spline chart, create an instance of [`SplineSeries`]() and add to the [`series`]() collection property of [`SfCartesianChart`](). You can use the following properties to customize the spline segment appearance.

* [`color`]() – used to change the color of the series.
* [`opacity`]() - used to control the transparency of the chart series.
* [`width`]() – used to change the stroke width of the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    SplineSeries<SalesData, double>(
                        dataSource: chartData,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales),
                ])
            )
        ));
    }

{% endhighlight %}

![Spline border](images/getting-started/livechart.png)

### Dashed spline

The [`dashArray`]() property of the [`SplineSeries`]() is used to render spline series with dashes.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                series: <ChartSeries>[
                 SplineSeries<SalesData, String>(
                  dataSource: chartData,
                  dashArray: <double>[5,5],
                  xValueMapper: (SalesData sales, _) => sales.year,
                  yValueMapper: (SalesData sales, _) => sales.sales),
                ])
            )
        ));
    }

{% endhighlight %}

![Dashed spline chart](images/getting-started/livechart.png)

###	Spline rendering types

The [`splineType`]() allows you to change the spline curve in series. The following types are used in [`SplineSeries`]()

* natural
* monotonic
* cardinal
* clamped

By default [`splineType`]() value is [`natural`]().

The following code shows how to set the [`splineType`]() value as [`cardinal`](). When you set the cardinal type, then you can specify the desired line tension of the [`cardinal`]() spline using [`cardinalSplineTension`]() property which ranges from 0 to 1.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    SplineSeries<SalesData, double>(
                        dataSource: chartData,
                        splineType: SplineType.cardinal,
                        cardinalSplineTension: 0.9,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales),
                ])
            )
        ));
    }

{% endhighlight %}

![Spline type](images/getting-started/livechart.png)

## Column chart

To render a column chart, create an instance of [`ColumnSeries`]() and add to the [`series`]() collection property of [`SfCartesianChart`](). You can use the following properties to customize the appearance.

* [`color`]() – used to change the color of the series.
* [`opacity`]() - used to control the transparency of the chart series.
* [`borderWidth`]() – used to change the stroke width of the series.
* [`borderColor`]() – used to change the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    ColumnSeries<SalesData, double>(
                        dataSource: chartData,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales),
                    ])
            )   
        ));
    }

{% endhighlight %}

![Column chart](images/getting-started/livechart.png)

### Side by side series placement

By default, all the column series which has the same x and y axes are placed side by side in a chart. If you want place the series one over the other (overlapped), set the [`enableSideBySideSeriesPlacement`]() property of [`SfCartesianChart`]() to *false* and configure the [`width`]() property to differentiate the series. The following code snippet and screenshot illustrate the overlapped placement of column series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        final List<SalesData> chartData = [
            SalesData(2010, 35, 23),
            Salesata(2011, 38, 49),
            SalesData(2012, 34, 12),
            SalesData(2013, 52, 33),
            SalesData(2014, 40, 30)
        ];
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
              enableSideBySideSeriesPlacement: false,
                series: <ChartSeries>[
              ColumnSeries<SalesData, double>(
                dataSource: chartData,
                xValueMapper: (SalesData sales, _) => sales.year,
                yValueMapper: (SalesData sales, _) => sales.sales,
              ),
              ColumnSeries<SalesData, double>(
                opacity: 0.9,
                width: 0.4,
                dataSource: chartData,
                xValueMapper: (SalesData sales, _) => sales.year,
                yValueMapper: (SalesData sales, _) => sales.segmentColor
              ),
            ])
          )   
        ));
    }

{% endhighlight %}

![Column side by side placement](images/getting-started/livechart.png)

### Column width and spacing

The [`spacing`]() property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The [`width`]() property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    ColumnSeries<SalesData, double>(
                        dataSource: chartData,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales,
                        width: 0.8,
                        spacing: 0.2),
            ])
          )   
        ));
    }

{% endhighlight %}

![Column width and spacing](images/getting-started/livechart.png)

### Rounded corners

The [`borderRadius`]() property is used to add the rounded corners to the rectangle.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    ColumnSeries<SalesData, double>(
                        dataSource: chartData,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales,
                        borderRadius: BorderRadius.all(Radius.circular(15))),
                ])
          )   
        ));
    }

{% endhighlight %}

![Rounded corners](images/getting-started/livechart.png)


### Track customization

Renders column with track. Track is a rectangular bar rendered from the start to the end of the axis. Column series will be rendered above the track. The [`isTrackVisible`]() property is used to enable the track.You can use the following properties to customize the appearance.

* [`trackColor`]() – used to change the color of the track.
* [`trackBorderWidth`]() – used to change the stroke width of the track.
* [`trackBorderColor`]() – used to change the stroke color of the track.
* [`trackPadding`]() - used to add padding to the track.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    ColumnSeries<SalesData, double>(
                        dataSource: chartData,
                        isTrackVisible: true ,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales),
                ])
          )   
        ));
    }

{% endhighlight %}

![Track](images/getting-started/livechart.png)

## Bar chart

To render a column chart, create an instance of [`BarSeries`]() and add to the [`series`]() collection property of [`SfCartesianChart`](). You can use the following properties to customize the appearance.

* [`color`]() – used to change the color of the series.
* [`opacity`]() - used to control the transparency of the chart series.
* [`borderWidth`]() – used to change the stroke width of the series.
* [`borderColor`]() – used to change the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    BarSeries<SalesData, double>(
                        dataSource: chartData,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales),
                    ])
            )   
        ));
    }

{% endhighlight %}

![Bar chart](images/getting-started/livechart.png)

### Column width and spacing

The [`spacing`]() property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The [`width`]() property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    BarSeries<SalesData, double>(
                        dataSource: chartData,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales,
                        width: 0.8,
                        spacing: 0.2),
            ])
          )   
        ));
    }

{% endhighlight %}

![Bar width and spacing](images/getting-started/livechart.png)

### Rounded corners

The [`borderRadius`]() property is used to add the rounded corners to the rectangle.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    BarSeries<SalesData, double>(
                        dataSource: chartData,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales,
                        borderRadius: BorderRadius.all(Radius.circular(15))),
                ])
          )   
        ));
    }

{% endhighlight %}

![Bar rounded corners](images/getting-started/livechart.png)


### Track customization

You can render the bar chart with track. Track is a rectangular bar rendered from the start to the end of the axis. Bar series will be rendered above the track. The [`isTrackVisible`]() property is used to enable the track.You can use the following properties to customize the appearance.

* [`trackColor`]() – used to change the color of the track.
* [`trackBorderWidth`]() – used to change the stroke width of the track.
* [`trackBorderColor`]() – used to change the stroke color of the track.
* [`trackPadding`]() - used to add padding to the track.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    BarSeries<SalesData, double>(
                        dataSource: chartData,
                        isTrackVisible: true ,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales),
                ])
          )   
        ));
    }

{% endhighlight %}

![Bar track](images/getting-started/livechart.png)

## Bubble chart

To render a bubble chart, create an instance of [`BubbleSeries`]() and add to the [`series`]() collection property of [`SfCartesianChart`]().

Bubble chart requires 3 fields (X, Y and Size) to plot a point. Here [`sizeValueMapper`]() is used to map the size of each bubble segment from data source.

* [`color`]() – used to change the color of the series.
* [`opacity`]() - used to control the transparency of the chart series.
* [`borderColor`]() – used to change the stroke width of the series.
* [`borderWidth`]() – used to change the stroke color of the series.

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
                child:SfCartesianChart(series: <ChartSeries>[
                    BubbleSeries<ChartData, double>(
                        dataSource: chartData,
                        sizeValueMapper: (ChartData sales, _) => sales.size,
                        xValueMapper: (ChartData sales, _) => sales.x,
                        yValueMapper: (ChartData sales, _) => sales.y),
                ])
          )   
        ));
    }

    class ChartData {
        ChartData(this.x, this.y, this.size);
            final double x;
            final double y;
            final double size;
    }

{% endhighlight %}

![Bubble chart](images/getting-started/livechart.png)

### Change min and max radius of bubble

The [`minimumRadius`]() property is used to change the minimum size of the series and [`maximumRadius`]() property is used to change the maximum size of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    BubbleSeries<ChartData, double>(
                        dataSource: chartData,
                        sizeValueMapper: (ChartData sales, _) => sales.size,
                        minimumRadius:9,
                        maximumRadius: 15,
                        xValueMapper: (ChartData sales, _) => sales.x,
                        yValueMapper: (ChartData sales, _) => sales.y),
                ])
          )   
        ));
    }

{% endhighlight %}

![Bubble size](images/getting-started/livechart.png)

## Scatter chart

To render a scatter chart, create an instance of [`ScatterSeries`]() and add to the [`series`]() collection property of [`SfCartesianChart`](). You can use the following properties to customize the scatter segment appearance.

* [`color`]() – used to change the color of the series.
* [`opacity`]() - used to control the transparency of the chart series.
* [`borderWidth`]() – used to change the stroke width of the series.
* [`borderColor`]() – used to change the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    ScatterSeries<ChartData, double>(
                        dataSource: chartData,
                        xValueMapper: (ChartData sales, _) => sales.x,
                        yValueMapper: (ChartData sales, _) => sales.y),
                ])
          )   
        ));
    }

{% endhighlight %}

![Scatter chart](images/getting-started/livechart.png)

###	Change shape and size of the scatter

The [`shape`]() property is used to change the rendering shape of scatter series. The available shapes are [`circle`](), [`rectangle`](), [`pentagon`](), [`verticalLine`](), [`horizontalLine`](), [`diamond`](), [`triangle`](), [`image`]() and [`invertedTriangle`](). If [`image`]() shape is specified, then you can assign the image using [`imageUrl`]() property.

The [`height`]() and [`width`]() properties of [`markerSettings`]() are used to change the height and width of the scatter series respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    ScatterSeries<ChartData, double>(
                        dataSource: chartData,
                        xValueMapper: (ChartData sales, _) => sales.x,
                        yValueMapper: (ChartData sales, _) => sales.y,
                        markerSettings: MarkerSettings(
                            height: 15,
                            width: 15,
                            shape: DataMarkerType.diamond,
                )),
            ])
          )   
        ));
    }

{% endhighlight %}

![Scatter shape](images/getting-started/livechart.png)

## Step line chart

To render a step line chart, create an instance of [`StepLineSeries`]() and add to the [`series`]() collection property of [`SfCartesianChart`](). You can use the following properties to customize the spline segment appearance.

* [`color`]() – used to change the color of the line.
* [`opacity`]() - used to control the transparency of the chart series.
* [`width`]() – used to change the stroke width of the line.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    StepLineSeries<ChartData, double>(
                        dataSource: chartData,
                        xValueMapper: (ChartData sales, _) => sales.x,
                        yValueMapper: (ChartData sales, _) => sales.y,
                    ),
                ])
          )   
        ));
    }

{% endhighlight %}

![Step line chart](images/getting-started/livechart.png)

### Dashed line

The [`dashArray`]() property of the [`StepLineSeries`]() is used to render step line series with dashes.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    StepLineSeries<ChartData, double>(
                        dataSource: chartData,
                        dashArray: <double>[5,5],
                        xValueMapper: (ChartData sales, _) => sales.x,
                        yValueMapper: (ChartData sales, _) => sales.y,
                    ),
                ])
          )   
        ));
    }

{% endhighlight %}

![Step line chart](images/getting-started/livechart.png)

## Fast line chart

[`FastLineSeries`]() is a line chart, but it loads faster than [`LineSeries`](). You can use this when there are large number of points to be loaded in chart. To render a fast line chart, create an instance of [`FastLineSeries`]() and add to the [`series`]() collection property of [`SfCartesianChart`](). You can use the following properties to customize the fast line segment appearance.

* [`color`]() – used to change the color of the line.
* [`opacity`]() - used to control the transparency of the chart series.
* [`width`]() – used to change the stroke width of the line.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <ChartSeries>[
                    FastLineSeries<SalesData, double>(
                        dataSource: chartData,
                        xValueMapper: (SalesData sales, _) => sales.year,
                        yValueMapper: (SalesData sales, _) => sales.sales),
                ])
            )
        ));
    }


{% endhighlight %}

![Fast line chart](images/getting-started/livechart.png)