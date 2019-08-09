---
layout: post
title: Syncfusion Flutter Charts Data Point Selection
description: Learn how to select the data point in  Flutter Charts.
platform: flutter
control: Chart
documentation: ug
---

# Selection

The selection feature in chart let you to select a segment in a series or the series itself.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
              series: <CartesianSeries>[
            ColumnSeries<ChartData, double>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
                selectionSettings: SelectionSettings(enable: true))
          ],
        ))
        ));
    }

{% endhighlight %}

## Customizing the segments

You can customize the segments using the below properties.

* [`selectedColor`]() - used to change the background color of selected segment.
* [`unselectedColor`]() - used to change the background color of unselected segment.
* [`selectedBorderColor`]() - used to change the stroke color of the selected segment.
* [`selectedBorderWidth`]() - used to change the stroke width of the selected segment.
* [`unselectedBorderColor`]() - used to change the stroke color of the unselected segment.
* [`unselectedBorderWidth`]() - used to change the stroke width of the unselected segment.
* [`selectedOpacity`]() - used to control the transparency of the selected segment.
* [`unselectedOpacity`]() - used to control the transparency of the selected segment.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
              series: <CartesianSeries>[
            ColumnSeries<ChartData, double>(
                selectionSettings: SelectionSettings(
                  enable: true,
                  selectedColor: Colors.red,
                  unselectedColor: Colors.grey
                ))
          ],
        ))
        ));
    }

{% endhighlight %}

## Selection modes

The selection features allows you to select segments in following modes using [`selectionType`]() property of chart.

* [`Point`]() - selects the individual data point.
* [`Series`]() - selects the entire series.
* [`Cluster`]() - selects the cluster of points of different series i.e selects the points with same index in each series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                    selectionType: SelectionType.cluster
            ))
        ));
    }

{% endhighlight %}


## Multi-selection

Multiple selection can be enabled using the [`enableMultiSelection`]() property of chart.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                    enableMultiSelection: true,
            ))
        ));
    }

{% endhighlight %}

## Selection on initial rendering

You can select a point or series programmatically on a chart using [`initialSelectedDataIndexes`]() property of chart.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                    initialSelectedDataIndexes: <IndexesModel>[IndexesModel(1, 0)]
            ))
        ));
    }

{% endhighlight %}
