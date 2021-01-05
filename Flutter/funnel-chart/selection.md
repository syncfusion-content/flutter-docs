---
layout: post
title: Syncfusion Flutter Charts Data Point Selection
description: Learn how to select and customize the data point in SfFunnel Charts and enable the multi selection in SfFunnel Charts.
platform: flutter
control: Chart
documentation: ug
---

# Selection in Funnel chart

The selection feature in chart let you to select a segment in a series or the series itself. This features allows you to select either individual or cluster of segments in the chart series.

{% highlight dart %} 

    @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: Center(
            child: Container(
              child: SfFunnelChart(
                series: FunnelSeries<SalesData, String>(
                    dataSource: chartData,
                    xValueMapper: (SalesData sales, _) =>   sales.year,
                    yValueMapper: (SalesData sales, _) => sales.sales,
                    selectionBehavior: SelectionBehavior(
                    // Enables the selection
                    enable: true)
                  )
              )
            )
          )
        );
      }

{% endhighlight %}

## Customizing the segments

You can customize the segments using the below properties.

* [`selectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectedColor.html) - used to change the background color of selected segment.
* [`unselectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/unselectedColor.html) - used to change the background color of unselected segment.
* [`selectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectedBorderColor.html) - used to change the stroke color of the selected segment.
* [`selectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectedBorderWidth.html) - used to change the stroke width of the selected segment.
* [`unselectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/unselectedBorderColor.html) - used to change the stroke color of the unselected segment.
* [`unselectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/unselectedBorderWidth.html) - used to change the stroke width of the unselected segment.
* [`selectedOpacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectedOpacity.html) - used to control the transparency of the selected segment.
* [`unselectedOpacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/unselectedOpacity.html) - used to control the transparency of the unselected segment.

{% highlight dart %} 

    @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: Center(
            child: Container(
              child: SfFunnelChart(
                series: FunnelSeries<SalesData, String>(
                    dataSource: chartData,
                    xValueMapper: (SalesData sales, _) =>   sales.year,
                    yValueMapper: (SalesData sales, _) => sales.sales,
                    selectionBehavior: SelectionBehavior(
                    // Enables the selection
                    enable: true,
                    selectedColor: Colors.red,
                    unselectedColor: Colors.grey,
                    )
                  )
              )
            )
          )
        );
      }

{% endhighlight %}

![Customizing segments](images/selection/customizing_segments.png)

## Multi-selection

Multiple selection can be enabled using the [`enableMultiSelection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/enableMultiSelection.html) property of chart.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        // Enables multiple selection
                        enableMultiSelection: true
                    )
                )
            )
        );
    }

{% endhighlight %}

![Multi selection](images/selection/multi_select.png)

## Selection on initial rendering

You can select a point or series programmatically on a chart using [`initialSelectedDataIndexes`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/initialSelectedDataIndexes.html) property of chart.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        initialSelectedDataIndexes: [1, 0]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Initial selection](images/selection/customizing_segments.png)

Also refer [selection event](./events#onselectionchanged) for customizing the selection further.

## Methods in SelectionBehavior

### SelectDataPoints method in SelectionBehavior

The [`selectDataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectDataPoints.html) method is used to select the data point programmatically. The required arguments are listed below.

* `pointIndex` - index of the point which needs to be selected.
* `seriesIndex` - index of the series for which the pointIndex is specified and this is an optional parameter. By default it will be considered as 0.

N> The [`enableMultiSelection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/enableMultiSelection.html) is also applicable for this but, it is based on the API values specified in the chart.

{% highlight dart %}

    SfFunnelChart chart;
    SelectionBehavior selection;

    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34)
      // Add the required data
    ];

    selection = SelectionBehavior(enable: true);
    
    chart = SfFunnelChart(
      series: FunnelSeries<ChartData, double>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y,
            selectionBehavior: selection
        )
    );
    
    return Scaffold(
      body: Center(
        child: Column(
          children: <Widget>[
            FlatButton(
              child: Text('Select'),
              onPressed: select
            ),
            Container(child: chart)
          ]
        )
      )
    );
    }
    void select() {
        selection.selectDataPoints(1, 0);
    }

{% endhighlight %}