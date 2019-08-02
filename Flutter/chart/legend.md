---
layout: post
title: Syncfusion Flutter Chart legend
description: How to configure the chart legend and customize the appearance of the legend title, Icons, labels, and template in Essential Flutter Chart.
platform: flutter
control: Chart
documentation: ug
---

# Legend

The [`legend`]() contains list of chart series/data points in chart. The information provided in each legend item helps to identify the corresponding data series in chart.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(
                legend: Legend(isVisible: true),
                series: <CircularSeries>[
              PieSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
            ])
        )));
    }

{% endhighlight %}

![Legend](images/getting-started/livechart.png)

## Customizing legend item text

The [`name`]() property of [`CartesianSeries`] is used to define the label for the corresponding series legend item and for [`CircularSeries`]() type chart by default values mapped with [`xValueMapper`]() will be displayed. The appearance of the label can be customized using the below properties.

* [`borderWidth`]() – used to change the stroke width of the legend shape.
* [`borderColor`]() – used to change the stroke color of the legend shape.
* [`backgroundColor`] - used to change the background color of legend shape.
* [`opacity`] - used to control the transparency of the legend icon shape.
* [`padding`] - used to add padding between the icon shape and the text.
* [`iconHeight`]() - used to change the height of the icon shape.
* [`iconWidth`]() - used to change the width of the icon shape.
* [`borderWidth`]() – used to change the stroke width of the legend icon shape.
* [`iconBorderColor`]() – used to change the stroke color of the legend icon shape.
* [`itemPadding`]() - used to add padding between the first legend text and the second legend icon shape.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(
                legend: Legend(
                    isVisible: true,
                    borderColor: Colors.black,
                    borderWidth: 2,
                ),
                series: <CircularSeries>[
              PieSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
            ])
        )));
    }

{% endhighlight %}

![Legend text](images/getting-started/livechart.png)

### Legend title

The following properties are used to define and customize the [`title`]() of [`legend`]().

* [`text`] - used to change the text of the title.
* [`textStyle`]() – used to change the text color, size, font family, fontStyle, and font weight.
* [`textStyle.color`]() – used to change the color of the text.
* [`textStyle.fontFamily`]() - used to change the font family for legend text. 
* [`textStyle.fontStyle`]() – used to change the font style for the legend text.
* [`textStyle.fontSize`]() - used to change the font size for the legend text.
* [`alignment`] – used to change the alignment of the title text; it can be near, center, or far.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(
                legend: Legend(
                    isVisible: true,
                    textStyle: ChartTextStyle(
                      color: Colors.red,
                      fontSize: 15,
                      fontStyle: FontStyle.italic,
                      fontWeight: FontWeight.w900
                    ),
                ),
                series: <CircularSeries>[
              PieSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
            ])
        )));
    }

{% endhighlight %}

![Legend text](images/getting-started/livechart.png)

### Toggles the series visibility

You can control the visibility of the series by tapping the legend item. You can enable this feature by enabling the [`toggleSeriesVisibility`]() property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(
                legend: Legend(
                    isVisible: true,
                    toggleSeriesVisibility: true,
                ),
                series: <CircularSeries>[
              PieSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
            ])
        )));
    }

{% endhighlight %}

### Legend visibility

The [`isVisible`]() property of [`legend`]() is used to toggle the visibility of legend.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(
                legend: Legend(
                    isVisible: false,
                ),
                series: <CircularSeries>[
              PieSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
            ])
        )));
    }

{% endhighlight %}

![Legend visibility](images/getting-started/livechart.png)

### Legend item visibility

You can control the visibility of a particular series legend item using the [`isVisibleInLegend`]() property of series. The default value of the [`isVisibleInLegend`]() property is *true*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                legend: Legend(
                    isVisible: true,
                ),
                primaryXAxis: CategoryAxis(),
                series: <ColumnSeries>[
              ColumnSeries<ChartData, String>(
                isVisibleInLegend: false,
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
            ])
        )));
    }

{% endhighlight %}

### Legend over flow

The legend items can be placed in multiple rows using the [`overflowMode`]() property if size of the total legend exceeds the available size. The default value of the [`overflowMode`]() property is [`scroll `]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(
                legend: Legend(
                    isVisible: true,
                    overflowMode: LegendItemOverflowMode.wrap,
                ),
                series: <CircularSeries>[
              PieSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
            ])
        )));
    }

{% endhighlight %}

![Legend over flow](images/getting-started/livechart.png)


### Positioning the legend

You can position the legend anywhere inside the chart. The following properties are used to customize the position of legend:

* [`position`]() – used to position the legend relatively. The available options are  [`auto`](), [`bottom`](), [`left`](), [`right`](), and [`top`]().
* [`orientation`]() - used to change the orientation of the legend, the default value is [`auto`](). Also you can set [`horizontal`]() or [`vertical`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(
                legend: Legend(
                    isVisible: true,
                    position: LegendPosition.left,
                ),
                series: <CircularSeries>[
              PieSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
            ])
        )));
    }

{% endhighlight %}

![Legend position](images/getting-started/livechart.png)

### Legend item template

You can customize the appearance of legend items with your template by using [`legendItemBuilder`]() property of [`legend`].

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(
                legend: Legend(
                    isVisible: true,
                    legendItemBuilder: (String name, dynamic series,
                        dynamic point, int index) {
                      return Container(
                        height: 20,
                        width: 10,
                        child: Container(child: Text(point.y.toString())),
                      );
                    }),
                series: <CircularSeries>[
              PieSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
            ])
        )));
    }

{% endhighlight %}

![Legend template](images/getting-started/livechart.png)