---
layout: post
title: Customization in Flutter Circular Charts widget | Syncfusion 
description: Learn here all about Customization of Syncfusion Flutter Circular Charts (SfCircularChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Customization in Flutter Circular Charts (SfCircularChart)

## Chart sizing

Chart renders based on the parent widget size. If you need the chart to be rendered in specific size, then set the size(width/height) to the parent widget. By default initializing only the [`SfCircularChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html) without defining any of its properties renders a white screen.

{% highlight dart hl_lines="8 10" %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              // height of the Container widget
              height: 300, 
              // width of the Container widget
              width: 350,  
              child: SfCircularChart()
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

## Chart margin

Margin to the chart can be specified using the [`margin`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/margin.html) property.

{% highlight dart hl_lines="13" %} 

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
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

## Chart area customization

You can customize the area of the chart using the below properties.

* [`backgroundColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/backgroundColor.html) - used to change the chart area background color.
* [`backgroundImage`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/backgroundImage.html) - used to set the image path.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/borderWidth.html) - used to change chart area the border width.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/borderColor.html) - used to change the chart area border color.

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
{% endtabs %}