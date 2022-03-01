---
layout: post
title: Step line Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about step line chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Step line Chart in Flutter Cartesian Charts (SfCartesianChart)

To render a step line chart, create an instance of [`StepLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StepLineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties can be used to customize the appearance of spline segment:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) - changes the stroke width of the line.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <ChartSeries>[
                            // Renders step line chart
                            StepLineSeries<ChartData, DateTime>(
                                dataSource: chartData,
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

![Step line chart](cartesian-chart-types-images/stepline.jpg)

## Dashed step line

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of the [`StepLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StepLineSeries-class.html) is used to render step line series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart hl_lines="12" %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <ChartSeries>[
                            StepLineSeries<ChartData, DateTime>(
                                dataSource: chartData,
                                // Dashes for step line
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

![Step line chart](cartesian-chart-types-images/dashed_stepline.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the step line series further.