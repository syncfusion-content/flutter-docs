---
layout: post
title: Plot band in Flutter Spark Charts widget | Syncfusion 
description: Learn here all about the plot band feature of Syncfusion Spark Charts widget, its properties, and more.
platform: flutter
control: Sparkline
documentation: ug
---
# Plot band in Flutter Spark Charts 

This feature is used to highlight a particular region in the spark charts along Y axis.

The following properties are used to customize the appearances:
* [`start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartPlotBand/start.html) - used to configure the start plot band value in Y axis.
* [`end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartPlotBand/end.html) - used to configure the end plot band values in Y axis.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartPlotBand/color.html) - used to change the color for plot band.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartPlotBand/borderColor.html) - used to change the border color of plot band.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartPlotBand/borderWidth.html) - used to change the border width of plot band.

{% tabs %}
{% highlight Dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfSparkLineChart(
            axisLineWidth:0,
              plotBand: SparkChartPlotBand(start: 7, end: 8),
              data: <double>[
                  5, 6, 5, 7, 4, 3, 9, 5, 6, 5, 7, 8, 4, 5, 3, 4, 11, 10, 2, 12, 4, 7, 6, 8
              ],
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

![Sparkline plot band](images/plotband/spark-plotband.png)