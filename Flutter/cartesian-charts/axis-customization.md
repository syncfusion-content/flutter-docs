---
layout: post
title: Axis customization in Flutter Cartesian Charts | Syncfusion 
description: Learn here all about Axis customization feature of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Cartesian Charts
documentation: ug
---

# Axis customization in Flutter Cartesian Charts (SfCartesianChart)

## Common axis features

Customization of features such as axis title, labels, grid lines and tick lines are common to all the axes. Each of these features are explained in this section.

### Axis Visibility

Axis visibility can be controlled using the [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/isVisible.html) property of axis. Default value of [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/isVisible.html) is `true`. When the axis visibility is set to false, then the axis elements like ticks, labels, title, etc will be hidden.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            // X axis is hidden now
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

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisTitle/text.html) - used to set the title for axis.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisTitle/textStyle.html) - used to change the text color, size, font family, font style, and font weight.
* [`color`](https://api.flutter.dev/flutter/painting/TextStyle/color.html) - used to change the color of the label.
* [`fontFamily`](https://api.flutter.dev/flutter/painting/TextStyle/fontFamily.html) - used to change the font family for the axis title.
* [`fontStyle`](https://api.flutter.dev/flutter/painting/TextStyle/fontStyle.html) - used to change the font style for the axis title.
* [`fontWeight`](https://api.flutter.dev/flutter/painting/TextStyle/fontWeight.html) - used to change the font weight for the axis title.
* [`fontSize`](https://api.flutter.dev/flutter/painting/TextStyle/fontSize.html) - used to change the font size for the axis title.

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
                                textStyle: TextStyle(
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

The [`labelRotation`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelRotation.html) property of axis can be used to rotate the axis labels position. Default value of [`labelRotation`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelRotation.html) property is 0.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            // Axis labels will be rotated to 90 degree
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

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLine/color.html) - used to change the stroke color of axis line.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLine/width.html) - used to change the stroke width of axis line.
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

* [`labelStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelStyle.html) - used to change the text color, size, font family, font style, and font weight.
* [`color`](https://api.flutter.dev/flutter/painting/TextStyle/color.html) - used to change the color of the axis label.
* [`fontFamily`](https://api.flutter.dev/flutter/painting/TextStyle/fontFamily.html) - used to change the font family for the axis label.
* [`fontStyle`](https://api.flutter.dev/flutter/painting/TextStyle/fontStyle.html) - used to change the font style for the axis label.
* [`fontWeight`](https://api.flutter.dev/flutter/painting/TextStyle/fontWeight.html) - used to change the font weight for the axis label.
* [`fontSize`](https://api.flutter.dev/flutter/painting/TextStyle/fontSize.html) - used to change the font size for the axis label.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            labelStyle: TextStyle(
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

### Axis border customization

The color and width of the axis border can be customized with [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/borderColor.html) and [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/borderWidth.html) properties respectively. The border types can be changed using the [`axisBorderType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/axisBorderType.html) property and the default value is [`AxisBorderType.rectangle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisBorderType.html). Another value of [`axisBorderType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/axisBorderType.html) is [`AxisBorderType.withoutTopAndBottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisBorderType.html).

* [`AxisBorderType.rectangle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisBorderType.html) - Renders the border as a rectangle around a label.
* [`AxisBorderType.withoutTopAndBottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisBorderType.html) - Renders the border without the top and bottom of a rectangle.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = <ChartData>[
        ChartData(1, 24),
        ChartData(2, 20),
        ChartData(3, 35),
        ChartData(4, 27),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];
      return Scaffold(
        body: SfCartesianChart(
          primaryXAxis: NumericAxis(
            borderWidth: 1.0,
            borderColor: Colors.blue
          ),
          primaryYAxis: NumericAxis(
            borderWidth: 1.0, 
            borderColor: Colors.blue
          ),
          series: <ChartSeries<ChartData, int>>[
            LineSeries<ChartData, int>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
            )
          ]
        )
      );
    }  

    class ChartData {
      ChartData(this.x, this.y);
        final int x;
        final int y;
    }

{% endhighlight %}

![Axis border customization](images/axis-customization/axis_border_customization.jpg)

### Axis animation

The axis animation can be enabled using the `enableAxisAnimation` property of the chart. It defaults to `false` and this is applicable for all the primary and secondary axis in the chart.

On setting the `enableAxisAnimation` property to true, the axis elements like grid lines, tick lines, and labels will be animated when the axis range is changed dynamically. Axis visible range will be changed while zooming, panning, or while updating the data points.

{% highlight dart %}

    Widget build(BuildContext context) {
        return Container(
            child: SfCartesianChart(
                enableAxisAnimation: true,
            )
        );
    }

{% endhighlight %}

![Axis label](images/axis-customization/animatedAxis.gif)

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
                            // '°C' will be append to all the labels in Y axis
                            labelFormat: '{value}°C'
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

Also refer [number format](./axis-types#formatting-the-labels) and [date format](./axis-types#formatting-the-labels-1) for formatting the labels further.

>**Note**: You must import [`intl`](https://pub.dev/packages/intl) package for formatting axis label using the [`NumberFormat`](https://pub.dev/documentation/intl/latest/intl/NumberFormat-class.html) class and  [`date Format`](https://pub.dev/documentation/intl/latest/intl/DateFormat-class.html) class.

### Label and tick positioning

Axis labels and ticks can be positioned inside or outside the chart area by using [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelPosition.html) and [`tickPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/tickPosition.html) properties of ChartAxis. By default labels and ticks will be positioned outside the chart area.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            labelPosition: ChartDataLabelPosition.inside,
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

Labels with long text at the edges of an axis may appear partially outside the chart. The [`edgeLabelPlacement`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/edgeLabelPlacement.html) property can be used to avoid the partial appearance of labels at the corners. Default value of this property is [`EdgeLabelPlacement.none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EdgeLabelPlacement.html). Other available options of [`edgeLabelPlacement`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/edgeLabelPlacement.html) are shift and hide. [`EdgeLabelPlacement.shift`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EdgeLabelPlacement.html) option will move the edge labels inside the axis bounds, where the [`EdgeLabelPlacement.hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EdgeLabelPlacement.html) option will hides the edge labels.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            // Edge labels will be shifted
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
                    child: SfCartesianChart(
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

The [`majorTickLines`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/majorTickLines.html) and [`minorTickLines`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/minorTickLines.html) properties in axis are used to customize the major tick lines of an axis and minor tick lines of an axis respectively. We have provided options to customize the [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MajorTickLines/width.html), [`size`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MajorTickLines/size.html), [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MajorTickLines/color.html) and [`minorTicksPerInterval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/minorTicksPerInterval.html) of tick lines. By default minor tick lines will not be visible.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
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

Axis can be inversed using the [`isInversed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/isInversed.html) property of an axis. Default value of [`isInversed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/isInversed.html) property is `false`.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            // X axis will be inversed
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

The [`opposedPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/opposedPosition.html) property of axis can be used to place the axis at the opposite side of its default position. Default value of [`opposedPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/opposedPosition.html) property is `false`.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            // X axis will be opposed
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

The [`plotOffset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/plotOffset.html) property is used to offset the rendering of the axis at start and end position. The following code snippet demonstrates how to apply the plot offset of an axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            // 20 logical pixels gap will be left at the start and end of the x axis
                            plotOffset: 20
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Plot Offset](images/axis-customization/plot_offset.jpg)

### Maximum number of labels per 100 logical pixels

By default, a maximum of 3 labels are displayed for each 100 logical pixels in axis. The maximum number of labels that should be present within 100 logical pixels length can be customized using the [`maximumLabels`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/maximumLabels.html) property of an axis. This property is applicable only for automatic range calculation and will not work if you set value for `interval` property of an axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
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

The [`visibleMinimum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/visibleMinimum.html) property is used to set the minimum visible range of an axis. When panning is enabled, you can pan to the actual minimum range of an axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            visibleMinimum: 2
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

Also refer [`minimum`](./axis-types) and [`maximum`](./axis-types) range of an axis.

### Visible maximum

The [`visibleMaximum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/visibleMaximum.html) property is used to set the minimum visible range of an axis. When panning is enabled, you can pan to the actual maximum range of an axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
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

Axis labels may overlap with each other based on chart dimensions and label size. The [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelIntersectAction.html) property of axis is used to avoid overlapping of axis labels. The default value of the [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelIntersectAction.html) is [`AxisLabelIntersectAction.hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction.html). Other available values are [`AxisLabelIntersectAction.none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction.html), [`AxisLabelIntersectAction.wrap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction.html), [`AxisLabelIntersectAction.multipleRows`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction.html), [`AxisLabelIntersectAction.rotate45`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction.html) and [`AxisLabelIntersectAction.rotate90`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelIntersectAction.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            // Axis labels will be placed in multiple rows, if it is intersected
                            labelIntersectAction: AxisLabelIntersectAction.multipleRows
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Label intesect action](images/axis-customization/smartLabels.jpg)

## Axis crossing

Axis can be positioned anywhere in the plot area using the [`crossesAt`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/crossesAt.html) property. This property specifies where the horizontal axis should intersect or cross the vertical axis, or vice-versa. The default value of the [`crossesAt`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/crossesAt.html) property is `null`.

{% highlight dart %} 
   
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            crossesAt: 0
                        ),
                        primaryYAxis:NumericAxis(
                            crossesAt: 0
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Axis crossing](images/axis-customization/axis_crossing.jpg)

### Crossing in category axis

For crossing in horizontal category axis, index value should be provided for the [`crossesAt`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/crossesAt.html) property of vertical axis.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis:CategoryAxis(),
                        primaryYAxis:NumericAxis(
                            crossesAt: 3
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Category crossing](images/axis-customization/category_crossing.jpg)

### Crossing in date-time axis

For crossing in horizontal date-time axis, date value should be provided for the [`crossesAt`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/crossesAt.html) property of vertical axis.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        primaryYAxis:NumericAxis(
                            crossesAt: DateTime(2018, 4, 1)
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}  

![Datetime crossing](images/axis-customization/datetime_crossing.jpg)

### Positioning the axis labels when crossing

The [`placeLabelsNearAxisLine`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/placeLabelsNearAxisLine.html) property is used to determine whether the axis labels of crossed axis should be placed near to the axis line or not. The default value of [`placeLabelsNearAxisLine`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/placeLabelsNearAxisLine.html) property is `false`.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(
                            placeLabelsNearAxisLine: false
                        ),
                        primaryYAxis:NumericAxis(
                            placeLabelsNearAxisLine: false
                        )
                    )
                )
            )
        );
    } 
    
{% endhighlight %}

![Datetime crossing](images/axis-customization/axis_crossing_labels.jpg)

## Plot bands

Plot bands are also known as strip lines, which are used to shade the different ranges in plot area with different colors to improve the readability of the chart. You can also add a text to indicate what that particular region indicates. You can enable the plot bands to be drawn repeatedly at regular intervals. This will be useful when you need to mark an event that occurs recursively along the timeline of the chart.

Since plot bands are drawn based on the axis, you have to add plot bands using the [`plotBands`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/plotBands.html) property of the respective axis. You can also add multiple plot bands to an axis.

The following properties are used to configure the plot bands:

* [`size`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/size.html) - changes how long plot band should be expanded. This is applicable only when end is not specified.
* [`sizeType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/sizeType.html) - changes the date-time unit of the value specified in the size property. The values can be year, month, day, hour, minute, second, and millisecond.
* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/text.html) - changes the text of the plot band.
* [`textAngle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/textAngle.html) - changes the angle of the text.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/color.html) - changes the color of the plot band.
* [`gradient`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/gradient.html) - applies gradient color for plot band.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/opacity.html) - changes the opacity of the plot band.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/borderWidth.html) - changes the stroke width of the plot band.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/borderColor.html) - changes the stroke color of the plot band.
* [`horizontalTextAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/horizontalTextAlignment.html) - aligns the text horizontally.
* [`verticalTextAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/verticalTextAlignment.html) - aligns the text vertically.
* [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/isVisible.html) - changes the visibility of the plot band in chart axis.
* [`shouldRenderAboveSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/shouldRenderAboveSeries.html) - changes the rendering order of the plot band.
* [`isRepeatable`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/isRepeatable.html) - specifies the plot band need to be repeated in specified interval.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/Legend/textStyle.html) - customizes the text style of plot band.

![Plotband](images/axis-customization/plotband.jpg)

### Add plot band for category axis

Plot band can be added to the category axis by specifying index values to the [`start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/start.html) and [`end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/end.html) properties.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis:CategoryAxis(
                            plotBands: <PlotBand>[
                            PlotBand(
                            isVisible: true,
                            start: 1,
                            end: 2,
                        ),
                    )
                )
            )
        );
    }

