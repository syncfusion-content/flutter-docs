---
layout: post
title: Customizing the appearance of Syncfusion Flutter Charts
description: Learn how to customize the appearance of Chart.
platform: flutter
control: Chart
documentation: ug
---

# Appearance

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
              child: SfCartesianChart()
            )
          )
        )
      );
    }

{% endhighlight %}

![Chart size](images/appearance/chart_sizing.jpg)

## Chart margin

Margin to the chart can be specified using the [`margin`]() property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
        child: Container(
          height: 300, 
          width: 350, 
          child: SfCartesianChart(
              borderColor: Colors.red,
              borderWidth: 2,
              margin: EdgeInsets.all(15)
          )
        )
      );
    }

{% endhighlight %}

![Chart Margin](images/appearance/chart_margin.jpg)

## Plot area customization

You can customize the plot area of the chart using the below properties.

* [`plotAreaBackgroundColor`]() – used to change the plot area background color.
* [`plotAreaBorderColor`]() – used to change the stroke width of the plot area.
* [`plotAreaBorderWidth`]() – used to change the stroke color of the plot area.
* [`plotAreaBackgroundImageUrl`]() - used to set the image path.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              height: 300, 
              width: 350, 
              child: SfCartesianChart(
                plotAreaBorderWidth: 5,
                plotAreaBorderColor: Colors.red,
                plotAreaBackgroundColor: Colors.lightGreen,
                plotAreaBackgroundImageUrl: 'images/livechart.png'
              )
            )
          )
        )
      );
    }

{% endhighlight %}

![Chart plot area](images/appearance/plot_area_customization.jpg)