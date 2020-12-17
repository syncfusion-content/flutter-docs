---
layout: post
title: Syncfusion Flutter Spark charts types
description: Learn what are the different types of Spark charts available in the Syncfusion Flutter Spark chart widgets.
platform: flutter
control: Sparkline
documentation: ug
---

# Chart types in Spark charts

## Line chart

[`SfSparkLineChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart-class.html) is used for identifying patterns and trends in the data such as seasonal effects, large changes and turning points over a period of time. 

The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/color.html) - Specifies the spark line color.
* [`data`]()  - Used to bind the data to spark line charts.
* [`axisCrossesAt`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/axisCrossesAt.html) - Specifies the axis line's position.
* [`axisLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/axisLineColor.html) - Specifies the color of the axis line.
* [`axisLineWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/axisLineWidth.html) - Specifies the width of the axis line.
* [`axisLineDashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/axisLineDashArray.html) - Specifies the dash array value of the axis line.
* [`marker`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/marker.html) - Represents the marker settings of spark line chart.
* [`labelDisplayMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/labelDisplayMode.html) - Specifies the spark line data label.
* [`labelStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/labelStyle.html) - Specifies the spark line data label.
* [`trackball`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/trackball.html) - Represents the track ball options of spark line chart.
* [`plotBand`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/plotBand.html) - Represents the plot band settings for spark line chart.
* [`isInversed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/isInversed.html) - Specifies whether to inverse the spark line chart.
* [`highPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/highPointColor.html) - Specifies the high point color.
* [`lowPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/lowPointColor.html) - Specifies the low point color.
* [`negativePointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/negativePointColor.html) - Specifies the negative point color.
* [`firstPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/firstPointColor.html) - Specifies the first point color.
* [`lastPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/lastPointColor.html) - Specifies the last point color.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/width.html) - Specifies the width of the line series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfSparkLineChart(
            data: <double>[
                5, 6, 5, 7, 4, 3, 9, 5, 6, 5, 7, 8, 4, 5, 3, 4, 11, 10, 2, 12, 4, 7, 6, 8
            ],
            highPointColor: Colors.red,
            lowPointColor: Colors.green,
            firstPointColor: Colors.orange,
            lastPointColor: Colors.orange,
            width: 3,
            marker: SparkChartMarker(
              displayMode: SparkChartMarkerDisplayMode.all
            ),
          )
        )
      );
    }

{% endhighlight %}

![Spark line chart](images/sparkline-types/sparkline.png)

### Dashed line

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/dashArray.html) property of [`SfSparkLineChart`]() is used to render line chart with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child:  SfSparkLineChart(
            axisLineWidth: 0,
            data: <double>[
                        5, 6, 5, 7, 4, 3, 9, 5, 6, 5, 7, 8, 4, 5, 3, 4, 11, 10, 2, 12, 4, 7, 6, 8
                      ],
            dashArray: <double>[5,3],
          )
        )
      );
    }

{% endhighlight %}

![Spark line dashArray](images/sparkline-types/sparkline-dasharray.png)

## Area chart

[`SfSparkAreaChart`]() is used to emphasize a change in values. This is primarily used when the magnitude of the trend is to be communicated rather than individual data values.

The following properties are used to customize the appearance:

* [`color`]() - Specifies the fill color of spark area chart.
* [`data`]()  - Used to bind the data to spark area charts.
* [`axisCrossesAt`]() - Specifies the axis line's position.
* [`axisLineColor`]() - Specifies the color of the axis line.
* [`axisLineWidth`]() - Specifies the width of the axis line.
* [`axisLineDashArray`] - Specifies the dash array value of the axis line.
* [`marker`]() - Represents the marker settings of spark area chart.
* [`labelDisplayMode`]() - Specifies the spark area data label.
* [`labelStyle`]() - Specifies the spark area data label.
* [`trackball`]() - Represents the track ball options of spark area chart.
* [`plotBand`]() - Represents the plot band settings for spark area chart.
* [`isInversed`]() - Specifies whether to inverse the spark area chart.
* [`highPointColor`]() - Specifies the high point color.
* [`lowPointColor`]() - Specifies the low point color.
* [`negativePointColor`]() - Specifies the negative point color.
* [`firstPointColor`]() - Specifies the first point color.
* [`lastPointColor`]() - Specifies the last point color.
* [`borderWidth`]() – Changes the stroke width of the spark area chart.
* [`borderColor`]() – Changes the stroke color of the spark area chart.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child:  SfSparkAreaChart(
            data: <double>[
                34, 36, 32, 35, 40, 38, 33, 37, 34, 31, 30
            ],
            borderColor: Colors.red.withOpacity(0.8),
            borderWidth: 2,
            marker: SparkChartMarker(
              displayMode: SparkChartMarkerDisplayMode.high
            ),
          )
        )
      );
    }