{% endhighlight %}    

![Category plotband](images/axis-customization/category_plotband.jpg)

### Add plot band for date-time axis

Plot band can be added to the date-time axis by specifying date values to the [`start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/start.html) and [`end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/end.html) properties.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis:DateTimeAxis(
                            plotBands: <PlotBand>[
                            PlotBand(
                            isVisible: true,
                            start: DateTime(2018, 2, 1),
                            end:  DateTime(2018, 4, 1),
                        ),
                     ],
                  )
              )
          )
        )  
      );
    }

{% endhighlight %}

![DateTime plotband](images/axis-customization/datetime_plotband.jpg)

### Recursive plot band

This feature is used to enable the plot bands to be drawn repeatedly at the regular intervals. This will be useful when you need to mark an event that occurs recursively along the timeline of the chart. The following properties are used to configure this feature:

* [`repeatEvery`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/repeatEvery.html) - changes the frequency of the plot band being repeated.
* [`repeatUntil`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/repeatUntil.html) - specifies the end value at which point strip line has to stop repeating.

The following code snippet and screenshot demonstrate this feature by highlighting weekends.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis:DateTimeAxis(
                            plotBands: <PlotBand>[
                            PlotBand(
                            isVisible: true,
                            isRepeatable: true,
                            repeatEvery: 2,
                            size: 1,
                            sizeType: DateTimeIntervalType.months,
                            repeatUntil: DateTime(2018, 6, 1),
                            ),
                        ],
                    )
                )
            )
         ) 
      );
    }

