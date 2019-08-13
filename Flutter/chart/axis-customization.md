---
layout: post
title: Axis customization in Syncfusion Flutter Charts
description: Learn how to customize the visibility, title, labels, grid lines and tick lines of chart axis
platform: flutter
control: Chart
documentation: ug
---

# Axis customization

## Common axis features

Customization of features such as axis title, labels, grid lines and tick lines are common to all the axes. Each of these features are explained in this section.

### Axis Visibility

Axis visibility can be controlled using the [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/isVisible.html) property of axis. Default value of [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/isVisible.html) is *true*. When the axis visibility is set to false, then the axis elements like ticks, labels, title, etc will be hidden.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            isVisible: false
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Axis visibility](images/axis-customization/axis_visible.jpg)

### Axis title

The [`title`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/title.html) property in axis provides options to customize the text and font of axis title. Axis does not display title by default. The title can be customized using following properties,

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisTitle/text.html) – used to set the title for axis.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisTitle/textStyle.html) – used to change the text color, size, font family, font style, and font weight.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/color.html) – used to change the color of the label.
* [`fontFamily`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontFamily.html) - used to change the font family for the axis title.
* [`fontStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontStyle.html) - used to change the font style for the axis title.
* [`fontWeight`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontWeight.html) - used to change the font weight for the axis title.
* [`fontSize`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontSize.html) - used to change the font size for the axis title.

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
                                    color: Colors.deepOrange,
                                    fontFamily: 'Roboto',
                                    fontSize: 16,
                                    fontStyle: FontStyle.italic,
                                    fontWeight: FontWeight.w300
                                )
                            )
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Axis title](images/axis-customization/axis_title.jpg)

### Axis label rotation

The [`labelRotation`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelRotation.html) property of axis can be used to rotate the axis labels position. Default value of [`labelRotation`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelRotation.html) property is 0d.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            labelRotation: 90
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Axis label rotation](images/axis-customization/label_rotation.jpg)

### Axis line customization

[`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html) provides support to customize the style of the axis line by defining the [`axisLine`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/axisLine.html) property as shown in the below code snippet.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLine/color.html) – used to change the stroke color of axis line.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLine/width.html) – used to change the stroke width of axis line.
* [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLine/dashArray.html) - used to render axis line series with dashes.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            axisLine: AxisLine(
                                color: Colors.deepOrange,
                                width: 2,
                                dashArray: <double>[5,5]
                            )
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Axis line](images/axis-customization/axis_line_custom.jpg)

### Axis label customization

The [`labelStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelStyle.html) property in axis provides options to customize the font of axis label. The axis label can be customized using following properties,

* [`labelStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelStyle.html) – used to change the text color, size, font family, font style, and font weight.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/color.html) – used to change the color of the axis label.
* [`fontFamily`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontFamily.html) - used to change the font family for the axis label.
* [`fontStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontStyle.html) - used to change the font style for the axis label.
* [`fontWeight`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontWeight.html) - used to change the font weight for the axis label.
* [`fontSize`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontSize.html) - used to change the font size for the axis label.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            labelStyle: ChartTextStyle(
                                color: Colors.deepOrange,
                                fontFamily: 'Roboto',
                                fontSize: 14,
                                fontStyle: FontStyle.italic,
                                fontWeight: FontWeight.w500
                            )
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Axis label](images/axis-customization/label_custom.jpg)

### Formatting axis label content

The [`labelFormat`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/labelFormat.html) property is used to add prefix or suffix with the axis label.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: NumericAxis(
                            labelFormat: '{value}°C'
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

### Label and tick positioning

Axis labels and ticks can be positioned inside or outside the chart area by using [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelPosition.html) and [`tickPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/tickPosition.html) properties of ChartAxis. By default labels and ticks will be positioned outside the chart area.

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
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Axis label and tick position](images/axis-customization/label_tick_poisition.jpg)

### Edge label placement

Labels with long text at the edges of an axis may appear partially outside the chart. The [`edgeLabelPlacement`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/edgeLabelPlacement.html) property can be used to avoid the partial appearance of labels at the corners. Default value of this property is *none*. Other available options of [`edgeLabelPlacement`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/edgeLabelPlacement.html) are shift and hide.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            edgeLabelPlacement: EdgeLabelPlacement.shift
                        ) 
                    )
                )
            )
        );
    }

{% endhighlight %}

![Edge label placement](images/axis-customization/edge_label_placement.jpg)

### Grid lines customization

