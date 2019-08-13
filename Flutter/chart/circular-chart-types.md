---
layout: post
title: Syncfusion Circular Chart Types
description: Learn what are the different types of circular charts available in Flutter Chart.
platform: flutter
control: Chart
documentation: ug
---

# Circular chart types

## Pie chart

To render a pie chart, create an instance of [`PieSeries`]() and add to the [`series`]() collection property of [`SfCircularChart`](). You can use the following properties to customize the pie segment appearance.

* [`opacity`]() - used to control the transparency of the chart series.
* [`strokeWidth`]() – used to change the stroke width of the series.
* [`strokeColor`]() – used to change the stroke color of the series.
* [`pointColorMapper`]() - used to map the color for individual points from the data source.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData('David', 25),
            ChartData('Steve', 38),
            ChartData('Jack', 34),
            ChartData('Others', 52)
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                PieSeries<ChartData, String>(
                    dataSource: chartData,
                    pointColorMapper:(ChartData data,  _) => data.color,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y
                )
            ]))
        )
        );
    }

    class ChartData {
        ChartData(this.x, this.y, [this.color]);
            final String x;
            final double y;
            final Color color;
    }

{% endhighlight %}

![Pie chart](images/circular-chart-types/pie.jpg)

### Changing pie size

You can use [`radius`]() property to change the diameter of the pie chart with respect to the plot area. The default value is *80%*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                PieSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    radius: '50%'
                )
            ]))
        )
        );
    }


{% endhighlight %}

![Pie size](images/circular-chart-types/pie_sizing.jpg)

### Exploding a segment

You can explode a pie segment by enabling the [`explode`]() property. You can use the following properties to customize the explode options.

* [`explodeIndex`]() - specifies the index of the slice to explode it at the initial rendering.
* [`explodeOffset`]() - specifies the offset of exploded slice. The value ranges from 0% to 100%.
* [`explodeGesture`]() - gesture for activating the explode. Explode can be activated in single tap, double tap, and long press. The available gesture types are [`singleTap`](), [`doubleTap`](), [`longPress`]() and [`none`]() and the default value is [`singleTap`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                PieSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    explode: true,
                    explodeIndex: 1
                )
            ]))
        )
        );
    }


{% endhighlight %}

![Pie explode](images/circular-chart-types/pie_explode.jpg)

### Exploding all the segments

Using [`explodeAll`]() property of [`PieSeries`](), you can explode all the pie segments.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                PieSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    explode: true,
                    explodeAll: true
                ),
            ])),
        ),
        );
    }


{% endhighlight %}

![Pie explode all](images/circular-chart-types/pie_explodeAll.jpg)

### Angle of pie

[`SfCircularChart`]() allows you to render all the data points/segments in semi-pie, quarter-pie or in any sector using [`startAngle`]() and [`endAngle`]() properties.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                PieSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    startAngle: 270,
                    endAngle: 90
                ),
            ])),
        ),
        );
    }


{% endhighlight %}

![Pie angle](images/circular-chart-types/pie_angle.jpg)

### Grouping data points

The small segments in the pie chart can be grouped into **others** category using the [`groupTo`]() and [`groupMode`]() properties of [`PieSeries`](). The [`groupMode`]() property is used to specify the grouping type based on the actual data point value, or by points length, and the [`groupTo`]() property is used to set the limit to group data points into a single slice. The grouped segment is labeled as **Others** in legend and toggled as any other segment. The default value of the [`groupTo`]() property is *null*, and [`groupMode`]() property is [`point`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                PieSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    groupMode: CircularChartGroupMode.point,
                    groupTo: 2
                ),
            ])),
        ),
        );
    }


{% endhighlight %}

![Pie grouping](images/circular-chart-types/pie_grouping.jpg)

### Various radius for each slice

The [`pointRadiusMapper`]() maps the field name, which will be considered for calculating the radius of the data points.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData('USA', 10, '70%'),
            ChartData('China', 11, '60%'),
            ChartData('Russia', 9, '52%'),
            ChartData('Germany', 10, '40%'),
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                        PieSeries<ChartData, String>(
                            dataSource: chartData,
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y,
                            pointRadiusMapper: (ChartData data, _) => data.size,
                        ),
                ])),
            ),
        );
    }

    class ChartData {
         ChartData(this.x, this.y, this.size);
            final String x;
            final double y;
            final String size;
    }

