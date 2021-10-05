---
layout: post
title: Methods in Flutter Pyramid Chart widget | Syncfusion 
description: Learn here all about available methods of Syncfusion Flutter Pyramid Chart(SfPyramidChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Methods in Flutter Pyramid Chart (SfPyramidChart)

## PixelToPoint 

Converts logical pixel value to the data point value.
 
The [`pixelToPoint`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeriesController/pixelToPoint.html) method takes logical pixel value as input and returns a chart data point.
 
 >Note :- The method will return the center value of the segment.

{% highlight dart %}

    //Initialize the series controller
    PyramidSeriesController? seriesController;

    @override
    Widget build(BuildContext context) {
      return Container(
        child: SfPyramidChart(
          onChartTouchInteractionDown: (ChartTouchInteractionArgs args) {
            final Offset value = Offset(args.position.dx, args.position.dy);
            final PointInfo<dynamic>? chartpoint = seriesController?.pixelToPoint(value);
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

