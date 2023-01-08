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

{% tabs %}
{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData(2010, 32),
            ChartData(2011, 40),
            ChartData(2012, 34),
            ChartData(2013, 52),
            ChartData(2014, 42),
            ChartData(2015, 38),
            ChartData(2016, 41),
        ];
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
{% endtabs %}

![Scatter chart](cartesian-chart-types-images/scatter.jpg)

##	Change shape and size of the scatter

The [`shape`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/shape.html) property is used to change the rendering shape of scatter series. The available shapes are [`circle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`rectangle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`pentagon`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`verticalLine`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`horizontalLine`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`diamond`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`triangle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), [`image`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html), and [`invertedTriangle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/DataMarkerType.html). If [`image`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/image.html) shape is specified, then you can assign the image using the [`image`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/image.html) property.

The [`height`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/height.html) and [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/width.html) properties of [`markerSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/markerSettings.html) can be used to change the height and width of the scatter series, respectively.

{% tabs %}
{% highlight dart hl_lines="17" %} 
    
    @override
    Widget build(BuildContext context) {
         final List<ChartData> chartData = [
            ChartData(2010, 32),
            ChartData(2011, 40),
            ChartData(2012, 34),
            ChartData(2013, 52),
            ChartData(2014, 42),
            ChartData(2015, 38),
            ChartData(2016, 41),
        ];
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
{% endtabs %}

![Scatter shape](cartesian-chart-types-images/scatter_shape.jpg)

#### See Also

* [Color palette](/flutter/cartesian-charts/series-customization#color-palette) 
* [Color mapping](/flutter/cartesian-charts/series-customization#color-mapping-for-data-points)
* [Animation](/flutter/cartesian-charts/series-customization#animation)
* [Gradient](/flutter/cartesian-charts/series-customization#gradient-fill)
* [Empty points](/flutter/cartesian-charts/series-customization#empty-points)
* [Sorting](/flutter/cartesian-charts/series-customization#sorting)
