---
layout: post
title: Overview of Syncfusion Essential Flutter Chart
description: How to customize the visibility, title, labels, grid lines and tick lines of chart axis
platform: flutter
control: Chart
documentation: ug
---

# Axis customization

## Common axis features

Customization of features such as axis title, labels, grid lines and tick lines are common to all the axes. Each of these features are explained in this section.

### Axis Visibility

Axis visibility can be controlled using the [`isVisible`]() property of axis. Default value of [`isVisible`]() is *true*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: NumericAxis(
                       isVisible: false,
                    ),
                )
            )
        ));
    }

{% endhighlight %}

![Axis visibility](images/getting-started/livechart.png)

### Axis title

The [`title`]() property in axis provides options to customize the text and font of axis title. Axis does not display title by default. The title can be customized using following properties,

* [`text`]() – used to set the title for axis.
* [`textStyle`]() – used to change the text color, size, font family, font style, and font weight.
* [`color`]() – used to change the color of the label.
* [`fontFamily`]() - used to change the font family for the axis title.
* [`fontStyle`]() - used to change the font style for the axis title.
* [`fontWeight`]() - used to change the font weight for the axis title.
* [`fontSize`]() - used to change the font size for the axis title.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: CategoryAxis(
                       title: AxisTitle(
                         text: 'X-Axis',
                         textStyle: ChartTextStyle(
                           color: Colors.red,
                           fontFamily: 'Roboto',
                           fontSize: 16,
                           fontStyle: FontStyle.italic,
                           fontWeight: FontWeight.w300
                         )
                       )
                    ),
                )
            )
        ));
    }

{% endhighlight %}

![Axis title](images/getting-started/livechart.png)

### Axis label rotation

The [`labelRotation`]() property of axis can be used to rotate the axis labels position. Default value of [`labelRotation`]() property is 0d.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                     primaryXAxis: CategoryAxis(
                       labelRotation: 90
                    ), 
                )
            )
        ));
    }

{% endhighlight %}

![Axis label rotation](images/getting-started/livechart.png)

### Axis line customization

[`SfCartesianChart`]() provides support to customize the style of the axis line by defining the [`axisLine`]() property as shown in the below code snippet.

* [`color`]() – used to change the stroke color of axis line.
* [`width`]() – used to change the stroke width of axis line.
* [`dashArray`]() - used to render axis line series with dashes.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                     primaryXAxis: CategoryAxis(
                       axisLine: AxisLine(
                         color: Colors.red,
                         width: 2,
                         dashArray: <double>[5,5]
                       )
                    ), 
                )
            )
        ));
    }

{% endhighlight %}

![Axis line](images/getting-started/livechart.png)

### Axis label customization

The [`labelStyle`]() property in axis provides options to customize the font of axis label. The axis label can be customized using following properties,

* [`labelStyle`]() – used to change the text color, size, font family, font style, and font weight.
* [`color`]() – used to change the color of the axis label.
* [`fontFamily`]() - used to change the font family for the axis label.
* [`fontStyle`]() - used to change the font style for the axis label.
* [`fontWeight`]() - used to change the font weight for the axis label.
* [`fontSize`]() - used to change the font size for the axis label.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                     primaryXAxis: NumericAxis(
                       labelStyle: ChartTextStyle(
                         color: Colors.red,
                         fontFamily: 'Roboto',
                         fontSize: 14,
                         fontStyle: FontStyle.italic,
                         fontWeight: FontWeight.w500
                       )
                    ), 
                )
            )
        ));
    }

{% endhighlight %}

![Axis label](images/getting-started/livechart.png)

### Formatting axis label content

The [`labelFormat`]() property is used to add prefix or suffix with the axis label.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                     primaryYAxis: NumericAxis(
                       labelFormat: '{value}°C'
                    ), 
                )
            )
        ));
    }

{% endhighlight %}

![Axis label format](images/getting-started/livechart.png)

### Label and tick positioning

Axis labels and ticks can be positioned inside or outside the chart area by using [`labelPosition`]() and [`tickPosition`]() properties of ChartAxis. By default labels and ticks will be positioned outside the chart area.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                     primaryXAxis: CategoryAxis(
                       labelPosition: LabelPosition.inside,
                       tickPosition: TickPosition.inside
                     ), 
                    )
            )
        ));
    }

{% endhighlight %}

![Axis label and tick position](images/getting-started/livechart.png)

### Edge label placement

Labels with long text at the edges of an axis may appear partially outside the chart. The [`edgeLabelPlacement`]() property can be used to avoid the partial appearance of labels at the corners. Default value of this property is *none*. Other available options of [`edgeLabelPlacement`]() are shift and hide.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                     primaryXAxis: CategoryAxis(
                       edgeLabelPlacement: EdgeLabelPlacement.shift
                    ), 
                )
            )
        ));
    }

{% endhighlight %}

![Edge label placement](images/getting-started/livechart.png)

### Grid lines customization

The [`width`]() property is used to control the visibility of grid lines. [`majorGridLines`]() and [`minorGridLines`]() properties in axis are used to customize the major grid lines and minor grid lines of an axis respectively. They provide options to change the width, dashes, color of grid lines. By default minor grid lines will not be visible.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                     primaryXAxis: NumericAxis(
                       majorGridLines: MajorGridLines(
                         width: 1,
                         color: Colors.red,
                         dashArray: <double>[5,5]
                       ), minorGridLines: MinorGridLines(
                         width: 1,
                         color: Colors.green,
                         dashArray: <double>[5,5]
                       ),
                       minorTicksPerInterval:2
                     ), 
                  )
            )
        ));
    }

