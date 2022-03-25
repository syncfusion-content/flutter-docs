---
layout: post
title: Appearance customization in Flutter Funnel Chart widget | Syncfusion 
description: Learn here all about Appearance customization of Syncfusion Flutter Funnel Chart (SfFunnelChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Appearance customization in Flutter Funnel Chart (SfFunnelChart)

## Chart sizing

Chart renders based on the parent widget size. If you need the chart to be rendered in specific size, then set the size(width/height) to the parent widget.

{% tabs %}
{% highlight dart hl_lines="13 14" %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: Center(
            child: Container(
              height: 300,
              width: 350,
              child: SfFunnelChart()
            )
           )
          )
        );
    }

{% endhighlight %}

## Chart margin

Margin to the chart can be specified using the [`margin`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/margin.html) property.

{% tabs %}
{% highlight dart hl_lines="9" %} 

    @override
      Widget build(BuildContext context) {
        List<ChartData> chartData = [
          ChartData('Jan', 35),
          ChartData('Feb', 28),
          ChartData('Mar', 38),
          ChartData('Apr', 32),
          ChartData('May', 40)
        ];
        return Scaffold(
          body: SafeArea(
            child: Center(
              child: Container(
                height: 300,
                width: 350,
                child: SfFunnelChart(
                  borderColor: Colors.red,
                  borderWidth: 2,
                  // Sets 15 logical pixels as margin for all the 4 sides.
                  margin: EdgeInsets.all(15)
                  ),
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

![margin](images\chart-title\chart_margin.png)


## Chart area customization

You can customize the area of the chart using the below properties.

* [`backgroundColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/backgroundColor.html) - used to change the chart area background color.
* [`backgroundImage`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/backgroundImage.html) - used to set the image path.

{% tabs %}
{% highlight Dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              height: 300, 
              width: 350, 
              child: SfFunnelChart(
                borderColor: Colors.red,
                borderWidth: 2,
                margin: EdgeInsets.all(15),
                backgroundColor: Colors.lightGreen,
                backgroundImage: const AssetImage('images/train.png'),
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

![margin](images\chart-title\background_image.png)