{% endhighlight %}

![Recursive plotband](images/axis-customization/recursive_plotband.jpg)

### Segmented plot band

Typically, if you draw a plot band for a vertical axis, the height of the plot band is determined by the start and end properties, and the end of the plot band is equivalent to the end of its associated horizontal axis, i.e., plot band is drawn horizontally to the entire stretch of its associated horizontal axis. Similarly, for horizontal axis, width is determined by the Start and Width properties, and vertically, it is drawn to the entire stretch of the associated vertical axis.

Suppose, you need to draw a plot band that should not stretch along its associated axis, you have to set the [`associatedAxisStart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/associatedAxisStart.html) and [`associatedAxisEnd`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/associatedAxisEnd.html) properties. The values provided in these two properties correspond to its associated axis specified by the [`associatedAxisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/associatedAxisName.html) property in the axis.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis:DateTimeAxis(
                            plotBands: <PlotBand>[
                            PlotBand(
                            isVisible: true,
                            start: DateTime(2018,2,1),
                            end: DateTime(2018,6,1),
                            associatedAxisStart: 8,
                            associatedAxisEnd: 15,
                            shouldRenderAboveSeries: true,
                            color: const Color.fromRGBO(224, 155, 0, 1)
                        ),
                      ]
                    )
                )
            )
        )
      );
    }

