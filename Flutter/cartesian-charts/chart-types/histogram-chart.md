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
        final List<ChartData1> histogramData = <ChartData1>[
        ChartData1(5.250),
        ChartData1(7.750),
        ChartData1(0.0),
        ChartData1(8.275),
        ChartData1(9.750),
        ChartData1(7.750),
        ChartData1(8.275),
        ChartData1(6.250),
        ChartData1(5.750),
        ChartData1(5.250),
        ChartData1(23.000),
        ChartData1(26.500),
        ChartData1(26.500),
        ChartData1(27.750),
        ChartData1(25.025),
        ChartData1(26.500),
        ChartData1(28.025),
        ChartData1(29.250),
        ChartData1(26.750),
        ChartData1(27.250),
        ChartData1(26.250),
        ChartData1(25.250),
        ChartData1(34.500),
        ChartData1(25.625),
        ChartData1(25.500),
        ChartData1(26.625),
        ChartData1(36.275),
        ChartData1(36.250),
        ChartData1(26.875),
        ChartData1(40.000),
        ChartData1(43.000),
        ChartData1(46.500),
        ChartData1(47.750),
        ChartData1(45.025),
        ChartData1(56.500),
        ChartData1(56.500),
        ChartData1(58.025),
        ChartData1(59.250),
        ChartData1(56.750),
        ChartData1(57.250),
        ChartData1(46.250),
        ChartData1(55.250),
        ChartData1(44.500),
        ChartData1(45.525),
        ChartData1(55.500),
        ChartData1(46.625),
        ChartData1(46.275),
        ChartData1(56.250),
        ChartData1(46.875),
        ChartData1(43.000),
        ChartData1(46.250),
        ChartData1(55.250),
        ChartData1(44.500),
        ChartData1(45.425),
        ChartData1(55.500),
        ChartData1(56.625),
        ChartData1(46.275),
        ChartData1(56.250),
        ChartData1(46.875),
        ChartData1(43.000),
        ChartData1(46.250),
        ChartData1(55.250),
        ChartData1(44.500),
        ChartData1(45.425),
        ChartData1(55.500),
        ChartData1(46.625),
        ChartData1(56.275),
        ChartData1(46.250),
        ChartData1(56.875),
        ChartData1(41.000),
        ChartData1(63.000),
        ChartData1(66.500),
        ChartData1(67.750),
        ChartData1(65.025),
        ChartData1(66.500),
        ChartData1(76.500),
        ChartData1(78.025),
        ChartData1(79.250),
        ChartData1(76.750),
        ChartData1(77.250),
        ChartData1(66.250),
        ChartData1(75.250),
        ChartData1(74.500),
        ChartData1(65.625),
        ChartData1(75.500),
        ChartData1(76.625),
        ChartData1(76.275),
        ChartData1(66.250),
        ChartData1(66.875),
        ChartData1(80.000),
        ChartData1(85.250),
        ChartData1(87.750),
        ChartData1(89.000),
        ChartData1(88.275),
        ChartData1(89.750),
        ChartData1(97.750),
        ChartData1(98.275),
        ChartData1(96.250),
        ChartData1(95.750),
        ChartData1(95.250)
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(series: <ChartSeries>[
                    HistogramSeries<ChartData1, double>(
                    dataSource: histogramData,
                    showNormalDistributionCurve: true,
                    curveColor: const Color.fromRGBO(192, 108, 132, 1),
                    binInterval: 20,
                    yValueMapper: (ChartData1 data, _) => data.y)]
                     )
                  )
               )
           );
       }
    }
    class ChartData1 {
        ChartData1(this.y);
        final double y;
    }


{% endhighlight %}

![histogram chart](cartesian-chart-types-images/Histogram.png)

#### See Also

* [Color palette](./series-customization#color-palette) 
* [Color mapping](./series-customization#color-mapping-for-data-points)
* [Animation](./series-customization#animation)
* [Gradient](./series-customization#gradient-fill)
* [Empty points](./series-customization#empty-points)  
* [Sorting](./series-customization##sorting) 