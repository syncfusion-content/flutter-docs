---
layout: post
title: Scatter Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about scatter chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Scatter Chart in Flutter Cartesian Charts (SfCartesianChart)

To render a scatter chart, create an instance of [`ScatterSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ScatterSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties can be used to customize the scatter segment appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <ChartSeries>[
                            // Renders scatter chart
                            ScatterSeries<ChartData, DateTime>(
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

![Scatter chart](cartesian-chart-types-images/scatter.jpg)

##	Change shape and size of the scatter

The [`shape`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/shape.html) property is used to change the rendering shape of scatter series. The available shapes are [`circle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`rectangle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`pentagon`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`verticalLine`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`horizontalLine`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`diamond`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`triangle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`image`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), and [`invertedTriangle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html). If [`image`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/image.html) shape is specified, then you can assign the image using the [`image`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/image.html) property.

The [`height`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/height.html) and [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/width.html) properties of [`markerSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/markerSettings.html) can be used to change the height and width of the scatter series, respectively.

{% highlight dart hl_lines="17" %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        series: <ChartSeries>[
                            ScatterSeries<ChartData, DateTime>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                markerSettings: MarkerSettings(
                                    height: 15,
                                    width: 15,
                                    // Scatter will render in diamond shape
                                    shape: DataMarkerType.diamond
                                )
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Scatter shape](cartesian-chart-types-images/scatter_shape.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the scatter series further.