{% endhighlight %}

![Segement plotband](images/axis-customization/segment_plotband.jpg)

### Plot line

When you specify the same value for both [`start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/start.html) and [`end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/end.html), it will draw a line. You can customize the line using the  [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/borderWidth.html) and [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/borderColor.html) properties.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
               child: SfCartesianChart(
                    primaryXAxis: NumericAxis(
                      plotBands: <PlotBand>[
                        PlotBand(
                          isVisible: true,
                          start: 13,
                          end: 13,
                          borderWidth: 2,
                        borderColor: Colors.black,
                               )
                           ]
                         )
                      )
                    )
                )
            );  
        }

{% endhighlight %}

![plotband_line](images/axis-customization/plotband_line.png)

### Plot band padding

Padding to the plot band text can be added using the [`verticalTextPadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/verticalTextPadding.html) or [`horizontalTextPadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/horizontalTextPadding.html) properties. The [`verticalTextPadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/verticalTextPadding.html) is used to move the plot band text vertically and [`horizontalTextPadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/horizontalTextPadding.html) is used to move the plot band text horizontally.

These properties takes pixel or percentage value. For pixel input should be like `10px` and for percentage input should be like `10%`. If no suffix is specified (`10`), it will be considered as pixel value. Percentage value refers to the overall width of the chart. i.e 100% is equal to the width of the chart. 

This is applicable for both vertical and horizontal axis. Positive value for this property moves the text to right and negative value moves to left.

If [`verticalTextAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/verticalTextAlignment.html) or [`horizontalTextAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PlotBand/horizontalTextAlignment.html) is specified, text padding will be calculated from that modified position. Defaults to `null`.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Container(
        child: SfCartesianChart(
            primaryXAxis: NumericAxis(
                plotBands: <PlotBand>[
                    PlotBand(
                        verticalTextPadding:'5%',
                        horizontalTextPadding: '5%',
                        text: 'Average',
                        textAngle: 0,
                        start: 10,
                        end: 10, 
                        textStyle: TextStyle(color: Colors.deepOrange, fontSize: 16),
                        borderColor: Colors.red,
                        borderWidth: 2
                    )
                ]
            )
        )
      );
    }

{% endhighlight %}

![plotband padding](images/axis-customization/plotband_padding.png)

## Multiple axes

By default, the chart is rendered with primary x axis and primary y axis. But, the users can add n number of axis to the chart. An additional horizontal or vertical axis can be added to the chart using the [`axes`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/axes.html) property, and then you can associate it to a series by specifying the name of the axis to the [`xAxisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/xAxisName.html) or [`yAxisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/yAxisName.html) property in the series.

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
                        // adding multiple axis
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
                            LineSeries<ChartData, String>(
                                dataSource: [
                                    ChartData('Jan', 35),
                                    ChartData('Feb', 28),
                                    ChartData('Mar', 34),
                                    ChartData('Apr', 32),
                                    ChartData('May', 40)
                                ],
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y
                            ),
                            LineSeries<ChartData, String>(
                                dataSource: [
                                    ChartData('Jan', 15, 1),
                                    ChartData('Feb', 11, 2),
                                    ChartData('Mar', 14, 3),
                                    ChartData('Apr', 12, 4),
                                ],
                                xValueMapper: (ChartData data, _) => sales.numeric,
                                yValueMapper: (ChartData data, _) => data.y,
                                xAxisName: 'xAxis',
                                yAxisName: 'yAxis'
                            )
                        ]
                    )
                )
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.y, [this.numeric]);
        final String x;
        final double? y;
        final double? numeric;
    }

{% endhighlight %}

![Multiple axes](images/axis-customization/multiple_axis.jpg)

## Axis label alignment

The position of axis label can be aligned using the [`labelAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelAlignment.html) property.The following options are available in axis label alignment.

* [`LabelAlignment.start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelAlignment.html) - if it is a horizontal axis, aligns the labels before the gridline and if it is a vertical axis, aligns the labels below the gridline.

* [`LabelAlignment.end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelAlignment.html) - if it is a horizontal axis, aligns the labels after the gridline and if it is a vertical axis, align the labels above the gridline.

* [`LabelAlignment.center`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelAlignment.html) - aligns the axis label to the center of the gridlines.

### Center

Aligns the axis label to the center of the gridlines.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                        child: SfCartesianChart(
                            primaryXAxis: DateTimeAxis(),
                            primaryYAxis:
                                NumericAxis(
                                    //Aligns the y-axis labels
                                    labelAlignment: LabelAlignment.center
                                ),
                        )
                )
            )
        );
    }
     
{% endhighlight %}

![center](images/axis-customization/center.png)

### Start

If it is a horizontal axis, aligns the labels before the gridline and if it is a vertical axis, aligns the labels below the gridline.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                        child: SfCartesianChart(
                            primaryXAxis: DateTimeAxis(),
                            primaryYAxis: NumericAxis(
                                //Aligns the y-axis labels
                                labelAlignment:LabelAlignment.start),
                        )
                ) 
            )
        );
    }
     
{% endhighlight %}

![start](images/axis-customization/start.png)

### End

If it is a horizontal axis, aligns the labels after the gridline and if it is a vertical axis, align the labels above the gridline.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                        child: SfCartesianChart(
                            primaryXAxis: DateTimeAxis(),
                            primaryYAxis: NumericAxis(
                                //Aligns the y-axis labels
                                labelAlignment: LabelAlignment.end
                            ),
                        )
                )
            )
        );
    }
     
{% endhighlight %}

![end](images/axis-customization/end.png)

## Auto range calculation
Determines the value axis range, based on the visible data points or based on the overall data points available in chart. 

By default, value axis range will be calculated automatically based on the visible data points on dynamic changes. The visible data points are changed on performing interactions like pinch zooming, selection zooming, panning and also on specifying [`visibleMinimum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/visibleMinimum.html) and [`visibleMaximum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/visibleMaximum.html) values.
  
To toggle this functionality, [`anchorRangeToVisiblePoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/anchorRangeToVisiblePoints.html) property can be used. i.e. on setting this property to false, the value axis range will be calculated based on all the data points in chart irrespective of visible points.
  