The [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MajorGridLines/width.html) property is used to control the visibility of grid lines. [`majorGridLines`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/majorGridLines.html) and [`minorGridLines`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/minorGridLines.html) properties in axis are used to customize the major grid lines and minor grid lines of an axis respectively. We have provided options to change the width, dashes, color of grid lines. By default minor grid lines will not be visible.

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
                            ),
                            minorGridLines: MinorGridLines(
                                width: 1,
                                color: Colors.green,
                                dashArray: <double>[5,5]
                            ),
                            minorTicksPerInterval:2
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Grid lines customization](images/axis-customization/gridLine.jpg)

### Tick lines customization

The [`majorTickLines`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/majorTickLines.html) and [`minorTickLines`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/minorTickLines.html) properties in axis are used to customize the major tick lines of an axis and minor tick lines of an axis respectively. We have provided options to change the [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MajorTickLines/width.html), [`size`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MajorTickLines/size.html), [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MajorTickLines/color.html) and [`minorTicksPerInterval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/minorTicksPerInterval.html) of tick lines. By default minor tick lines will not be visible.

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
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Tick lines customization](images/axis-customization/tickLine.jpg)

### Inversing axis

Axis can be inversed using the [`isInversed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/isInversed.html) property of an axis. Default value of [`isInversed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/isInversed.html) property is *false*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            isInversed: true
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Inversing axis](images/axis-customization/inverse.jpg)

### Placing axes at the opposite side

The [`opposedPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/opposedPosition.html) property of axis can be used to place the axis at the opposite side of its default position. Default value of [`opposedPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/opposedPosition.html) property is *false*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            opposedPosition: true
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Opposed axis](images/axis-customization/opposite.jpg)

### Offset the rendering

The [`plotOffset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/plotOffset.html) property is used to offset the rendering of the axis at start and end position. The following code snippet demonstrates to apply the plot offset of an axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            plotOffset: 20
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Plot Offset](images/axis-customization/plot_offset.jpg)

### Maximum number of labels per 100 pixels

By default, a maximum of 3 labels are displayed for each 100 pixels in axis. The maximum number of labels that should be present within 100 pixels length can be customized using the [`maximumLabels`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/maximumLabels.html) property of an axis. This property is applicable only for automatic range calculation and will not work if you set value for **interval** property of an axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            maximumLabels: 3
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

### Visible minimum

The [`visibleMinimum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/visibleMinimum.html) property is used to set the minimum visible range of an axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            visibleMinimum: 2,
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

### Visible maximum

The [`visibleMaximum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/visibleMaximum.html) property is used to set the minimum visible range of an axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            visibleMaximum: 4
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

## Smart axis labels

Axis labels may overlap with each other based on chart dimensions and label size. The [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelIntersectAction.html) property of axis is used to avoid overlapping of axis labels. The default value of the [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelIntersectAction.html) is [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction-class.html). Other available values are [`none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction-class.html), [`wrap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction-class.html), [`multipleRows`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction-class.html), [`rotate45`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction-class.html) and [`rotate90`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction-class.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            labelIntersectAction: AxisLabelIntersectAction.multipleRows
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Label intesect action](images/axis-customization/smartLabels.jpg)

## Multiple axes

User can add n number of axis to the chart. Using the [`xAxisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/xAxisName.html) and [`yAxisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/yAxisName.html) properties of the series, you can bind the horizontal and vertical axis respectively.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            title: AxisTitle(text: 'Primary X Axis')
                        ),
                        primaryYAxis: NumericAxis(
                            title: AxisTitle(
                                text: 'Primary Y Axis'
                            )
                        ),
                        //Adding multiple axis
                        axes: <ChartAxis>[
                            NumericAxis(
                                name: 'xAxis',
                                opposedPosition: true,
                                interval:1,
                                minimum: 0,
                                maximum: 5,
                                title: AxisTitle(
                                    text: 'Secondary X Axis'
                                )
                            ),
                            NumericAxis(
                                name: 'yAxis',
                                opposedPosition: true,
                                title: AxisTitle(
                                    text: 'Secondary Y Axis'
                                )
                            )
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
                                yValueMapper: (SalesData sales, _) => sales.sales
                            ),
                            LineSeries<SalesData, double>(
                                dataSource: [
                                    SalesData('Jan', 15, 1),
                                    SalesData('Feb', 11, 2),
                                    SalesData('Mar', 14, 3),
                                    SalesData('Apr', 12, 4),
                                ],
                                xValueMapper: (SalesData sales, _) => sales.numeric,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                xAxisName: 'xAxis',
                                yAxisName: 'yAxis'
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Multiple axes](images/axis-customization/multiple_axis.jpg)