---
layout: post
title: Methods in Flutter Pyramid Chart widget | Syncfusion 
description: Learn here all about available Methods of Syncfusion Flutter Pyramid Chart(SfPyramidChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Methods in Flutter Pyramid Chart (SfPyramidChart)

## PixelToPoint 

Converts logical pixel value to the data point value.
 
The [`pixelToPoint`](~) method takes logical pixel value as input and returns a chart data point.
 

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
          series: PyramidSeries<ChartSampleData, String>(
            dataSource: data,
            onRendererCreated: (PyramidSeriesController pyramidSeriesController) {
              seriesController = pyramidSeriesController;
              },
            xValueMapper: (ChartSampleData sales, _) => sales.x,
            yValueMapper: (ChartSampleData sales, _) => sales.y
          )
        ),
      );
    }

    class ChartSampleData{
      ChartSampleData(this.x, this.y);
      final String x;
      final double? y;
    }


{% endhighlight %}

