---
layout: post
title: Markers and data labels in Syncfusion Flutter Sparkline
description: Learn how to add the markers and data point labels to the series available in the Syncfusion Flutter Sparkline widget.
platform: flutter
control: Sparkline
documentation: ug
---

# Marker and data label

## Marker

[`SparklineMarker`]() are used to highlight the data point in [`SfSparkLineChart`](), [`SfSparkBarChart`]() and [`SfSparkAreaChart`](). 

You can use the following properties to customize the appearance:

* [`displayMode`]() - Toggles the visibility of the marker. Defaults to `none`
* [`borderWidth`]() - Represents the border width of the marker.
* [`color`]() - used to change the color of the marker.
* [`borderColor`]() - used to change the borderColor of the marker.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child:  SfSparkAreaChart(
                    marker: (displayMode: MarkerDisplayMode.none,
                    color: Colors.red),
            data: <double>[10,6,8,-5,11,5,-2,7,-3,6,8,10],
               )
             )
           );
         }

    class SalesData {
    SalesData(this.month, this.sales);
    final String month;
    final double sales;
    }

{% endhighlight %}

![Spark Area chart]()

### Customizing marker shapes

Markers can be assigned with different shapes using the [`shape`]() property. By default, markers are rendered with circle shape. The shapes of markers are listed below.

* circle,
* diamond,
* square,
* triangle,
* invertedTriangle

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child:  SfSparkAreaChart(
                    marker: (shape: MarkerShape.square),
            data: <double>[10,6,8,-5,11,5,-2,7,-3,6,8,10],
               )
             )
           );
         }

    class SalesData {
    SalesData(this.month, this.sales);
    final String month;
    final double sales;
    }

{% endhighlight %}

![Spark Area chart]()