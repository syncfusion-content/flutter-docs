---
layout: post
title: Customization in Flutter Funnel Chart widget | Syncfusion 
description: Learn here all about Customization of Syncfusion Flutter Funnel Chart (SfFunnelChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Customization in Flutter Funnel Chart (SfFunnelChart)

To render a funnel chart, create an instance of [`FunnelSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/series.html) property of [`SfFunnelChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart-class.html). The following properties are used to customize the appearance of a funnel segment:

* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/borderColor.html) - changes the stroke color of the series.
* [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/pointColorMapper.html) - Maps the color from data source.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        series: FunnelSeries<ChartData, String>(
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

![Funnel chart](images/funnel-charts/funnel.jpg)

## Changing funnel size

You can modify the size of funnel series using the [`height`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/height.html) and [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/width.html) properties. It ranges from 0% to 100%.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        series: FunnelSeries<ChartData, String>(
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
            );
        }

{% endhighlight %}
{% endtabs %}

![Funnel size](images/funnel-charts/funnel_size.jpg)

## Changing neck size

You can modify the neck size of funnel series using the [`neckHeight`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/neckHeight.html) and [`neckWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/neckWidth.html) properties. It ranges from 0% to 100%.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        series: FunnelSeries<ChartData, String>(
                            neckHeight: '40%',
                            neckWidth: '10%',
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

![Neck size](images/funnel-charts/neck_size.jpg)

## Gap between segments

You can control the gap between the two segments using the [`gapRatio`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/gapRatio.html) property. It ranges from 0 to 1.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        series: FunnelSeries<ChartData, String>(
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
            );
        }

{% endhighlight %}
{% endtabs %}

![Funnel gap](images/funnel-charts/funnel_gap.jpg)

## Explode segments

You can explode a funnel segment using the [`explodeIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/explodeIndex.html) property. The [`explodeOffset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/explodeOffset.html) property is used to specify the exploded segment’s distance.

Also, the segments can be exploded by tapping the segment.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        series: FunnelSeries<ChartData, String>(
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
            );
        }

{% endhighlight %}
{% endtabs %}

![Explode](images/funnel-charts/funnel_explode.jpg)

## Applying palette color

The [`palette`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/palette.html) property is used to define colors for the series available in chart. By default, a set of 10 colors is predefined for applying it to the series. If the colors specified in the series are less than the number of series, then the remaining series will be filled with the specified palette colors rotationally.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        palette: <Color>[
                            Colors.teal,
                            Colors.orange,
                            Colors.brown
                        ],
                        series: FunnelSeries<ChartData, String>(
                        dataSource: chartData,
                        xValueMapper: (ChartData data, _) => data.x,
                        yValueMapper: (ChartData data, _) => data.y,
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Palette](images/funnel-charts/funnel_palette.jpg)