>**Note**: This is applicable only to the value axis and not for other axis and applicable only when zoom mode is set to x.
  
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Container(
          child: SfCartesianChart(
             primaryYAxis: NumericAxis(anchorRangeToVisiblePoints: false),
          )
      );
    }

{% endhighlight %}

![Auto_Range_Calculation](images/axis-customization/auto_range_calculation.gif)

## Axis label width customization

The maximum width for axis labels and the space occupied by the axis labels can be controlled by using the [`maximumLabelWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/maximumLabelWidth.html) and [`labelsExtent`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelsExtent.html) properties of the axis respectively. If the provided width is lesser than the axis label's width, the label gets trimmed and the tooltip  is shown when clicking/tapping the axis label in both cases. Both properties default to `null`.


{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Container(
          child: SfCartesianChart(
            primaryXAxis: CategoryAxis(
                maximumLabelWidth: 80,
            ),
            series: <ChartSeries<ChartData, String>>[
                    BarSeries<ChartData, String>(
                        dataSource: <ChartData>[
                            ChartData('Goldin Finance 117', 597),
                            ChartData('Ping An Finance Center', 599),
                            ChartData('Makkah Clock Royal Tower', 601),
                            ChartData('Shanghai Tower', 632),
                            ChartData('Burj Khalifa', 828)],
                        xValueMapper: (ChartData data, _) => data.x,
                        yValueMapper: (ChartData data, _) => data.y
                    ),
            ]
          )
      );
    }

    class ChartData {
        ChartData(this.x, this.y);
        final String x;
        final double y;
    }

{% endhighlight %}

>**Note**:  If both [`maximumLabelWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/maximumLabelWidth.html) and [`labelsExtent`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelsExtent.html) properties are specified, then the priority goes to [`labelsExtent`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/labelsExtent.html) property.

![Axis label trim](images/axis-customization/axis-label-trim.gif)

## Auto scrolling

