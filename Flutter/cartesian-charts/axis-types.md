---
layout: post
title: Syncfusion Flutter Chart Axis types.
description: Learn how to customize the grid lines, tick lines, labels and title of a chart axis in Syncfusion Flutter charts.
platform: flutter
control: Chart
documentation: ug
---

# Axis types in Cartesian charts

Charts typically have two axes that are used to measure and categorize data: a vertical (Y) axis, and a horizontal (X) axis.

Vertical(Y) axis always uses numerical scale. Horizontal(X) axis supports the following types of scale:

* Category
* Numeric
* Date-time
* Logarithmic

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
                        primaryYAxis: NumericAxis() 
                    )
                )
            )
        );
    }

{% endhighlight %}

![Numeric axis](images/axis-types/numeric.jpg)

### Inversed numeric axis

By using  the [isInversed](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/isInversed.html) Property in Cartesian charts, the  numeric axis can be inverted.Axis is rendered from the minimum value to the maximum value by default, and can be inverted from the maximum value to the minimum value.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(isInversed: true), 
                        primaryYAxis: NumericAxis(isInversed: true) 
                    )
                )
            )
        );
    }

{% endhighlight %}

![Inversed Numeric axis](images/axis-types/inversed-numeric.png)

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
                            // axis interval is set to 10
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
                            // Additional range padding is applied to y axis
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

When the value of [`rangePadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/rangePadding.html) property is [`round`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartRangePadding-class.html), axis range will be rounded to the nearest possible numeric value.

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

The [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/NumericAxis/numberFormat.html) property of numeric axis formats the numeric axis labels with [`globalized label formats`](https://api.flutter.dev/flutter/intl/NumberFormat-class.html). The following code snippet demonstrates how to format numeric labels.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: NumericAxis(
                            // Y axis labels will be rendered with currency format
                            numberFormat: NumberFormat.simpleCurrency()
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Number format](images/axis-types/number_format.jpg)

Also refer [label format](./axis-customization#formatting-axis-label-content) and [date format](#formatting-the-labels-1) for formatting the labels further.


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
                            // Axis labels will be placed on the ticks
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

Category axis can also be rendered based on the index values of data source by setting the [`arrangeByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CategoryAxis/arrangeByIndex.html) property to true in the axis.

{% highlight dart %}

    final List<ChartData> chartData = [
        ChartData('John', 10),
        ChartData('David', 9),
        ChartData('Brit', 10),
    ];

    final List<ChartData> chartData2 = [
        ChartData('Anto', 11),
        ChartData('Peter', 12),
        ChartData('Parker', 8),
    ];

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(
                            // Axis will be rendered based on the index values
                            arrangeByIndex: true
                        ),
                        series: <ChartSeries<ChartData, String>>[
                            ColumnSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y,
                            ),
                            ColumnSeries<ChartData, String>(
                                dataSource: chartData2,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y,
                            )
                        ]
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
                            // Interval type will be months
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

### Double range support

Date-time axis [`interval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/interval.html) property can be customize using double value.

For example, if you are rendering a series with months in x-axis with an interval of 0.5, then the interval will be calculated in days. The interval calculation may vary depends upon the number of days in the month.


{% highlight dart %} 

     @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(
                             interval: 0.5,
                        )
                        primaryXAxis: NumericAxis()
                    )
                )
            )
        );
     }

{% endhighlight %}

![doublerange](images/axis-types/doublerange.png)

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

The [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DateTimeAxis/dateFormat.html) property formats the date-time axis labels. The default data-time axis label can be formatted with various built-in [`date formats`](https://api.flutter.dev/flutter/intl/DateFormat-class.html), which depend on the given data source.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(
                            // X axis labels will be rendered based on the below format
                            dateFormat: DateFormat.y()
                        )  
                    )
                )
            )
        );
    }

{% endhighlight %}

![Date format](images/axis-types/datetime_labelFormat.jpg)

Also refer [label format](./axis-customization#formatting-axis-label-content) and [number format](#formatting-the-labels) for formatting the labels further.

## Logarithmic axis

Logarithmic axis uses logarithmic scale and displays numbers as axis labels.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: NumericAxis(),
                        primaryYAxis: LogarithmicAxis() 
                    )
                )
            )
        );
    }

{% endhighlight %}

![Logarithmic axis](images/axis-types/logarthmic.jpg)

### Change logarithmic range

To customize the range of log axis, use the [`minimum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LogarithmicAxis/minimum.html), [`maximum`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LogarithmicAxis/maximum.html), and [`interval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/interval.html) properties. By default, the range will be calculated automatically based on the provided data.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: LogarithmicAxis(
                            minimum: 300,
                            maximum: 10000,
                            interval: 1,
                        )  
                    )
                )
            )
        );
    }

{% endhighlight %}

![Logarithmic range](images/axis-types/logarthmic_range.jpg)

### Change log base value

To customize the log base value, use the [`logBase`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LogarithmicAxis/logBase.html) property.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: LogarithmicAxis(
                           logBase: 5,
                        )  
                    )
                )
            )
        );
    }
     
{% endhighlight %}

![Logarithmic base](images/axis-types/log_base.jpg)

### Inversed logarithmic axis 

By using  the [isInversed](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/isInversed.html) Property in Cartesian charts, the  logarithmic axis can be inverted.Axis is rendered from the minimum value to the maximum value by default, and can be inverted from the maximum value to the minimum value.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: LogarithmicAxis(
                          isInversed:true,
                        )  
                    )
                )
            )
        );
    }
     
{% endhighlight %}

![Inversed logarithmic axis](images/axis-types/inversed-logarithmic.png) 

## See Also

* [Applying currency format to axis labels](https://www.syncfusion.com/kb/11519/how-to-apply-the-currency-format-to-the-axis-labels-sfcartesianchart).