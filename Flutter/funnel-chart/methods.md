---
layout: post
title: Methods in Flutter Funnel Chart widget | Syncfusion 
description: Learn here all about available Methods of Syncfusion Flutter Funnel Chart widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Methods in Flutter Funnel Chart (SfFunnelChart)

## PixelToPoint 

Converts logical pixel value to the data point value.
 
The [`pixelToPoint`](~) method takes logical pixel value as input and returns a chart data point.
 

{% highlight dart %}

    //Initialize the series controller
    FunnelSeriesController? seriesController;

    @override
    Widget build(BuildContext context) {
      return Container(
        child: SfFunnelChart(
          onChartTouchInteractionDown:   (ChartTouchInteractionArgs args) {
           final Offset value = Offset(args.position.dx, args.position.dy);
           final PointInfo<dynamic> chartpoint = seriesController.pixelToPoint(value);
           }, 
          series: FunnelSeries<ChartSampleData, String>(
            dataSource: data,
            onRendererCreated: (FunnelSeriesController funnelSeriesController) {
            seriesController = funnelSeriesController;
            }
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

## PointToPixel 

 Converts chart data point value to logical pixel value.

The [pointToPixel](~) method takes chart data point value as input and returns logical pixel value.

N> It returns the data point's center location value.
 
{% highlight dart %}

    //Initialize the series controller
    FunnelSeriesController? seriesController;

    @override
    Widget build(BuildContext context) {
      return Container(
        child: SfFunnelChart(
          onChartTouchInteractionDown: (ChartTouchInteractionArgs args) {
           PointInfo<dynamic> chartPoint = seriesController.pixelToPoint(args.position);
           final Offset pointOcation = seriesController.pointToPixel(chartPoint);
           }, 
          series: FunnelSeries<ChartSampleData, String>(
            dataSource: data,
            onRendererCreated: (FunnelSeriesController funnelSeriesController) {
            seriesController = funnelSeriesController;
           }
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
