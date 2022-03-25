---
layout: post
title: Customization in Flutter Pyramid Chart widget | Syncfusion 
description: Learn here all about Customization of Syncfusion Flutter Pyramid Chart (SfPyramidChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Customization in Flutter Pyramid Chart (SfPyramidChart)

To render a pyramid chart, create an instance of [`PyramidSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/series.html) property of [`SfPyramidChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart-class.html). The following properties can be used to customize the appearance of a pyramid segment.

* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/borderColor.html) - changes the stroke color of the series.
* [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/pointColorMapper.html) - maps the color from data source.

{% tabs %}
{% highlight Dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                            dataSource: [
                                ChartData('Walnuts', 654),
                                ChartData('Almonds', 575),
                                ChartData('Soybeans', 446),
                                ChartData('Black beans', 341),
                                ChartData('Mushrooms', 296),
                                ChartData('Avacado', 160),
                            ],
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y)
                    )
                )
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.y);
            final String x;
            final double y;
    }

{% endhighlight %}
{% endtabs %}

![Pyramid chart](images/pyramid-charts/pyramid.jpg)

## Pyramid modes

You can render the pyramid series as [`PyramidMode.linear`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidMode.html) or [`PyramidMode.surface`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidMode.html) mode. In linear mode, the height of the pyramid segment is based on the Y value, and in surface mode, area of the pyramid segment is based on the Y value. The default value of [`PyramidMode.pyramidMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidMode.html) property is [`PyramidMode.linear`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidMode.html).

{% highlight dart hl_lines="8" %}  

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                            pyramidMode: PyramidMode.surface,
                            dataSource: [
                                ChartData('Walnuts', 654),
                                ChartData('Almonds', 575),
                                ChartData('Soybeans', 446),
                                ChartData('Black beans', 341),
                                ChartData('Mushrooms', 296),
                                ChartData('Avacado', 160),
                            ],
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y)
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Pyramid chart](images/pyramid-charts/pyramid_surface.jpg)

## Changing pyramid size

You can modify the size of pyramid series using the [`height`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/height.html) and [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/width.html) properties. It ranges from 0% to 100%.

{% highlight dart hl_lines="8 9" %}  

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                            height: '50%',
                            width: '50%',
                            dataSource: [
                                ChartData('Walnuts', 654),
                                ChartData('Almonds', 575),
                                ChartData('Soybeans', 446),
                                ChartData('Black beans', 341),
                                ChartData('Mushrooms', 296),
                                ChartData('Avacado', 160),
                            ],
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y)
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Pyramid size](images/pyramid-charts/pyramid_size.jpg)

## Gap between segments

You can control the gap between the two segments using the [`gapRatio`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/gapRatio.html) property. It ranges from 0 to 1.

{% highlight dart hl_lines="8" %}  

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                            gapRatio: 0.1,
                            dataSource: [
                                ChartData('Walnuts', 654),
                                ChartData('Almonds', 575),
                                ChartData('Soybeans', 446),
                                ChartData('Black beans', 341),
                                ChartData('Mushrooms', 296),
                                ChartData('Avacado', 160),
                            ],
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y)
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Pyramid gap](images/pyramid-charts/pyramid_gap.jpg)

## Explode segments

You can explode a pyramid segment using the [`explodeIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/explodeIndex.html) property. The [`explodeOffset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/explodeOffset.html) property is used to specify the exploded segment’s distance.

Also, the segments can be exploded by tapping the segment.

{% highlight dart hl_lines="8 9 10" %}  

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                            explode: true,
                            explodeOffset: '5%',
                            explodeIndex: 2,
                            dataSource: [
                                ChartData('Walnuts', 654),
                                ChartData('Almonds', 575),
                                ChartData('Soybeans', 446),
                                ChartData('Black beans', 341),
                                ChartData('Mushrooms', 296),
                                ChartData('Avacado', 160),
                            ],
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y)
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Explode](images/pyramid-charts/pyramid_explode.jpg)

## Applying palette color

The [`palette`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/palette.html) property is used to define colors for the series available in chart. By default, a set of 10 colors is predefined for applying it to the series. If the colors specified in the series are less than the number of series, then the remaining series will be filled with the specified palette colors rotationally.

{% tabs %}
{% highlight Dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        palette: <Color>[
                            Colors.teal,
                            Colors.orange,
                            Colors.brown
                        ],
                        series: PyramidSeries<ChartData, String>(
                            dataSource: [
                                ChartData('Walnuts', 654),
                                ChartData('Almonds', 575),
                                ChartData('Soybeans', 446),
                                ChartData('Black beans', 341),
                                ChartData('Mushrooms', 296),
                                ChartData('Avacado', 160),
                            ],
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y)
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Palette](images/pyramid-charts/pyramid_palette.jpg)
