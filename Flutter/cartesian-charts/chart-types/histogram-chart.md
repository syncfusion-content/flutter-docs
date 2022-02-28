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
{% include relative code-snippet/data.dart %}

        @override
        Widget build(BuildContext context) {
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

{% endhighlight %}

![histogram chart](cartesian-chart-types-images/Histogram.png)

#### See Also

* [Color palette](./series-customization#color-palette) 
* [Color mapping](./series-customization#color-mapping-for-data-points)
* [Animation](./series-customization#animation)
* [Gradient](./series-customization#gradient-fill)
* [Empty points](./series-customization#empty-points)  
* [Sorting](./series-customization##sorting) 