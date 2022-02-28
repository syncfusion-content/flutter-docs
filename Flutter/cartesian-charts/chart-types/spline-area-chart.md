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
            final List<ChartData> chartData = <ChartData>[
            ChartData(2010, 10.53, 3.3),
            ChartData(2011, 9.5, 5.4),
            ChartData(2012, 10, 2.65),
            ChartData(2013, 9.4, 2.62),
            ChartData(2014, 5.8, 1.99),
            ChartData(2015, 4.9, 1.44),
            ChartData(2016, 4.5, 2),
            ChartData(2017, 3.6, 1.56),
            ChartData(2018, 3.43, 2.1),
            ];
        return Scaffold(
            body: Center(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            SplineAreaSeries<ChartData, int>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y
                            ),
                            SplineAreaSeries<ChartData, int>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y1
                            ),
                        ]
                    )
                )
            );
        }
    class ChartData {
      ChartData(this.x, this.y, this.y1);
      final int x;
      final double y;
      final double y1;
    }

{% endhighlight %}

![Spline area chart](cartesian-chart-types-images/spline_area.png)

##	Spline area rendering types

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
        final List<ChartData> chartData = <ChartData>[
            ChartData(2010, 10.53),
            ChartData(2011, 9.5),
            ChartData(2012, 10),
            ChartData(2013, 9.4),
            ChartData(2014, 5.8),
            ChartData(2015, 4.9),
            ChartData(2016, 4.5),
            ChartData(2017, 3.6),
            ChartData(2018, 3.43),
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            SplineAreaSeries<ChartData, int>(
                                dataSource: chartData,
                                splineType: SplineType.cardinal,
                                cardinalSplineTension: 0.9,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Spline area type](cartesian-chart-types-images/spline_area_types.png)

## Dashed spline area

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of the [`SplineAreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineAreaSeries-class.html) is used to render spline area series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = <ChartData>[
            ChartData(2010, 10.53),
            ChartData(2011, 9.5),
            ChartData(2012, 10),
            ChartData(2013, 9.4),
            ChartData(2014, 5.8),
            ChartData(2015, 4.9),
            ChartData(2016, 4.5),
            ChartData(2017, 3.6),
            ChartData(2018, 3.43),
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            SplineAreaSeries<ChartData, int>(
                                dataSource: chartData,
                                dashArray: <double>[5, 5],
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Dashed spline area chart](cartesian-chart-types-images/spline_area_dashed.png)



#### See Also

* [color palette](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#color-palette) 
* [color mapping](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#color-mapping-for-data-points)
* [animation](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#animation)
* [gradient](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#gradient-fill)
* [empty points](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#empty-points)
* [Sorting](https://help.syncfusion.com/flutter/cartesian-charts/series-customization##sorting)