{% endhighlight %}

![Pie various radius](images/circular-chart-types/pie_radius.jpg)

## Doughnut chart

To render a doughnut chart, create an instance of [`DoughnutSeries`]() and add to the [`series`]() collection property of [`SfCircularChart`](). You can use the following properties to customize the doughnut segment appearance.

* [`opacity`]() - used to control the transparency of the chart series.
* [`strokeWidth`]() – used to change the stroke width of the series.
* [`strokeColor`]() – used to change the stroke color of the series.
* [`pointColorMapper`]() - used to map the color for individual points from the data source.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData('David', 25, Color.fromRGBO(9,0,136,1)),
            ChartData('Steve', 38, Color.fromRGBO(147,0,119,1)),
            ChartData('Jack', 34, Color.fromRGBO(228,0,124,1)),
            ChartData('Others', 52, Color.fromRGBO(255,189,57,1)),
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                DoughnutSeries<ChartData, String>(
                    dataSource: chartData,
                    pointColorMapper:(ChartData data,  _) => data.color,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                ),
            ])),
        ),
        );
    }

    class ChartData {
        ChartData(this.x, this.y, [this.color]);
            final String x;
            final double y;
            final Color color;
    }

{% endhighlight %}

![Doughnut chart](images/circular-chart-types/doughnut.jpg)

### Rounded corners

The [`cornerStyle`]() property specifies the corner type for doughnut chart. The corners can be customized using [`bothFlat`](), [`bothCurve`](), [`startCurve`](), and [`endCurve`]() options. The [`cornerStyle`]() defaults to [`bothFlat`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                DoughnutSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    cornerStyle: CornerStyle.bothCurve
                ),
            ])),
        ),
        );
    }

{% endhighlight %}

![Doughnut corner style](images/circular-chart-types/doughnut_roundCorner.jpg)

### Changing the doughnut size

You can use [`radius`]() property to change the diameter of the doughnut chart with respect to the plot area. The default value is *80%*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                DoughnutSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    radius: '50%'
                ),
            ])),
        ),
        );
    }


{% endhighlight %}

![Doughnut size](images/circular-chart-types/doughnut_size.jpg)

### Changing doughnut inner radius

You can change the doughnut chart inner radius using the [`innerRadius`]() with respect to the plot area. The value ranges from 0% to 100%.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                DoughnutSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    innerRadius: '80%'
                ),
            ])),
        ),
        );
    }

{% endhighlight %}

![Doughnut innner radius](images/circular-chart-types/doughnut_innerRadius.jpg)


### Exploding a segment

You can explode a doughnut segment by enabling the [`explode`]() property. You can use the following properties to customize the explode options.

* [`explodeIndex`]() - specifies the index of the slice to explode it at the initial rendering.
* [`explodeOffset`]() - specifies the offset of exploded slice. The value ranges from 0% to 100%.
* [`explodeGesture`]() - gesture for activating the explode. Explode can be activated in single tap, double tap, and long press. The available gesture types are [`singleTap`](), [`doubleTap`](), [`longPress`]() and [`none`]() and the default value is [`singleTap`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                DoughnutSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    explode: true,
                    explodeIndex: 1,
                ),
            ])),
        ),
        );
    }


{% endhighlight %}

![Doughnut explode](images/circular-chart-types/doughnut_explode.jpg)

### Exploding all the segments

Using [`explodeAll`]() property of [`DoughnutSeries`](), you can explode all the doughnut segments.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                DoughnutSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    explode: true,
                    explodeAll: true
                ),
            ])),
        ),
        );
    }


{% endhighlight %}

![Pie explode all](images/circular-chart-types/doughnut_explodeAll.jpg)

### Angle of doughnut

[`SfCircularChart`]() allows you to render all the data points/segments in semi-pie, quarter-pie or in any sector using [`startAngle`]() and [`endAngle`]() properties.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                DoughnutSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    startAngle: 270,
                    endAngle: 90
                )
            ]))
        )
        );
    }


{% endhighlight %}

![Doughnut angle](images/circular-chart-types/doughnut_angle.jpg)

### Grouping data points

