---
layout: post
title: On-demand loading in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about On-demand loading feature of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# On-demand loading in Flutter Cartesian Charts (SfCartesianChart)

[`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html) provides support to return a widget which can be used to load more data to the chart when the visible range reaches the end on dragging in the chart with the help of the [`loadMoreIndicatorBuilder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/loadMoreIndicatorBuilder.html) builder.

To learn more about how to lazy load data while panning in Flutter Charts, you can watch this video.

<style>#flutterChartsVideoTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterChartsVideoTutorial' src='https://www.youtube.com/embed/GBKB1U-iwqI'></iframe>

## Infinite scrolling

The [`loadMoreIndicatorBuilder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/loadMoreIndicatorBuilder.html) builds the widget at the top of the chart area (ex., loading indicator or load more button) when horizontal scrolling reaches the start or end of the chart and if the chart is transposed, then this will be called when the vertical scrolling reaches the top or bottom of the chart. This can be used to achieve functionalities like infinite scrolling in the chart.

The example below demonstrates the infinite scrolling by showing the circular progress indicator until the data is loaded when horizontal scrolling reaches the end of the chart.

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Container(
          child: SfCartesianChart(
             loadMoreIndicatorBuilder:
               (BuildContext context, ChartSwipeDirection direction) =>
                   getLoadMoreViewBuilder(context, direction),
             series: <CartesianSeries<ChartData, num>>[
                  LineSeries<ChartData, num>(
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

    class ChartData {
        ChartData(this.x, this.y);
        final num x;
        final double? y;
      }

{% endhighlight %}
{% endtabs %}

![Infinite_scrolling](images/on-demand-loading/infinite_scrolling.gif)

>**Note**: `chartData` in the above code snippets is a class type list and holds the data for binding to the chart series. Refer [Bind data source](https://help.syncfusion.com/flutter/cartesian-charts/getting-started#bind-data-source) topic for more details.

#### See Also

* [Lazily load more data to the chart](https://support.syncfusion.com/kb/article/10855/how-to-lazily-load-more-data-to-the-chart-sfcartesianchart).