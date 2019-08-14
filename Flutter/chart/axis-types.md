---
layout: post
title: Syncfusion Flutter Chart Axis
description: Learn how to customize the grid lines, tick lines, labels and title of a chart axis.
platform: flutter
control: Chart
documentation: ug
---

# Axis

Charts typically have two axes that are used to measure and categorize data: a vertical (Y) axis, and a horizontal (X) axis.

Vertical(Y) axis always uses numerical scale. Horizontal(X) axis supports the following types of scale:

* Category
* Numeric
* Date-time

## Numeric axis

Numeric axis uses numerical scale and displays numbers as labels. By default, [`Numeric Axis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis-class.html) is set to both horizontal axis and vertical axis.

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
            )
        );
    }

{% endhighlight %}

![Numeric axis](images/axis-types/numeric.jpg)

### Customizing range

To customize the range of an axis, use the [`minimum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/minimum.html) and [`maximum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/maximum.html) properties of [`NumericAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/NumericAxis.html). By default, nice range will be calculated automatically based on the provided data.

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
                        )  
                    )
                )
            )
        );
    }

{% endhighlight %}

![Numeric axis range](images/axis-types/numeric_range.jpg)

### Customizing interval

Axis interval can be customized using the [`interval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/interval.html) property of [`ChartAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis-class.html). By default, nice interval will be calculated based on the minimum and maximum values of the provided data.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: NumericAxis(
                            interval: 10
                        ) 
                    )
                )
            )
        );
    }

{% endhighlight %}

![Numeric axis interval](images/axis-types/numeric_interval.jpg)

### Applying padding to the range

Padding can be applied to the minimum and maximum extremes of the axis range using the [`rangePadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangePadding.html) property. Numeric axis supports the following types of padding:

* additional
* auto
* none
* normal
* round

**additional**

When the value of [`rangePadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangePadding.html) property is [`additional`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartRangePadding-class.html), the axis range will be rounded and an interval of the axis will be added as padding to the minimum and maximum values of the range.

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
            )
        );
    }

{% endhighlight %}

![RangePadding additional](images/axis-types/numeric_additional.jpg)

**auto**

When the value of [`rangePadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangePadding.html) property is [`auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartRangePadding-class.html), the horizontal numeric axis takes none for padding calculation, whereas the vertical numeric axis takes normal for padding calculation. This is also the default value of rangePadding.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: NumericAxis(
                            rangePadding: ChartRangePadding.auto
                        )  
                    )
                )
            )
        );
    }

{% endhighlight %}

![RangePadding auto](images/axis-types/numeric_auto.jpg)

**none**

When the value of [`rangePadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangePadding.html) property is [`none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartRangePadding-class.html), padding will not be applied to the axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: NumericAxis(
                            rangePadding: ChartRangePadding.none
                        )  
                    )
                )
            )
        );
    }

{% endhighlight %}

**normal**

When the value of [`rangePadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangePadding.html) property is [`normal`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartRangePadding-class.html), padding is applied to the axis based on the default range calculation.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: NumericAxis(
                            rangePadding: ChartRangePadding.normal
                        )   
                    )
                )
            )
        );
    }

{% endhighlight %}

![RangePadding normal](images/axis-types/numeric_normal.jpg)

**round**

When the value of [`rangePadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangePadding.html) property is [`round`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartRangePadding-class.html), axis range will be rounded to the nearest possible date-time value.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: NumericAxis(
                            rangePadding: ChartRangePadding.round
                        )  
                    )
                )
            )
        );
    }

{% endhighlight %}

![RangePadding round](images/axis-types/numeric_round.jpg)

### Formatting the labels

The [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/numberFormat.html) property of numeric axis formats the numeric axis labels with globalized label formats. The following code snippet demonstrates how to format numeric labels.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: NumericAxis(
                            numberFormat: NumberFormat.simpleCurrency()
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Number format](images/axis-types/number_format.jpg)

## Category axis

Category axis displays text labels instead of numbers. When the string values are bound to x values, then the x-axis must be initialized with CategoryAxis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis()
                    )
                )
            )
        );
    }