{% endhighlight %}

![Grid lines customization](images/getting-started/livechart.png)

### Tick lines customization

The [`majorTickLines`]() and [`minorTickLines`]() properties in axis are used to customize the major tick lines of an axis and minor tick lines of an axis respectively. They provide options to change the [`width`](), [`size`](), [`color`]() and [`minorTicksPerInterval`]() of tick lines. By default minor tick lines will not be visible.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                     primaryXAxis: NumericAxis(
                      majorTickLines: MajorTickLines(
                        size: 6,
                        width: 2,
                        color: Colors.red
                      ),
                      minorTickLines: MinorTickLines(
                        size: 4,
                        width: 2,
                        color: Colors.blue
                      ),
                      minorTicksPerInterval:2
                    ), 
                )
            )
        ));
    }

{% endhighlight %}

![Tick lines customization](images/getting-started/livechart.png)

### Inversing axis

Axis can be inversed using the [`isInversed`]() property of an axis. Default value of [`isInversed`]() property is *false*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                     primaryXAxis: NumericAxis(
                       isInversed: true
                     ), 
                )
            )
        ));
    }

{% endhighlight %}

![Inversing axis](images/getting-started/livechart.png)

### Placing axes at the opposite side

The [`opposedPosition`]() property of axis can be used to place the axis at the opposite side of its default position. Default value of [`opposedPosition`]() property is *false*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                     primaryXAxis: NumericAxis(
                       opposedPosition: true
                     ), 
                )
            )
        ));
    }

{% endhighlight %}

![Opposed axis](images/getting-started/livechart.png)

### Offset the rendering

The [`plotOffset`]() property is used to offset the rendering of the axis at start and end position. The following code snippet demonstrates to apply the plot offset to both x and y axes.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                     primaryXAxis: NumericAxis(
                       plotOffset: 20
                     ), 
                )
            )
        ));
    }

{% endhighlight %}

![Plot Offset](images/getting-started/livechart.png)

### Maximum number of labels per 100 pixels

By default, a maximum of 3 labels are displayed for each 100 pixels in axis. The maximum number of labels that should be present within 100 pixels length can be customized using the [`maximumLabels`]() property of an axis. This property is applicable only for automatic range calculation and will not work if you set value for **interval** property of an axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                     primaryXAxis: NumericAxis(
                       maximumLabels: 5
                     ), 
                )
            )
        ));
    }

{% endhighlight %}

![Maximum labels](images/getting-started/livechart.png)

### Visible minimum

The [`visibleMinimum`]() property is used to set the minimum visible range of an axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                     primaryXAxis: NumericAxis(
                       visibleMinimum: 2
                     ), 
                )
            )
        ));
    }

{% endhighlight %}

![Visible minimum](images/getting-started/livechart.png)

### Visible maximum

The [`visibleMaximum`]() property is used to set the minimum visible range of an axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                     primaryXAxis: NumericAxis(
                       visibleMaximum: 4
                     ), 
                )
            )
        ));
    }

{% endhighlight %}

![Visible maximum](images/getting-started/livechart.png)

## Smart axis labels

Axis labels may overlap with each other based on chart dimensions and label size. The [`labelIntersectAction`]() property of axis is used to avoid overlapping of axis labels. The default value of the [`labelIntersectAction`]() is [`hide`](). Other available values are [`none`](), [`wrap`](), [`multipleRows`](), [`rotate45`]() and [`rotate90`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                     primaryXAxis: CategoryAxis(
                       labelIntersectAction: AxisLabelIntersectAction.multipleRows
                     ), 
                )
            )
        ));
    }

{% endhighlight %}

![Label intesect action](images/getting-started/livechart.png)

## Multiple axes

User can add n number of axis to the chart. Using the [`xAxisName`]() and [`yAxisName`]() properties of the series, you can bind the horizontal and vertical axis respectively.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                primaryXAxis:
                    CategoryAxis(title: AxisTitle(text: 'Primary X Axis')),
                primaryYAxis:
                    NumericAxis(title: AxisTitle(text: 'Primary Y Axis')),
                //Adding multiple axis
                axes: <ChartAxis>[
              NumericAxis(
                  name: 'xAxis',
                  opposedPosition: true,
                  title: AxisTitle(text: 'Secondary X Axis')),
              NumericAxis(
                  name: 'yAxis',
                  opposedPosition: true,
                  title: AxisTitle(text: 'Secondary Y Axis'))
            ],
                series: <ChartSeries>[
              LineSeries<SalesData, String>(
                  dataSource: [
                    SalesData('Jan', 35),
                    SalesData('Feb', 28),
                    SalesData('Mar', 34),
                    SalesData('Apr', 32),
                    SalesData('May', 40)
                  ],
                  xValueMapper: (SalesData sales, _) => sales.year,
                  yValueMapper: (SalesData sales, _) => sales.sales),
              LineSeries<SalesData, double>(
                  dataSource: [
                    SalesData('Jan', 15, 1),
                    SalesData('Feb', 8, 2),
                    SalesData('Mar', 14, 3),
                    SalesData('Apr', 12, 4),
                    SalesData('May', 20, 5)
                  ],
                  xValueMapper: (SalesData sales, _) => sales.numeric,
                  yValueMapper: (SalesData sales, _) => sales.sales,
                  xAxisName: 'xAxis',
                  yAxisName: 'yAxis')
            ])
            )
        ));
    }

{% endhighlight %}

![Multiple axes](images/getting-started/livechart.png)
