---
layout: post
title: Axis customization in Syncfusion Flutter Sparkline
description: Learn how to customize the axis types, labels, min and max values, colors, width and dashArray of the SFSparkline chart axis.
platform: flutter
control: Sparkline
documentation: ug
---

# Axis customization in Sparkline charts

You can customize axis value types and min and max values of the sparkline.

## Change axis type of the sparkline

You can customize the spark line chart with custom data source. Here, we can use [`SfSparkLineChart.custom()`]() widget. By using this widget can we customize the different axis such as `numeric` , `DateTime`, `Category`.

### Numeric Axis

You can assign `Numeric` values to the sparkline by using custom datasource. Here, the [`dataCount`]() property will use.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
          padding: EdgeInsets.all(5),
          child: SfSparkLineChart.custom(
            axisLineWidth: 0,
            dataCount: 6,
            xValueMapper: (index) => data[index].xval,
            yValueMapper: (index) => data[index].yval, 
          )),
    );
    }
    final dynamic data = [
    SalesData(xval: 1, yval: 4),
    SalesData(xval: 2, yval: 4.5),
    SalesData(xval: 3, yval: 8),
    SalesData(xval: 4, yval: 7),
    SalesData(xval: 5, yval: 6),
    SalesData(xval: 6, yval: 8),
     ]; 
     }
 
    class SalesData {
    SalesData({this.xval, this.yval});
    final dynamic xval;
    final double yval;
     }

{% endhighlight %}

### DateTime Axis

You can assign `DateTime `values to the sparkline by using custom datasource. Here, the [`dataCount`]() property will use.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
          padding: EdgeInsets.all(5),
          child: SfSparkLineChart.custom(
            axisLineWidth: 0,
            dataCount: 6,
            xValueMapper: (index) => data[index].xval,
            yValueMapper: (index) => data[index].yval, 
          )),
    );
    }
    final dynamic data = [
    SalesData(xval: DateTime(2018, 0, 1), yval: 4),
    SalesData(xval: DateTime(2018, 0, 2), yval: 4.5),
    SalesData(xval: DateTime(2018, 0, 3), yval: 8),
    SalesData(xval: DateTime(2018, 0, 4), yval: 7),
    SalesData(xval: DateTime(2018, 0, 5), yval: 6),
    SalesData(xval: DateTime(2018, 0, 6), yval: 8),
     ]; 
     }
 
    class SalesData {
    SalesData({this.xval, this.yval});
    final dynamic xval;
    final double yval;
     }

{% endhighlight %}

### Category Axis

You can assign `Category `values to the sparkline by using custom datasource. Here, the [`dataCount`]() property will use.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
          padding: EdgeInsets.all(5),
          child: SfSparkLineChart.custom(
            axisLineWidth: 0,
            dataCount: 6,
            xValueMapper: (index) => data[index].xval,
            yValueMapper: (index) => data[index].yval, 
          )),
    );
    }
    final dynamic data = [
    SalesData(xval: 'Sun', yval: 4),
    SalesData(xval: 'Mon', yval: 4.5),
    SalesData(xval: 'Tue', yval: 8),
    SalesData(xval: 'Wed'), yval: 7),
    SalesData(xval: 'Thur', yval: 6),
    SalesData(xval: 'Fri', yval: 8),
     ]; 
     }
 
    class SalesData {
    SalesData({this.xval, this.yval});
    final dynamic xval;
    final double yval;
     }

{% endhighlight %}

### Axis line customization

Axis line of the sparkline can be customized by the following properties.

* [axisCrossesAt]() - Specifies the horizontal axis line position.
* [axisLineColor]() - Specifies the horizontal axis line color.
* [axisLineWidth]() - Specifies the horizontal axis line width.
* [axisLineDashArray]() - Specifies the axis line dash array.


{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
          padding: EdgeInsets.all(5),
          child: SfSparkLineChart.custom(
            axisLineWidth: 2,
            axisLineDashArray: <double>[5,3],
            axisCrossesAt: 14,
            dataCount: 6,
            xValueMapper: (index) => data[index].xval,
            yValueMapper: (index) => data[index].yval, 
          )),
    );
    }
    final dynamic data = [
    SalesData(xval: 'Sun', yval: 4),
    SalesData(xval: 'Mon', yval: 4.5),
    SalesData(xval: 'Tue', yval: 8),
    SalesData(xval: 'Wed'), yval: 7),
    SalesData(xval: 'Thur', yval: 6),
    SalesData(xval: 'Fri', yval: 8),
     ]; 
     }
 
    class SalesData {
    SalesData({this.xval, this.yval});
    final dynamic xval;
    final double yval;
     }

{% endhighlight %}
