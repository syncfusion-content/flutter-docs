---
layout: post
title: Syncfusion Flutter Chart Data Point Selection
description: How to select the data point in Essential Flutter Chart
platform: flutter
control: Chart
documentation: ug
---

# Selection

Chart supports selection that enables you to select a segment in a series or series itself.

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

You can customize the segements using the below properties.

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

The selection features allows you to select segments with following options using [`selectionType`]() property of chart.

* [`point`]() - selects the individual point.
* [`series`]() - selects the entire series.
* [`cluster`]() - selects the cluster of points of same or different series.

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