The small segments in the doughnut chart can be grouped into **others** category using the [`groupTo`]() and [`groupMode`]() properties of [`DoughnutSeries`](). The [`groupMode`]() property is used to specify the grouping type based on the actual data point value, or by points length, and the [`groupTo`]() property is used to set the limit to group data points into a single slice. The grouped segment is labeled as **Others** in legend and toggled as any other segment. The default value of the [`groupTo`]() property is *null*, and [`groupMode`]() property is [`point`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                DoughnutSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    groupMode: CircularChartGroupMode.point,
                    groupTo: 2
                )
            ]))
        )
        );
    }


{% endhighlight %}

![Doughnut grouping](images/circular-chart-types/doughnut_grouping.jpg)

## Radial bar chart

The radial bar chart is used for showing the comparisons among the categories using the circualr shapes. To render a radial bar chart, create an instance of [`RadialBarSeries`]() and add to the [`series`]() collection property of [`SfCircularChart`](). You can use the following properties to customize the pie segment appearance.

* [`opacity`]() - used to control the transparency of the chart series.
* [`strokeWidth`]() – used to change the stroke width of the series.
* [`strokeColor`]() – used to change the stroke color of the series.
* [`pointColorMapper`]() - used to map the color for individual points from the data source.
* [`gap`]() - changes the spacing between two individual segments. The default value of spacing is 1%.
* [`maximumValue`]() - represents the entire span of an individual circle. The default value of the this property is null.
* [`trackColor`]() - changes the color of the track area.
* [`trackBorderColor`]() - changes the color of the track border.
* [`trackBorderWidth`]() - changes the width of the track border.
* [`trackOpacity`]() - controls the transparency of the track area.
* [`useSeriesColor`]() - uses the point color for filling the track area.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
          RadialBarSeries<ChartData, String>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y
          )
        ]))
        )
        );
    }


{% endhighlight %}

![Radial bar chart](images/circular-chart-types/radialbar.jpg)

### Changing the radial bar size

You can use [`radius`]() property to change the diameter of the radial bar chart with respect to the plot area. The default value is *80%*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                RadialBarSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    radius: '50%'
                )
            ]))
        )
        );
    }


{% endhighlight %}

![Radial bar size](images/circular-chart-types/radialbar_sizing.jpg)

### Changing the radial bar inner radius

You can change the radial bar chart inner radius using the [`innerRadius`]() with respect to the plot area. The value ranges from 0% to 100%.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                RadialBarSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    innerRadius: '80%'
                )
            ]))
        )
        );
    }

{% endhighlight %}

### Rounded corners

The [`cornerStyle`]() property specifies the corner type for radial bar chart. The corners can be customized using [`bothFlat`](), [`bothCurve`](), [`startCurve`](), and [`endCurve`]() options. The [`cornerStyle`]() default to [`bothFlat`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                RadialBarSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    cornerStyle: CornerStyle.bothCurve
                )
            ]))
        )
        );
    }

{% endhighlight %}

![Radial bar corner style](images/circular-chart-types/radialbar_roundCorner.jpg)

### Rendering data labels

Data labels can be enabled by using [`isVisible`]() property of [`dataLabelSettings`](). The label appearance can be customized using following properties.

* [`color`]() - used to change the label background color.
* [`textStyle`]() – used to change the text color, size, font family, fontStyle, and font weight.
* [`textStyle.color`]() – used to change the color of the text.
* [`textStyle.fontFamily`]() - used to change the font family for chart title. 
* [`textStyle.fontStyle`]() – used to change the font style for the chart title.
* [`textStyle.fontSize`]() - used to change the font size for the chart title.
* [`opacity`]() - used to control the transparency of the label background color.
* [`borderRadius`]() - customizes the data label border radius.
* [`angle`]() - used to rotate the labels.
* [`borderWidth`]() – used to change the stroke width of the data label shape.
* [`borderColor`]() – used to change the stroke color of the data label shape.
* [`useSeriesColor`]() - uses the series color for filling the data label shape.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries>[
                        RadialBarSeries<ChartData, String>(
                            dataSource: chartData,
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y,
                            dataLabelSettings: DataLabelSettings(
                                isVisible: true
                            ))
                    ]))
            )
        );
    }

{% endhighlight %}

![Radial bar data label](images/circular-chart-types/radialbar_dataLabel.jpg)