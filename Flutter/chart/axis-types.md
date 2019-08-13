---
layout: post
title: Syncfusion Flutter Chart Axis
description: Learn how to customize the grid lines, tick lines, labels and title of a chart axis.
platform: flutter
control: Chart
documentation: ug
---

# Axis

Charts typically have two axis, that are used to measure and categorize data: a vertical (Y) axis, and a horizontal (X) axis.

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

![Numeric axis](images/axis-types/numeric.jpg)


### Customizing numeric range

To customize the range of an axis, you can use the [`minimum`]() and [`maximum`]() properties of [`NumericAxis`](). By default, nice range will be calculated automatically based on the provided data.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryYAxis: NumericAxis(
                     minimum: 10,
                     maximum: 50
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![Numeric axis range](images/axis-types/numeric_range.jpg)

### Customizing numeric interval

Axis interval can be customized using the [`interval`]() property of [`ChartAxis`](). By default, nice interval will be calculated based on the minimum and maximum value of the provided data.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryYAxis: NumericAxis(
                     interval: 10
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![Numeric axis interval](images/axis-types/numeric_interval.jpg)

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
                   primaryYAxis: NumericAxis(
                    rangePadding: ChartRangePadding.additional
                   )  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding additional](images/axis-types/numeric_additional.jpg)

**auto**

When the value of [`rangePadding`]() property is [`auto`](), the horizontal numeric axis takes none as padding calculation, while the vertical numeric axis takes normal as padding calculation. This is also the default value of rangePadding.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryYAxis: NumericAxis(
                     rangePadding: ChartRangePadding.auto
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding auto](images/axis-types/numeric_auto.jpg)

**none**

When the value of [`rangePadding`]() property is [`none`](), padding will not be applied to the axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryYAxis: NumericAxis(
                     rangePadding: ChartRangePadding.none
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

**normal**

When the value of [`rangePadding`]() property is [`normal`](), padding is applied to the axis based on default range calculation.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryYAxis: NumericAxis(
                     rangePadding: ChartRangePadding.normal
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding normal](images/axis-types/numeric_normal.jpg)

**round**

When the value of [`rangePadding`]() property is [`round`](), axis range will be rounded to the nearest possible date time value.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryYAxis: NumericAxis(
                     rangePadding: ChartRangePadding.round
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![RangePadding round](images/axis-types/numeric_round.jpg)

### Formatting the labels

The [`numberFormat`]() property of numeric axis formats the numeric axis labels with globalized label formats. The following code snippet illustrates how to format numeric labels.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   primaryYAxis: NumericAxis(
                     numberFormat: NumberFormat.simpleCurrency()
                   ),  
                )
            )
        ));
    }

{% endhighlight %}

![Number format](images/axis-types/number_format.jpg)

## Category axis

Category axis displays text labels instead of numbers. When the string values are bound to x values, then the x axis must be initialized with CategoryAxis.

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

![Category Axis](images/axis-types/category.jpg)

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
                       labelPlacement: LabelPlacement.onTicks
                   ), 
                )
            )
        ));
    }

{% endhighlight %}

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

![Fixed interval](images/axis-types/category_interval.jpg)

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

![Indexed category axis](images/axis-types/category_arrangebyIndex.jpg)

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

![DateTime axis](images/axis-types/datetime.jpg)

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
                       minimum: DateTime(2010),
                       maximum: DateTime(2020)
                   )
                )
            )
        ));
    }

{% endhighlight %}

![DateTime range](images/axis-types/datetime_range.jpg)

### Date time intervals

Date time intervals can be customized using [`interval`]() and [`intervalType`]() properties of the [`DateTimeAxis`](). For example, setting [`interval`]() as 2 and [`intervalType`]() as years will consider 2 years as interval.

Essential Chart supports the following types of interval for date time axis.
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

![DateTime range](images/axis-types/datetime_interval.jpg)

### Apply padding to range

Padding can be applied to the [`minimum`]() and [`maximum`]() extremes of range by using the RangePadding property. Date-time axis supports the following types of padding:

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

![Range padding none](images/axis-types/datetime_rangePadding_none.jpg)

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

![RangePadding round](images/axis-types/datetime_rangePadding_round.jpg)

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

![RangePadding round](images/axis-types/datetime_rangePadding_add.jpg)

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

![RangePadding normal](images/axis-types/datetime_rangePadding_normal.jpg)

### Formatting the labels

The [`dateFormat`]() property formats the date-time axis labels. The default data-time axis label can be formatted with various built-in date formats which depends on the given data source.

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

![Date format](images/axis-types/datetime_labelFormat.jpg)