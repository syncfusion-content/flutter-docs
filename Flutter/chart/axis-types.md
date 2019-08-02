---
layout: post
title: Syncfusion Flutter Chart Axis
description: How to customize the grid lines, tick lines, labels and title of chart axis
platform: flutter
control: Chart
documentation: ug
---

# Axis

Charts typically have two axes that are used to measure and categorize data: a vertical (Y) axis, and a horizontal (X) axis.

Vertical(Y) axis always uses numerical scale. Horizontal(X) axis supports the following types of scale:

* Category
* Numeric
* Date time

## Numeric axis

Numeric axis uses numerical scale and displays numbers as labels. The default horizontal and vertical axis type is [`Numeric Axis`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: NumericAxis(), 
                   primaryYAxis: NumericAxis(), 
                )
            )
        ));
    }

{% endhighlight %}

![Numeric axis](images/getting-started/livechart.png)


### Customizing numeric range

To customize the range of an axis, you can use the [`minimum`]() and [`maximum`]() properties of [`NumericAxis`](). By default, nice range will be calculated automatically based on the provided data.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: NumericAxis(
                     minimum: 10,
                     maximum: 60
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![Numeric axis range](images/getting-started/livechart.png)

### Customizing numeric interval

Axis interval can be customized using the [`interval`]() property of [`ChartAxis`](). By default, nice interval will be calculated based on the minimum and maximum value of the provided data.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: NumericAxis(
                     interval: 2
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![Numeric axis interval](images/getting-started/livechart.png)

### Apply padding to the range

Padding can be applied to the minimum and maximum extremes of the axis range by using [`rangePadding`]() property. Numeric axis supports the following types of padding.

* additional
* auto
* none
* normal
* round

**additional**

When the value of [`rangePadding`]() property is [`additional`](), axis range will be rounded and an interval of the axis will be added as padding to the minimum and maximum values of the range.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: NumericAxis(
                     rangePadding: ChartRangePadding.additional
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding additional](images/getting-started/livechart.png)

**auto**

When the value of [`rangePadding`]() property is [`auto`](), the horizontal numeric axis takes none as padding calculation, while the vertical numeric axis takes normal as padding calculation. This is also the default value of rangePadding.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: NumericAxis(
                     rangePadding: ChartRangePadding.auto
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding auto](images/getting-started/livechart.png)

**none**

When the value of [`rangePadding`]() property is [`none`](), padding will not be applied to the axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: NumericAxis(
                     rangePadding: ChartRangePadding.none
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding none](images/getting-started/livechart.png)

**normal**

When the value of [`rangePadding`]() property is [`normal`](), padding is applied to the axis based on default range calculation.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: NumericAxis(
                     rangePadding: ChartRangePadding.normal
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding normal](images/getting-started/livechart.png)

**round**

When the value of [`rangePadding`]() property is [`round`](), axis range will be rounded to the nearest possible date time value.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: NumericAxis(
                     rangePadding: ChartRangePadding.round
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding round](images/getting-started/livechart.png)

### Formatting the labels

Formats the numeric axis labels with globalized label formats.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: NumericAxis(
                     numberFormat: NumberFormat.decimalPattern()
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![Number format](images/getting-started/livechart.png)

## Category axis

Category axis displays text labels instead of numbers.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: CategoryAxis(), 
                )
            )
        ));
    }

{% endhighlight %}

![Category Axis](images/getting-started/livechart.png)

### Placing labels between the ticks

Labels in category axis can be placed on the ticks by setting [`labelPlacement`]() to [`onTicks`](). Default value of [`labelPlacement`]() property is [`betweenTicks`]() i.e. labels will be placed between the ticks by default.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: CategoryAxis(
                       labelPlacement: LabelPlacement.betweenTicks
                   ), 
                )
            )
        ));
    }

{% endhighlight %}

![Label Placement](images/getting-started/livechart.png)

### Displaying labels after a fixed interval

To display labels after a fixed interval n, you can set [`interval`]() property of ChartAxis as n. Default value of interval is null

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: CategoryAxis(
                       labelPlacement: LabelPlacement.betweenTicks,
                       interval: 2
                   ), 
                )
            )
        ));
    }

{% endhighlight %}

![Fixed interval](images/getting-started/livechart.png)

### Indexed category axis

Category axis also can be rendered based on the index values of data source. This can be achieved by defining the [`arrangeByIndex`]() property to *true* in the axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: CategoryAxis(
                       arrangeByIndex: true
                   ), 
                )
            )
        ));
    }

{% endhighlight %}

![Indexed category axis](images/getting-started/livechart.png)

## Date time axis

Date time axis uses date time scale and displays date time values as axis labels in specified format.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: DateTimeAxis() 
                )
            )
        ));
    }

{% endhighlight %}

![DateTime axis](images/getting-started/livechart.png)

### Customizing date time range

To customize the range of an axis, you can use the [`minimum`]() and [`maximum`]() properties of [`DateTimeAxis`](). By default, nice range will be calculated automatically based on the provided data

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: DateTimeAxis(
                       minimum: DateTime(2000),
                       maximum: DateTime(2019)
                   )
                )
            )
        ));
    }

{% endhighlight %}

![DateTime range](images/getting-started/livechart.png)

### Date time intervals

Date time intervals can be customized using [`interval`]() and [`intervalType`]() properties of the [`DateTimeAxis`](). For example, setting Inter[`interval`]()val as 2 and [`intervalType`]() as years will consider 2 years as interval.

Essential Chart supports the following types of interval for date time axis

* auto
* years
* months
* days
* hours
* minutes
* seconds

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: DateTimeAxis(
                       intervalType: DateTimeIntervalType.months,
                    interval: 2
                   )
                )
            )
        ));
    }

{% endhighlight %}

![DateTime range](images/getting-started/livechart.png)

### Apply padding to range

Padding can be applied to the [`minimum`]() and ['maximum']() extremes of range by using the RangePadding property. Date-time axis supports the following types of padding:

* none
* round 
* additional
* normal

**none**

When the value of [`rangePadding`]() property is [`none`](), padding will not be applied to the axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: DateTimeAxis(
                      rangePadding: ChartRangePadding.none
                   )
                )
            )
        ));
    }

{% endhighlight %}

![Range padding none](images/getting-started/livechart.png)

**round**

When the value of [`rangePadding`]() property is [`round`](), axis range will be rounded to the nearest possible date time value.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: DateTimeAxis(
                     rangePadding: ChartRangePadding.round
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding round](images/getting-started/livechart.png)

**additional**

When the value of [`rangePadding`]() property is [`additional`](), range will be rounded and date time interval of the axis will be added as padding to the minimum and maximum extremes of the range.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: DateTimeAxis(
                     rangePadding: ChartRangePadding.additional
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding round](images/getting-started/livechart.png)

**normal**

When the value of [`rangePadding`]() property is [`normal`](), padding is applied to the axis based on default range calculation.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: DateTimeAxis(
                     rangePadding: ChartRangePadding.normal
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding normal](images/getting-started/livechart.png)

### Formatting the labels

The [`dateFormat`]() property formats the date-time axis labels. The default data-time axis label can be formatted with various built-in date formats.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryXAxis: DateTimeAxis(
                     dateFormat: DateFormat.y()
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![Date format](images/getting-started/livechart.png)