Auto scrolling feature available in SfCartesianChart is used to ensure that specified range of data is always visible in the chart and you can view the remaining data points by scrolling. The [`autoScrollingDelta `](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/autoScrollingDelta.html) property of the chart axis can be used to set the number of data points to be always visible in the chart. It always shows the recently added data points and scrolling will be reset to the start or end of the range, based on [`autoScrollingMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/autoScrollingMode.html) property's value, whenever a new point is added dynamically.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Container(
          child: SfCartesianChart(
             primaryYAxis: DateTimeAxis(
                 autoScrollingDelta: 7
             ),
          )
      );
    }

{% endhighlight %}

### AutoScrollingMode

[`AutoScrollingMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/autoScrollingMode.html) property can be used to determine whether the axis should be scrolled from start position or end position. The default value of [`AutoScrollingMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/autoScrollingMode.html) is `end`.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Container(
          child: SfCartesianChart(
             primaryYAxis: NumericAxis(
                 autoScrollingMode: AutoScrollingMode.start
             ),
          )
      );
    }

{% endhighlight %}

### AutoScrollingDeltaType

In [`DateTimeAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis-class.html), you can apply auto scrolling delta value in Years, Months, Days, Hours, Minutes, Seconds and auto by setting [`AutoScrollingDeltaType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/autoScrollingDeltaType.html) property. Default value of this property is `auto` and the delta will be calculated automatically based on range.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Container(
          child: SfCartesianChart(
             primaryYAxis: DateTimeAxis(
                 autoScrollingDeltaType: DateTimeIntervalType.months
             ),
          )
      );
    }

{% endhighlight %}

## RangeController

The [`rangeController`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangeController.html) property is used to set the maximum and minimum values for the chart in the viewport. In the minimum and maximum properties of the axis, you can specify the minimum and maximum values with respect to the entire data source. In the visibleMinimum and visibleMaximum properties, you can specify the values to be viewed in the viewed port i.e. range controller's start and end values respectively.

Here you need to specify the [`minimum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/minimum.html), [`maximum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/maximum.html), [`visibleMinimum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/visibleMinimum.html), and [`visibleMaximum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/visibleMaximum.html) properties to the axis and the axis values will be visible with respect to visibleMinimum and visibleMaximum properties.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    RangeController rangeController = RangeController(
      start: DateTime(2020, 2, 1),
      end: DateTime(2020, 2, 30),
    );
    SfCartesianChart sliderChart = SfCartesianChart(
      margin: const EdgeInsets.all(0),
      primaryXAxis:
          DateTimeAxis(isVisible: false),
      primaryYAxis: NumericAxis(isVisible: false),
      plotAreaBorderWidth: 0,
      series: <SplineAreaSeries<ChartSampleData, DateTime>>[
        SplineAreaSeries<ChartSampleData, DateTime>(
          //  Add required properties.
        )
      ],
    );
    return Scaffold(
      body: Column(
        children: <Widget>[
          Expanded(
            child: SfCartesianChart(
              primaryXAxis: DateTimeAxis(
                  maximum: DateTime(2020, 1, 1),
                  minimum: DateTime(2020, 3, 30),
                  // set maximum value from the range controller
                  visibleMaximum: rangeController.end,
                  // set minimum value from the range controller
                  visibleMinimum: rangeController.start,
                  rangeController: rangeController),
              primaryYAxis: NumericAxis(),
              series: <SplineSeries<ChartSampleData, DateTime>>[
                SplineSeries<ChartSampleData, DateTime>(
                  dataSource: splineSeriesData,
                  xValueMapper: (ChartSampleData sales, _) =>
                      sales.x as DateTime,
                  yValueMapper: (ChartSampleData sales, _) => sales.y,
                  //  Add required properties.
                )
              ],
            ),
          ),
          Expanded(
              child: SfRangeSelectorTheme(
            data: SfRangeSelectorThemeData(),
            child: SfRangeSelector(
              min: min,
              max: max,
              controller: rangeController,
              showTicks: true,
              showLabels: true,
              dragMode: SliderDragMode.both,
              onChanged: (SfRangeValues value) {
                // set the start value to rangeController from this callback
                rangeController.start = value.start;
                // set the end value to rangeController from this callback
                rangeController.end = value.end;
                setState(() {});
              },
              child: Container(
                child: sliderChart,
              ),
            ),
          )),
        ],
      ),
    );
    }

{% endhighlight %}

## Multi-level labels

The multi-level labels in the Cartesian chart are used to categorize axis labels and they can be added to the chart axis by using the [`multiLevelLabels`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/multiLevelLabels.html) property. The below properties are used to add the multi-level label.

* [`start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericMultiLevelLabel/start.html) - Represents the start value of an multi-level label.
* [`end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericMultiLevelLabel/end.html)   - Represents the end value of an multi-level label.
* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericMultiLevelLabel/text.html)  - Represents the text which needs to be rendered for a multilevel label.
* [`level`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericMultiLevelLabel/text.html) - Represents the hierarchical structure of a multi level label.

### Multi-level labels in numeric axis

The [`NumericMultiLevelLabel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericMultiLevelLabel/NumericMultiLevelLabel.html) class is used to render multi-level labels in the numeric axis. Here the values for [`start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericMultiLevelLabel/start.html) and [`end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericMultiLevelLabel/end.html) have to be double.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = <ChartData>[
        ChartData(1, 24),
        ChartData(2, 20),
        ChartData(3, 35),
        ChartData(4, 27),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];
      return Scaffold(
        body: SfCartesianChart(
          primaryXAxis: NumericAxis(
            multiLevelLabels: const <NumericMultiLevelLabel>[
              NumericMultiLevelLabel(
                start: 1, 
                end: 4, 
                text: 'First'
              ),
              NumericMultiLevelLabel(
                start: 4, 
                end: 7, 
                text: 'Second'
              ),
              NumericMultiLevelLabel(
                start: 1, 
                end: 4, 
                text: 'Third', 
                level: 1
              ),
              NumericMultiLevelLabel(
                start: 4, 
                end: 7, 
                text: 'Fourth', 
                level: 1
              ),
            ]
          ),
          series: <ChartSeries<ChartData, int>>[
            LineSeries<ChartData, int>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
            )
          ],
        )
      );
    }
    
    class ChartData {
      ChartData(this.x, this.y);
        final int x;
        final int y;
    }

{% endhighlight %}

![Multi-level labels](images/axis-customization/numeric_multi_level_label.jpg)

### Multi-level labels in category axis

