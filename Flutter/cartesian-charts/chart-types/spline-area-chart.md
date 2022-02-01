---
layout: post
title: Spline area Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about spline area chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Spline area Chart in Flutter Cartesian Charts (SfCartesianChart)

To render a spline area chart, create an instance of [`SplineAreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineAreaSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties can be used to customize the appearance of spline area chart:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) - changes the stroke width of the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <ChartSeries>[
                            SplineAreaSeries<ChartData, DateTime>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales
                            ),
                            SplineAreaSeries<ChartData, DateTime>(
                                dataSource: chartData1,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales
                            ),
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Spline area chart](cartesian-chart-types-images/spline_area.png)

## Dashed spline area

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of the [`SplineAreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineAreaSeries-class.html) is used to render spline area series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <ChartSeries>[
                            SplineAreaSeries<ChartData, DateTime>(
                                dataSource: chartData,
                                dashArray: <double>[5, 5],
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Dashed spline area chart](cartesian-chart-types-images/spline_area_dashed.png)

###	Spline area rendering types

The `splineType` allows you to change the spline area curve in series. The following types can be used in `SplineAreaSeries`:

* natural
* monotonic
* cardinal
* clamped

By default, the value of `splineType` is `natural`.

The following code sample demonstrates how to set the `splineType` value to `cardinal`. When you set the cardinal type, you can specify the desired line tension of the `cardinal` spline using the `cardinalSplineTension` property. The value of this property ranges from 0 to 1.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <ChartSeries>[
                            SplineAreaSeries<ChartData, DateTime>(
                                dataSource: chartData,
                                splineType: SplineType.cardinal,
                                cardinalSplineTension: 0.9,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Spline area type](cartesian-chart-types-images/spline_area_types.png)