---
layout: post
title: Appearance customization in Flutter Pyramid Chart widget | Syncfusion 
description: Learn here all about Appearance customization of Syncfusion Flutter Pyramid Chart (SfPyramidChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Appearance customization in Flutter Pyramid Chart (SfPyramidChart)

## Chart sizing

The chart renders based on the parent widget size. If you need the chart to be rendered in a specific size, then set the size(width/height) to the parent widget.

{% tabs %}
{% highlight dart hl_lines="13 14" %} 

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = [
            ChartData('Jan', 35),
            ChartData('Feb', 28),
            ChartData('Mar', 38),
            ChartData('Apr', 32),
            ChartData('May', 40)
        ];
        return Scaffold(
          body: Center(
            child: Container(
              height: 300,
              width: 350,
              child: SfPyramidChart(
                series: PyramidSeries<ChartData, String>(
                dataSource: chartData,
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

## Chart margin

Margin to the chart can be specified using the [`margin`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/margin.html) property.

{% tabs %}
{% highlight dart hl_lines="9" %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
            child: Container(
              child: SfPyramidChart(
                borderColor: Colors.red,
              borderWidth: 2,
              margin: EdgeInsets.all(15),
              series: PyramidSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y)
              )
            )
          )
      );
    }

{% endhighlight %}
{% endtabs %}

![margin](images\chart-title\chart_margin.png)

## Chart area customization

You can customize the area of the chart using the below properties.

* [`backgroundColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/backgroundColor.html) - used to change the chart area background color.
* [`backgroundImage`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/backgroundImage.html) - used to set the image path.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
            child: Container(
              height: 300, 
              width: 350, 
              child: SfPyramidChart(
                backgroundColor: Colors.lightGreen,
                backgroundImage: AssetImage('images/liveChart.png'),
                series: PyramidSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,)
              )
            )
          )
        );
      }

{% endhighlight %}
{% endtabs %}

![customization](images\chart-title\customization.png)