The [`CategoricalMultiLevelLabel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CategoricalMultiLevelLabel-class.html) is used to render multi-level labels in the category axis. Here [`start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CategoricalMultiLevelLabel/start.html) and [`end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CategoricalMultiLevelLabel/end.html) values need to be string values that are available in the data source.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = <ChartData>[
        ChartData('Parker', 24),
        ChartData('David', 20),
        ChartData('Peter', 35),
        ChartData('John', 30)
      ];
      return Scaffold(
        body: SfCartesianChart(
          primaryXAxis: CategoryAxis(
            multiLevelLabels: const <CategoricalMultiLevelLabel>[
              CategoricalMultiLevelLabel(
                start:'Parker', 
                end:'David', 
                text: 'First'
              ),
              CategoricalMultiLevelLabel(
                start:'Peter', 
                end:'John', 
                text: 'Second'
              ),
              CategoricalMultiLevelLabel(
                start:'Parker', 
                end:'David',  
                text: 'Third', 
                level: 1
              ),
              CategoricalMultiLevelLabel(
                start:'Peter', 
                end:'John', 
                text: 'Fourth', 
                level: 1
              )
            ]
          ),
          series: <ChartSeries<ChartData, String>>[
            LineSeries<ChartData, String>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
            )
          ]
        )
      );
    } 

    class ChartData {
      ChartData(this.x, this.y);
       final String x;
       final int y;
    }

{% endhighlight %}

![Multi-level labels](images/axis-customization/category_multi_level_label.jpg)

### Multi-level labels in date time axis

The [`DateTimeMultiLevelLabel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeMultiLevelLabel-class.html) is used to render multi-level labels in the date-time axis. Here [`start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeMultiLevelLabel/start.html) and [`end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeMultiLevelLabel/end.html) properties need to be date-time values.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = <ChartData>[
        ChartData(DateTime(2020,1,1), 24),
        ChartData(DateTime(2021,1,1), 20),
        ChartData(DateTime(2022,1,1), 35),
        ChartData(DateTime(2023,1,1), 27),
        ChartData(DateTime(2024,1,1), 30)
      ];
      return Scaffold(
        body: SfCartesianChart(
          primaryXAxis: DateTimeAxis(
            dateFormat: DateFormat.y(),
            edgeLabelPlacement: EdgeLabelPlacement.shift,
            multiLevelLabels: <DateTimeMultiLevelLabel>[
              DateTimeMultiLevelLabel(
                start: DateTime(2020,1,1), 
                end: DateTime(2022,1,1), 
                text: 'First'
              ),
              DateTimeMultiLevelLabel(
                start: DateTime(2022,1,1), 
                end: DateTime(2024,1,1), 
                text: 'Second'
              ),
              DateTimeMultiLevelLabel(
                start: DateTime(2020,1,1), 
                end: DateTime(2022,1,1),
                text: 'Third', 
                level: 1
              ),
              DateTimeMultiLevelLabel(
                start: DateTime(2022,1,1), 
                end: DateTime(2024,1,1), 
                text: 'Fourth', 
                level: 1
              ),
            ]
          ),
          series: <ChartSeries<ChartData, DateTime>>[
            LineSeries<ChartData, DateTime>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
            )
          ]
        )
      );
    }
    
    class ChartData {
      ChartData(this.x, this.y);
        final DateTime x;
        final int y;
    }

{% endhighlight %}

![Multi-level labels](images/axis-customization/datetime_multi_level_label.jpg)

### Multi-level labels in date time category axis

The [`DateTimeCategoricalMultiLevelLabel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeCategoricalMultiLevelLabel-class.html) is used to render multi-level labels in the date-time category axis. Here [`start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeCategoricalMultiLevelLabel/start.html) and [`end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeCategoricalMultiLevelLabel/end.html) properties need to be date-time values.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = <ChartData>[
        ChartData(DateTime(2010,1,1), 24),
        ChartData(DateTime(2022,1,1), 20),
        ChartData(DateTime(2040,1,1), 27),
        ChartData(DateTime(2060,1,1), 30)
      ];
      return Scaffold(
        body: SfCartesianChart(
          primaryXAxis: DateTimeCategoryAxis(
            multiLevelLabels: <DateTimeCategoricalMultiLevelLabel>[
              DateTimeCategoricalMultiLevelLabel(
                start: DateTime(2010,1,1), 
                end: DateTime(2022,1,1), 
                text: 'First'
              ),
              DateTimeCategoricalMultiLevelLabel(
                start: DateTime(2040,1,1), 
                end: DateTime(2060,1,1), 
                text: 'Second'
              ),
              DateTimeCategoricalMultiLevelLabel(
                start: DateTime(2010,1,1), 
                end: DateTime(2022,1,1),
                text: 'Third', 
                level: 1
              ),
              DateTimeCategoricalMultiLevelLabel(
                start: DateTime(2040,1,1), 
                end: DateTime(2060,1,1), 
                text: 'Fourth', 
                level: 1
              ),
            ]
          ),
          series: <ChartSeries<ChartData, DateTime>>[
            LineSeries<ChartData, DateTime>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
            )
          ]
        )
      );
    }
    
    class ChartData {
      ChartData(this.x, this.y);
        final DateTime x;
        final int y;
    }

{% endhighlight %}

![Multi-level labels](images/axis-customization/datetime_category_multi_level_label.jpg)

### Multi-level labels in logarithmic axis

The [`LogarithmicMultiLevelLabel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LogarithmicMultiLevelLabel-class.html) is used to render multi-level labels in the logarithmic axis. Here the [`start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LogarithmicMultiLevelLabel/start.html) and [`end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LogarithmicMultiLevelLabel/end.html) properties need to be double values.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = <ChartData>[
        ChartData(1, 2),
        ChartData(2, 5),
        ChartData(3, 10),
        ChartData(4, 24),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];
      return Scaffold(
        body: SfCartesianChart(
          primaryYAxis: LogarithmicAxis(
            multiLevelLabels: const <LogarithmicMultiLevelLabel>[
              LogarithmicMultiLevelLabel(
                start: 1, 
                end: 10, 
                text: 'First'
              ),
              LogarithmicMultiLevelLabel(
                start: 10, 
                end: 100, 
                text: 'Second'
              ),
              LogarithmicMultiLevelLabel(
                start: 1, 
                end: 10, 
                text: 'Third', 
                level: 1
              ),
              LogarithmicMultiLevelLabel(
                start: 10, 
                end: 100, 
                text: 'Fourth', 
                level: 1
              ),
            ]
          ),
          series: <ChartSeries<ChartData, int>>[
            LineSeries<ChartData, int>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
            )
          ]
        )
      );
    }

    class ChartData {
      ChartData(this.x, this.y);
       final int x;
       final int y;
    }

