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

Chart renders based on the parent widget size. If you need the chart to be rendered in specific size, then set the size(width/height) to the parent widget.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: Center(
            child: Container(
              height: 300,
              width: 350,
              child: SfPyramidChart()
            )
           )
          )
        );
    }

{% endhighlight %}

## Chart margin

Margin to the chart can be specified using the [`margin`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/margin.html) property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              height: 300,
              width: 350,
              child: SfPyramidChart(
                borderColor: Colors.red,
                borderWidth: 2,
                // Sets 15 logical pixels as margin for all the 4 sides.
                margin: EdgeInsets.all(15)
                )
              )
            )
          )
      );
    }

{% endhighlight %}

## Chart area customization

You can customize the area of the chart using the below properties.

* [`backgroundColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/backgroundColor.html) - used to change the chart area background color.
* [`backgroundImage`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/backgroundImage.html) - used to set the image path.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              height: 300, 
              width: 350, 
              child: SfPyramidChart(
                backgroundColor: Colors.lightGreen,backgroundImage: const AssetImage('images/livechart.png'),
              )
            )
          )
        )
      );
    }

{% endhighlight %}
