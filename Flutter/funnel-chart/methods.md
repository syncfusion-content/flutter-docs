---
layout: post
title: Methods in Flutter Funnel Chart | Syncfusion®
description: The methods in Flutter Funnel Chart documentation provide publicly accessible APIs for performing chart-related operations programmatically.
platform: flutter
control: Chart
documentation: ug
---

# Methods in Flutter Funnel Chart

## PixelToPoint 

Converts a logical pixel value to a data point value.
 
The [`pixelToPoint`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeriesController/pixelToPoint.html) method takes a logical pixel value as input and returns a chart data point.

>**Note**: The method returns the center value of the segment.

{% tabs %}
{% highlight dart %}

    // Initialize the series controller
    FunnelSeriesController? seriesController;

    @override
    Widget build(BuildContext context) {
      return Container(
        child: SfFunnelChart(
          onChartTouchInteractionDown: (ChartTouchInteractionArgs args) {
            final Offset value = Offset(args.position.dx, args.position.dy);
            final PointInfo<dynamic>? chartPoint = seriesController?.pixelToPoint(value);
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

