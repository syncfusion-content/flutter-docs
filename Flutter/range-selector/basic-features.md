---
layout: post
title: Basic features for Syncfusion Flutter Range Selector | Syncfusion
description: This basic features section explains how to add the numeric and date range selector for flutter platform
platform: flutter
control: SfRangeSelector
documentation: ug
---

# Basic features of range selector
This section explains about how to add the numeric and date range selector.

## Minimum

The minimum value that the user can select. The default value of `min` property is 0.0. Must be less than the `max` value.

## Maximum

The maximum value that the user can select. The default value of `max` property is 1.0. Must be greater than the `min`.

## Initial values

The values that initially selected in the range selector. The range selector's thumb is drawn corresponding to this value.

N> For date values, the range selector does not have auto interval support. So, it is mandatory to set `interval`, `dateIntervalType`, and `dateFormat` for date values.

**Numeric range slider**

You must import the [`Chart`](https://pub.dev/packages/syncfusion_flutter_charts) package to use chart as a child in range selector.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 6.0);

DateTime dateTimeMin = DateTime(2002, 01, 01),
      dateTimeMax = DateTime(2011, 01, 01);
  final SfRangeValues _dateTimeValues =
  SfRangeValues(DateTime(2006, 01, 01), DateTime(2007, 01, 01));

  final List<Data> chartData = <Data>[
    Data(x: DateTime(2002, 01, 01), y: 2.2),
    Data(x: DateTime(2003, 01, 01), y: 3.4),
    Data(x: DateTime(2004, 01, 01), y: 2.8),
    Data(x: DateTime(2005, 01, 01), y: 1.6),
    Data(x: DateTime(2006, 01, 01), y: 2.3),
    Data(x: DateTime(2007, 01, 01), y: 2.5),
    Data(x: DateTime(2008, 01, 01), y: 2.9),
    Data(x: DateTime(2009, 01, 01), y: 3.8),
    Data(x: DateTime(2010, 01, 01), y: 1.4),
    Data(x: DateTime(2011, 01, 01), y: 3.1),
  ];

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSelector(
                    min: 0.0,
                    max: 10.0,
                    interval: 2,
                    showLabels: true,
                    showTicks: true,
                    initialValues: _values,
                    child: SfCartesianChart(
                        margin: const EdgeInsets.all(0),
                        primaryXAxis: DateTimeAxis(minimum: dateTimeMin,maximum: dateTimeMax,isVisible: false,),
                        primaryYAxis: NumericAxis(isVisible: false , maximum: 4),
                        plotAreaBorderWidth: 0,
                        series: <SplineAreaSeries<Data, DateTime>>[
                            SplineAreaSeries<Data, DateTime>(
                                dataSource: chartData,
                                    xValueMapper: (Data sales, _) => sales.x,
                                    yValueMapper: (Data sales, _) => sales.y)
                        ],
                    ),
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight Dart %}

class Data {
  Data({this.x, this.y});
  final DateTime x;
  final double y;
}

{% endhighlight %}
{% endtabs %}

**Date range slider**

You must add the [`intl`](https://pub.dev/packages/intl) package for using date format in the range slider.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2002, 01, 01), DateTime(2003, 01, 01));

DateTime dateTimeMin = DateTime(2002, 01, 01),
      dateTimeMax = DateTime(2011, 01, 01);
  final SfRangeValues _dateTimeValues =
  SfRangeValues(DateTime(2006, 01, 01), DateTime(2007, 01, 01));

  final List<Data> chartData = <Data>[
    Data(x: DateTime(2002, 01, 01), y: 2.2),
    Data(x: DateTime(2003, 01, 01), y: 3.4),
    Data(x: DateTime(2004, 01, 01), y: 2.8),
    Data(x: DateTime(2005, 01, 01), y: 1.6),
    Data(x: DateTime(2006, 01, 01), y: 2.3),
    Data(x: DateTime(2007, 01, 01), y: 2.5),
    Data(x: DateTime(2008, 01, 01), y: 2.9),
    Data(x: DateTime(2009, 01, 01), y: 3.8),
    Data(x: DateTime(2010, 01, 01), y: 1.4),
    Data(x: DateTime(2011, 01, 01), y: 3.1),
  ];

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSelector(
                    min: DateTime(2000, 01, 01, 00),
                    max: DateTime(2004, 12, 31, 24),
                    initialValues: _values,
                    interval: 1,
                    showLabels: true,
                    showTicks: true,
                    dateFormat: DateFormat.y(),
                    dateIntervalType: DateIntervalType.years,
                    child: SfCartesianChart(
                        margin: const EdgeInsets.all(0),
                        primaryXAxis: DateTimeAxis(minimum: dateTimeMin,maximum: dateTimeMax,isVisible: false,),
                        primaryYAxis: NumericAxis(isVisible: false , maximum: 4),
                        plotAreaBorderWidth: 0,
                        series: <SplineAreaSeries<Data, DateTime>>[
                            SplineAreaSeries<Data, DateTime>(
                                dataSource: chartData,
                                    xValueMapper: (Data sales, _) => sales.x,
                                    yValueMapper: (Data sales, _) => sales.y)
                        ],
                    ),
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight Dart %}

class Data {
  Data({this.x, this.y});
  final DateTime x;
  final double y;
}

{% endhighlight %}
{% endtabs %}

## Enabled

Controls the range selector’s state whether it is disabled or enabled.
