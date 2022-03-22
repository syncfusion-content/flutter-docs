---
layout: post
title: Chart types in Flutter Spark Charts widget | Syncfusion 
description: Learn here all about the available Chart types of Syncfusion Spark Charts widget, its features and more.
platform: flutter
control: Sparkline
documentation: ug
---

# Chart types in Flutter Spark Charts

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
* [`labelStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/labelStyle.html) - Specifies the spark line data label style.
* [`trackball`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/trackball.html) - Represents the trackball options of spark line chart.
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
            axisLineWidth: 0,
            data: <double>[
                5, 6, 5, 7, 4, 3, 9, 5, 6, 5, 7, 8, 4, 5, 3, 4, 11, 10, 2, 12, 4, 7, 6, 8
            ],
            highPointColor: Colors.red,
            lowPointColor: Colors.red,
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

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/dashArray.html) property of [`SfSparkLineChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart-class.html) is used to render line chart with dashes. Odd value is considered as rendering size and even value is considered as gap.

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

#### See Also 

* [Bind data to the Flutter Sparkline chart](https://www.syncfusion.com/kb/12317/how-to-bind-data-to-the-flutter-sparkline-chart-sfsparklinechart).

## Area chart

[`SfSparkAreaChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart-class.html) is used to emphasize a change in values. This is primarily used when the magnitude of the trend is to be communicated rather than individual data values.

The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/color.html) - Specifies the fill color of spark area chart.
* [`data`]()  - Used to bind the data to spark area charts.
* [`axisCrossesAt`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/axisCrossesAt.html) - Specifies the axis line's position.
* [`axisLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/axisLineColor.html) - Specifies the color of the axis line.
* [`axisLineWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/axisLineWidth.html) - Specifies the width of the axis line.
* [`axisLineDashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/axisLineDashArray.html) - Specifies the dash array value of the axis line.
* [`marker`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/marker.html) - Represents the marker settings of spark area chart.
* [`labelDisplayMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/labelDisplayMode.html) - Specifies the spark area data label.
* [`labelStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/labelStyle.html) - Specifies the spark area data label style.
* [`trackball`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/trackball.html) - Represents the trackball options of spark area chart.
* [`plotBand`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/plotBand.html) - Represents the plot band settings for spark area chart.
* [`isInversed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/isInversed.html) - Specifies whether to inverse the spark area chart.
* [`highPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/highPointColor.html) - Specifies the high point color.
* [`lowPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/lowPointColor.html) - Specifies the low point color.
* [`negativePointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/negativePointColor.html) - Specifies the negative point color.
* [`firstPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/firstPointColor.html) - Specifies the first point color.
* [`lastPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/lastPointColor.html) - Specifies the last point color.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/borderWidth.html) - Changes the stroke width of the spark area chart.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart/borderColor.html) - Changes the stroke color of the spark area chart.

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

![Spark area chart](images/sparkline-types/spark-area.png)

## Bar chart

[`SfSparkBarChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart-class.html) is used to render the spark bar type series.The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/color.html) - Specifies the fill color of the spark bar chart.
* [`data`]()  - Used to bind the data to spark area charts.
* [`axisCrossesAt`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/axisCrossesAt.html) - Specifies the axis line's position.
* [`axisLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/axisLineColor.html) - Specifies the color of the axis line.
* [`axisLineWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/axisLineWidth.html) - Specifies the width of the axis line.
* [`axisLineDashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/axisLineDashArray.html) - Specifies the dash array value of the axis line.
* [`labelDisplayMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/labelDisplayMode.html) - Specifies the spark bar data label.
* [`labelStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/labelStyle.html) - Specifies the spark bar data label style.
* [`trackball`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/trackball.html) - Represents the trackball options of spark bar chart.
* [`plotBand`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/plotBand.html) - Represents the plot band settings for spark bar chart.
* [`isInversed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/isInversed.html) - Specifies whether to inverse the spark line chart.
* [`highPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/highPointColor.html) - Specifies the high point color.
* [`lowPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/lowPointColor.html) - Specifies the low point color.
* [`negativePointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/negativePointColor.html) - Specifies the negative point color.
* [`firstPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/firstPointColor.html) - Specifies the first point color.
* [`lastPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/lastPointColor.html) - Specifies the last point color.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/borderWidth.html) - Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkBarChart/borderColor.html) - Changes the stroke color of the series.

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

#### See Also

* [Export Flutter Spark bar charts as a pdf](https://www.syncfusion.com/kb/12914/how-to-export-flutter-spark-bar-charts-as-a-pdf-sfsparkbarchart).

* [Customize the Flutter Spark bar charts](https://www.syncfusion.com/kb/12363/how-to-customize-the-flutter-spark-bar-charts-sfsparkbarchart).

## WinLoss Sparkline chart

[`SfSparkWinLossChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart-class.html) is used to show whether each value is positive or negative visualizing a Win/Loss scenario. 

The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/color.html) - Specifies the spark line color.
* [`data`]()  - Create the spark line chart with custom data source.
* [`axisCrossesAt`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/axisCrossesAt.html) - Specifies the axis line's position.
* [`axisLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/axisLineColor.html) - Specifies the color of the axis line.
* [`axisLineWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/axisLineWidth.html) - Specifies the width of the axis line.
* [`axisLineDashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/axisLineDashArray.html) - Specifies the dash array value of the axis line.
* [`trackball`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/trackball.html) - Represents the trackball options of spark bar chart.
* [`isInversed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/isInversed.html) - Specifies whether to inverse the spark line chart.
* [`highPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/highPointColor.html) - Specifies the high point color.
* [`lowPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/lowPointColor.html) - Specifies the low point color.
* [`negativePointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/negativePointColor.html) - Specifies the negative point color.
* [`firstPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/firstPointColor.html) - Specifies the first point color.
* [`lastPointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/lastPointColor.html) - Specifies the last point color.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/borderWidth.html) - Changes the stroke width of the win loss chart.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/borderColor.html) - Changes the stroke color of the win loss chart.
* [`tiePointColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart/tiePointColor.html) - Specifies the tie point color of win loss chart. color.

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