{% endhighlight %}

![Multi-level labels](images/axis-customization/logarithmic_multi_level_label.jpg)

### Multi-level label customization

The [`multiLevelLabelStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/multiLevelLabelStyle.html) property is used to customize the multi-level label's border width, border type, color, and text style.

#### Multi-level label text customization

The text style of the multi-level label like color, font size, font-weight, etc can be customized by using [`TextStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelLabelStyle/textStyle.html) class.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = <ChartData>[
        ChartData(1, 24),
        ChartData(2, 20),
        ChartData(3, 35),
        ChartData(4, 27),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];
      return Scaffold(
        body: SfCartesianChart(
          primaryXAxis: NumericAxis(
            multiLevelLabelStyle: MultiLevelLabelStyle(
              textStyle: TextStyle(
                  fontSize: 1,
                  color: Colors.blue)
            ),
            multiLevelLabels: const <NumericMultiLevelLabel>[
              NumericMultiLevelLabel(
                start: 1, 
                end: 4, 
                text: 'First'
              ),
              NumericMultiLevelLabel(
                start: 4, 
                end: 7, 
                text: 'Second'
              ),
              NumericMultiLevelLabel(
                start: 1, 
                end: 4, 
                text: 'Third', 
                level: 1
              ),
              NumericMultiLevelLabel(
                start: 4, 
                end: 7, 
                text: 'Fourth', 
                level: 1
              )
            ]
          ),
          series: <ChartSeries<ChartData, int>>[
            LineSeries<ChartData, int>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
            )
          ]
        )
      );
    }

    class ChartData {
     ChartData(this.x, this.y);
     final int x;
     final int y;
    }

{% endhighlight %}

![Multi-level labels](images/axis-customization/multi_level_label_text_customization.jpg)

#### Multi-level label border customization

The border width, color and type of the multi-level label can be customized using the [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelLabelStyle/borderWidth.html),  [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelLabelStyle/borderColor.html) and [`borderType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelLabelStyle/borderType.html) properties.

The different types of multi-level label's border are mentioned below,

* [`MultiLevelBorderType.rectangle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelBorderType.html) - Renders the multi-level label border as rectangle.
* [`MultiLevelBorderType.withoutTopAndBottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelBorderType.html) - Renders the multi-level label border as rectangle without it's top and bottom.
* [`MultiLevelBorderType.squareBrace`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelBorderType.html) - Renders the multi-level label border as square braces.
* [`MultiLevelBorderType.curlyBrace`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelBorderType.html) - Renders the multi-level label border as curly braces.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = <ChartData>[
        ChartData(1, 24),
        ChartData(2, 20),
        ChartData(3, 35),
        ChartData(4, 27),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];
      return Scaffold(
        body: SfCartesianChart(
          primaryXAxis: NumericAxis(
            multiLevelLabelStyle: MultiLevelLabelStyle(
              borderColor: Colors.blue,
              borderWidth: 2.0,
              borderType: MultiLevelBorderType.curlyBrace,
            ),
            multiLevelLabels: const <NumericMultiLevelLabel>[
              NumericMultiLevelLabel(
                start: 1, 
                end: 4, 
                text: 'First'
              ),
              NumericMultiLevelLabel(
                start: 4, 
                end: 7, 
                text: 'Second'
              ),
              NumericMultiLevelLabel(
                start: 1, 
                end: 4, 
                text: 'Third', 
                level: 1
              ),
              NumericMultiLevelLabel(
                start: 4, 
                end: 7, 
                text: 'Fourth', 
                level: 1
              )
            ]
          ),
          series: <ChartSeries<ChartData, int>>[
            LineSeries<ChartData, int>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
            )
          ]
        )
      );
    }

    class ChartData {
     ChartData(this.x, this.y);
     final int x;
     final int y;
    }

{% endhighlight %}

![Multi-level labels](images/axis-customization/multi_level_label_border_customization.jpg)

#### See Also

* [Rendering a particular part of a data using visible minimum and visible maximum in the Cartesian chart](https://www.syncfusion.com/kb/11308/how-to-render-particular-part-of-a-data-in-cartesian-charts-sfcartesianchart).

* [Creating a flutter master-detail chart using range controller in the Cartesian chart](https://www.syncfusion.com/kb/12318/how-to-create-flutter-master-detail-chart-using-the-cartesian-charts-widget).

* [Changing the visible range of chart using range selector in the Cartesian chart](https://www.syncfusion.com/kb/12053/how-to-change-the-visible-chart-range-using-the-range-selector-widget-sfcartesianchart).
