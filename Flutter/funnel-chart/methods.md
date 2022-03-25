---
layout: post
title: Methods in Flutter Funnel Chart widget | Syncfusion 
description: Learn here all about available methods of Syncfusion Flutter Funnel Chart(SfFunnelChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Methods in Flutter Funnel Chart (SfFunnelChart)

## PixelToPoint 

Converts logical pixel value to the data point value.
 
The [`pixelToPoint`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeriesController/pixelToPoint.html) method takes logical pixel value as input and returns a chart data point.

>**Note**: The method will return the center value of the segment.

{% tabs %}
{% highlight Dart %}

    //Initialize the series controller
    FunnelSeriesController? seriesController;

    @override
    Widget build(BuildContext context) {
      return Container(
        child: SfFunnelChart(
          onChartTouchInteractionDown: (ChartTouchInteractionArgs args) {
            final Offset value = Offset(args.position.dx, args.position.dy);
            final PointInfo<dynamic>? chartpoint = seriesController?.pixelToPoint(value);
            },
          series: FunnelSeries<ChartData, String>(
            dataSource: data,
            onRendererCreated: (FunnelSeriesController funnelSeriesController) {
              seriesController = funnelSeriesController;
            },
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y
          )
        ),
      );
    }

     class ChartData{
        ChartData(this.x, this.y);
        final String x;
        final double y;
      }


{% endhighlight %}
{% endtabs %}

