---
layout: post
title: Histogram Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about histogram chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Histogram Chart in Flutter Cartesian Charts (SfCartesianChart)

Histogram chart is a graphical representation that organizes a group of data points into user-specified ranges. It is similar in appearance to a bar chart. The histogram condenses a data series into an easily interpreted visual by taking many data points and grouping them into logical ranges.

To render a histogram chart, create an instance of [`HistogramSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HistogramSeries-class.html) and add to the series collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html).

You can customize intervals using the [`binInterval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HistogramSeries/binInterval.html) property. Interval value by which the data points are grouped and rendered as bars, in histogram series.

For example, if the [`binInterval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HistogramSeries/binInterval.html) is set to 20, the x-axis will split with 20 as the interval. The first bar in the histogram represents the count of values lying between 0 to 20 in the provided data and the second bar will represent 20 to 40.

If no value is specified for this property, then the interval will be calculated automatically based on the data points count and value.

You can collapse the normal distribution curve using the [`showNormalDistributionCurve`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HistogramSeries/showNormalDistributionCurve.html) property. You can use the following properties to customize the appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.
* [`curveColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HistogramSeries/curveColor.html) - changes the color of the normal distribution curve.
* [`curveWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HistogramSeries/curveWidth.html) - changes the width of the normal distribution curve.
* [`curveDashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HistogramSeries/curveDashArray.html) - renders the normal distribution curve  with dashes.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(series: <ChartSeries>[
                HistogramSeries<ChartData, num>(
                 dataSource: <ChartData>[
                    ChartData(5.250),
                    ChartData(7.750),
                    ChartData(0.0),
                    ChartData(8.275),
                    ChartData(9.750),
                    ChartData(7.750),
                    ChartData(8.275),
                    ChartData(6.250),
                    ChartData(5.750),
                    ChartData(5.250),
                    ChartData(23.000),
                    ChartData(26.500),
                    ChartData(26.500),
                    ChartData(27.750),
                    ChartData(25.025),
                    ChartData(26.500),
                    ChartData(28.025),
                    ChartData(29.250),
                    ChartData(26.750),
                    ChartData(27.250),
                    ChartData(26.250),
                    ChartData(25.250),
                    ChartData(34.500),
                    ChartData(25.625),
                    ChartData(25.500),
                    ChartData(26.625),
                    ChartData(36.275),
                    ChartData(36.250),
                    ChartData(26.875),
                    ChartData(40.000),
                    ChartData(43.000),
                    ChartData(46.500),
                    ChartData(47.750),
                    ChartData(45.025),
                    ChartData(56.500),
                    ChartData(56.500),
                    ChartData(58.025),
                    ChartData(59.250),
                    ChartData(56.750),
                    ChartData(57.250),
                    ChartData(46.250),
                    ChartData(55.250),
                    ChartData(44.500),
                    ChartData(45.525),
                    ChartData(55.500),
                    ChartData(46.625),
                    ChartData(46.275),
                    ChartData(56.250),
                    ChartData(46.875),
                    ChartData(43.000),
                    ChartData(46.250),
                    ChartData(55.250),
                    ChartData(44.500),
                    ChartData(45.425),
                    ChartData(55.500),
                    ChartData(56.625),
                    ChartData(46.275),
                    ChartData(56.250),
                    ChartData(46.875),
                    ChartData(43.000),
                    ChartData(46.250),
                    ChartData(55.250),
                    ChartData(44.500),
                    ChartData(45.425),
                    ChartData(55.500),
                    ChartData(46.625),
                    ChartData(56.275),
                    ChartData(46.250),
                    ChartData(56.875),
                    ChartData(41.000),
                    ChartData(63.000),
                    ChartData(66.500),
                    ChartData(67.750),
                    ChartData(65.025),
                    ChartData(66.500),
                    ChartData(76.500),
                    ChartData(78.025),
                    ChartData(79.250),
                    ChartData(76.750),
                    ChartData(77.250),
                    ChartData(66.250),
                    ChartData(75.250),
                    ChartData(74.500),
                    ChartData(65.625),
                    ChartData(75.500),
                    ChartData(76.625),
                    ChartData(76.275),
                    ChartData(66.250),
                    ChartData(66.875),
                    ChartData(80.000),
                    ChartData(85.250),
                    ChartData(87.750),
                    ChartData(89.000),
                    ChartData(88.275),
                    ChartData(89.750),
                    ChartData(97.750),
                    ChartData(98.275),
                    ChartData(96.250),
                    ChartData(95.750),
                    ChartData(95.250)],
                showNormalDistributionCurve: true,
                curveColor: const Color.fromRGBO(192, 108, 132, 1),
                binInterval: 20,
                width: 0.99,
                curveWidth: 2.5,
                yValueMapper: (ChartData sales, _) => sales.x as double)]))));
        }
    }

        class ChartData {
            ChartData(this.x);
            final dynamic x;
        }

{% endhighlight %}

![histogram chart](cartesian-chart-types-images/Histogram.png)