{% endhighlight %}

![Category Axis](images/axis-types/category.jpg)

### Placing labels between the ticks

Labels in category axis can be placed on the ticks by setting the [`labelPlacement`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CategoryAxis/labelPlacement.html) to [`onTicks`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelPlacement-class.html). The default value of the [`labelPlacement`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CategoryAxis/labelPlacement.html) property is [`betweenTicks`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelPlacement-class.html). So, the labels will be placed between the ticks by default.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            labelPlacement: LabelPlacement.onTicks
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

### Displaying labels after a fixed interval

To display the labels after a fixed interval n, set the [`interval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/interval.html) property of ChartAxis to n. The default value of interval is null.

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
                        ) 
                    )
                )
            )
        );
    }

{% endhighlight %}

![Fixed interval](images/axis-types/category_interval.jpg)

### Indexed category axis

Category axis also can be rendered based on the index values of data source by setting the [`arrangeByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CategoryAxis/arrangeByIndex.html) property to true in the axis.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            arrangeByIndex: true
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Indexed category axis](images/axis-types/category_arrangebyIndex.jpg)

## Date-time axis

The date-time axis uses date-time scale and displays date-time values as axis labels in specified format.

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
            )
        );
    }

{% endhighlight %}

![DateTime axis](images/axis-types/datetime.jpg)

### Customizing range

To customize the range of an axis, use the [`minimum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/minimum.html) and [`maximum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/maximum.html) properties of [`DateTimeAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/DateTimeAxis.html). By default, nice range will be calculated automatically based on the provided data.

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
            )
        );
    }

{% endhighlight %}

![DateTime range](images/axis-types/datetime_range.jpg)

### Date-time intervals

The date-time intervals can be customized using the [`interval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/interval.html) and [`intervalType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/intervalType.html) properties of [`DateTimeAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/DateTimeAxis.html). For example, setting [`interval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/interval.html) as 2 and [`intervalType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/intervalType.html) as years will consider 2 years as interval.

The Flutter Chart supports the following types of interval for date-time axis:

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
            )
        );
    }

{% endhighlight %}

![DateTime range](images/axis-types/datetime_interval.jpg)

### Applying padding to range

Padding can be applied to the [`minimum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/minimum.html) and [`maximum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/maximum.html) extremes of a range using the `RangePadding` property. The date-time axis supports the following types of padding:

* none
* round 
* additional
* normal

**none**

When the value of [`rangePadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangePadding.html) property is [`none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartRangePadding-class.html), padding will not be applied to the axis.

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
            )
        );
    }

{% endhighlight %}

![Range padding none](images/axis-types/datetime_rangePadding_none.jpg)

**round**

When the value of [`rangePadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangePadding.html) property is [`round`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartRangePadding-class.html), axis range will be rounded to the nearest possible date-time value.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(
                            rangePadding: ChartRangePadding.round
                        ) 
                    )
                )
            )
        );
    }

{% endhighlight %}

![RangePadding round](images/axis-types/datetime_rangePadding_round.jpg)

**additional**

When the value of [`rangePadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangePadding.html) property is [`additional`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartRangePadding-class.html), range will be rounded and date-time interval of the axis will be added as padding to the minimum and maximum extremes of a range.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(
                            rangePadding: ChartRangePadding.additional
                        ) 
                    )
                )
            )
        );
    }

{% endhighlight %}

![RangePadding round](images/axis-types/datetime_rangePadding_add.jpg)

**normal**

When the value of [`rangePadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangePadding.html) property is [`normal`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartRangePadding-class.html), padding is applied to the axis based on the default range calculation.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(
                            rangePadding: ChartRangePadding.normal
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![RangePadding normal](images/axis-types/datetime_rangePadding_normal.jpg)

### Formatting the labels

The [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/dateFormat.html) property formats the date-time axis labels. The default data-time axis label can be formatted with various built-in date formats, which depend on the given data source.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(
                            dateFormat: DateFormat.y()
                        )  
                    )
                )
            )
        );
    }

{% endhighlight %}

![Date format](images/axis-types/datetime_labelFormat.jpg)
