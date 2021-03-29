---
layout: post
title: On demand loading feature in Syncfusion Flutter charts
description: Learn how to achieve infinite scrolling functionality in Syncfusion Flutter Cartesian charts using the on demand loading feature.
platform: flutter
control: Chart
documentation: ug
---

# On-demand loading in Cartesian chart

[`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html) provides support to return a widget which can be used to load more data to the chart when the visible range reaches the end on dragging in the chart with the help of the [`loadMoreIndicatorBuilder`](~) builder.

## Infinite scrolling

The [`loadMoreIndicatorBuilder`](~) builds the widget at the top of the chart area (ex., loading indicator or load more button) when horizontal scrolling reaches the start or end of the chart and if the chart is transposed then, this will be called when the vertical scrolling reaches the top or bottom of the chart. this can be used to achieve the functionalities like infinite scrolling in the chart.

The below example demonstrates the infinite scrolling by showing the circular progress indicator until the data is loaded when horizontal scrolling reaches the end of the chart.

{% highlight dart %}

    Widget build(BuildContext context) {
      return Container(
          child: SfCartesianChart(
             loadMoreIndicatorBuilder:
               (BuildContext context, ChartSwipeDirection direction) =>
                   getLoadMoreViewBuilder(context, direction),
             series: <ChartSeries<SalesData, num>>[
                  AreaSeries<SalesData, num>(
                      dataSource: chartData,
                  ),
                ],
            )
        );
    }

    Widget getLoadMoreViewBuilder(
      BuildContext context, ChartSwipeDirection direction) {
       if (direction == ChartSwipeDirection.end) {
         return FutureBuilder<String>(
           future: _updateData(), /// Adding data by updateDataSource method
           builder:
            (BuildContext futureContext, AsyncSnapshot<String> snapShot) {
             return snapShot.connectionState != ConnectionState.done
                 ? const CircularProgressIndicator()
                 : SizedBox.fromSize(size: Size.zero);
            },
         );
       } else {
         return SizedBox.fromSize(size: Size.zero);
       }
    }

{% endhighlight %}

![Infinite_scrolling](images/on-demand-loading/infinite_scrolling.gif)

