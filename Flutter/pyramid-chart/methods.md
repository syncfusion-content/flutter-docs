---
layout: post
title: Methods in Flutter Pyramid Chart | Syncfusion®
description: The methods in Flutter Pyramid Chart documentation provide publicly accessible APIs for performing chart-related operations programmatically.
platform: flutter
control: Chart
documentation: ug
---

# Methods in Flutter Pyramid Chart

## PixelToPoint 

Converts a logical pixel value to the corresponding data point value.

The [`pixelToPoint`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeriesController/pixelToPoint.html) method takes logical pixel value as input and returns a chart data point.
 
 >**Note**: The method will return the center value of the segment.

{% tabs %}
{% highlight dart %}

    //Initialize the series controller
    PyramidSeriesController? seriesController;

    @override
    Widget build(BuildContext context) {
      return Container(
        child: SfPyramidChart(
          onChartTouchInteractionDown: (ChartTouchInteractionArgs args) {
            final Offset value = Offset(args.position.dx, args.position.dy);
            final PointInfo<dynamic>? chartPoint = seriesController?.pixelToPoint(value);
              },
          series: PyramidSeries<ChartData, String>(
            dataSource: data,
            onRendererCreated: (PyramidSeriesController pyramidSeriesController) {
              seriesController = pyramidSeriesController;
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

