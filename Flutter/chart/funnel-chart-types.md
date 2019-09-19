---
layout: post
title: Syncfusion Funnel Chart Types
description: Learn how to customize funnel charts available in Syncfusion Flutter Chart.
platform: flutter
control: Chart
documentation: ug
---

# Funnel Chart Type

## Funnel chart

To render a funnel chart, create an instance of [`FunnelSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries-class.html) and add to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/series.html) property of [`SfFunnelChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart-class.html). You can use the following properties to customize the funnel segment appearance.

* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/opacity.html) - used to control the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/borderWidth.html) – used to change the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/borderColor.html) – used to change the stroke color of the series.
* [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/pointColorMapper.html) - used to map the color from data source

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
        ChartData(this.x, this.y, [this.color]);
            final String x;
            final double y;
            final Color color;
    }

{% endhighlight %}

![Funnel chart](images/funnel-charts/funnel.jpg)


### Changing funnel size

You can modify the size of funnel series using [`height`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/height.html) and [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/width.html) properties. It ranges from 0% to 100%.

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
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Funnel size](images/funnel-charts/funnel_size.jpg)


### Changing neck size

You can modify the neck size of funnel series using [`neckHeight`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/neckHeight.html) and [`neckWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/neckWidth.html) properties. It ranges from 0% to 100%.

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
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Neck size](images/funnel-charts/neck_size.jpg)

### Gap between segments

You can control the gap between the two segments using [`gapRatio`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/gapRatio.html) property. It ranges from 0 to 1.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        series: FunnelSeries<ChartData, String>(
                            gapRatio: 0.1,
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Funnel gap](images/funnel-charts/funnel_gap.jpg)

### Explode segments

You can explode a funnel segment using [`explodeIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/explodeIndex.html) property, and [`explodeOffset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/explodeOffset.html) property is used to specify the exploded segment’s distance.

Also, the segments can be exploded by tapping the segment.

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
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Explode](images/funnel-charts/funnel_explode.jpg)

### Smart data labels

The [`smartLabelMode`]() property can be used to place the data labels smartly. The following values are supported by [`smartLabelMode`]().

* [`shift`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SmartLabelMode-class.html) - shifts the data label position when intersect with other label and is the default value.
* [`none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SmartLabelMode-class.html) - renders all the data label when intersects.
* [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SmartLabelMode-class.html) - hide the intersect data label.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        smartLabelMode: SmartLabelMode.shift,
                        series: FunnelSeries<ChartData, String>(
                            dataLabelSettings: DataLabelSettings(
                                isVisible: true, 
                                labelPosition: LabelPosition.inside
                            ),
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

### Applying palette color

The [`palette`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/palette.html) property is used to define the colors for the series available in chart. By default, a set of 10 colors are predefined for applying it to the series. If the colors specified in the series are less than the number of series, than the remaining series are filled with the specified palette colors rotationally.

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
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Palette](images/funnel-charts/funnel_palette.jpg)