{% endhighlight %}

![Spark Area chart](images/sparkline-types/spark-area.png)

## Bar Sparkline chart

[`SfSparkBarChart`]() is used to render the sparkline series as Bar.The following properties are used to customize the appearance:

* [`color`]() - Specifies the fill color of the spark bar chart.
* [`data`]()  - Used to bind the data to spark are charts.
* [`axisCrossesAt`]() - Specifies the axis line's position.
* [`axisLineColor`]() - Specifies the color of the axis line.
* [`axisLineWidth`]() - Specifies the width of the axis line.
* [`axisLineDashArray`] - Specifies the dash array value of the axis line.
* [`marker`]() - Represents the marker settings of spark bar chart.
* [`labelDisplayMode`]() - Specifies the spark bar data label.
* [`labelStyle`]() - Specifies the spark bar data label.
* [`trackball`]() - Represents the track ball options of spark bar chart.
* [`plotBand`]() - Represents the plot band settings for spark bar chart.
* [`isInversed`]() - Specifies whether to inverse the spark line chart.
* [`highPointColor`]() - Specifies the high point color.
* [`lowPointColor`]() - Specifies the low point color.
* [`negativePointColor`]() - Specifies the negative point color.
* [`firstPointColor`]() - Specifies the first point color.
* [`lastPointColor`]() - Specifies the last point color.
* [`borderWidth`]() – Changes the stroke width of the series.
* [`borderColor`]() – Changes the stroke color of the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child:  SfSparkBarChart(
            data: <double>[
              10, 6, 8, -5, 11, 5, -2, 7, -3, 6, 8, 10
            ],
            highPointColor: Colors.red,
            lowPointColor: Colors.green,
            firstPointColor: Colors.orange,
            lastPointColor: Colors.orange,
          )
        )
      );
    }

{% endhighlight %}

![Spark Bar chart](images/sparkline-types/spark-bar.png)

## WinLoss Sparkline chart

[`SfSparkWinLossChart`]() is used to show whether each value is positive or negative visualizing a Win/Loss scenario. 

The following properties are used to customize the appearance:

* [`color`]() - Specifies the spark line color.
* [`data`]()  - Create the spark line chart with custom data source.
* [`axisCrossesAt`]() - Specifies the axis line's position.
* [`axisLineColor`]() - Specifies the color of the axis line.
* [`axisLineWidth`]() - Specifies the width of the axis line.
* [`axisLineDashArray`] - Specifies the dash array value of the axis line.
* [`trackball`]() - Represents the track ball options of spark bar chart.
* [`isInversed`]() - Specifies whether to inverse the spark line chart.
* [`highPointColor`]() - Specifies the high point color.
* [`lowPointColor`]() - Specifies the low point color.
* [`negativePointColor`]() - Specifies the negative point color.
* [`firstPointColor`]() - Specifies the first point color.
* [`lastPointColor`]() - Specifies the last point color.
* [`borderWidth`]() – Changes the stroke width of the win loss chart.
* [`borderColor`]() – Changes the stroke color of the win loss chart.
* [`tiePointColor`]() - Specifies the tie point color of win loss chart. color.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child:  SfSparkWinLossChart(
            data: <double>[
              12, 15, -10, 13, 15, 6, -12, 17, 13, 0, 8, -10
            ],
          )
        )
      );
    }

{% endhighlight %}

![Spark win-loss chart](images/sparkline-types/spark-win-loss.png)
