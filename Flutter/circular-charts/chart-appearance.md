---
layout: post
title: Customizing the appearance of Syncfusion Circular Charts
description: Learn how to customize the appearance of SfCircular Charts and the customizing properties available in SfCircular charts.
platform: flutter
control: Chart
documentation: ug
---

# Appearance of Circular charts

## Chart sizing

Chart renders based on the parent widget size. If you need the chart to be rendered in specific size, then set the size(width/height) to the parent widget. By default initializing only the [`SfCircularChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html) without defining any of its properties renders a white screen.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              height: 300, // height of the Container widget
              width: 350,  // width of the Container widget
              child: SfCircularChart()
            )
          )
        )
      );
    }

{% endhighlight %}

## Chart margin

Margin to the chart can be specified using the [`margin`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/margin.html) property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
        child: Container(
          height: 300, 
          width: 350, 
          child: SfCircularChart(
              borderColor: Colors.red,
              borderWidth: 2,
              // Sets 15 logical pixels as margin for all the 4 sides.
              margin: EdgeInsets.all(15)
          )
        )
      );
    }

{% endhighlight %}

## Chart area customization

You can customize the Area of the chart using the below properties.

* [`backgroundColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/backgroundColor.html) - used to change the Chart area background color.
* [`backgroundImage`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/backgroundImage.html) - used to set the image path.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/borderWidth.html) - used to change chart area the border width.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/bordeColor.html) - used to change the chart area border color.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              height: 300, 
              width: 350, 
              child: SfCircularChart(
                backgroundColor: Colors.lightGreen,
                backgroundImage: 'images/livechart.png',
              )
            )
          )
        )
      );
    }

{% endhighlight %}