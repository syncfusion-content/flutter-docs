---
layout: post
title: Getting Started for Syncfusion Flutter Range Selector | Syncfusion
description: This section explains the steps required to add the range selector widget and its elements such as numeric and date values, ticks, labels and tooltips.
platform: flutter
control: SfRangeSelector
documentation: ug
---

# Getting Started for Range Selector
This section explains the steps required to add the range selector widget and its elements such as numeric and date values, ticks, labels and tooltips. This section covers only basic features needed to know to get started with Syncfusion range selector.

## Add flutter range selector to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion flutter range selector dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_sliders: ^18.1.0.36-beta

{% endhighlight %}

**Get packages** 

Run the following command to get the required packages.

{% highlight dart %}

$ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_sliders/sliders.dart';

{% endhighlight %}
{% endtabs %}

## Initialize range selector

After importing the package, initialize the range selector widget as a child of any widget. Here, the range slider widget is added as a child of the Container widget. The default value of the `min` and `max` property of the SfRangeSlider is 0.0 and 1.0 respectively. So, the `initialValues` property must be given within the range. You can add any kind of widget as a child of range selector. Here, [Chart](https://help.syncfusion.com/flutter/chart/getting-started) widget is added as a child.

{% tabs %}
{% highlight Dart %}

final SfRangeValues _initialValues = SfRangeValues(0.3, 0.7);

final List<Data> _chartData = <Data>[
  Data(x: DateTime(2003, 01, 01), y: 3.4),
  Data(x: DateTime(2004, 01, 01), y: 2.8),
  Data(x: DateTime(2005, 01, 01), y: 1.6),
  Data(x: DateTime(2006, 01, 01), y: 2.3),
  Data(x: DateTime(2007, 01, 01), y: 2.5),
  Data(x: DateTime(2008, 01, 01), y: 2.9),
  Data(x: DateTime(2009, 01, 01), y: 3.8),
  Data(x: DateTime(2010, 01, 01), y: 2.0),
];

@override
Widget build(BuildContext context) {
  return Container(
      child: Center(
        child: SfRangeSelector(
          initialValues: _initialValues,
          child: Container(
            child: SfCartesianChart(
              margin: const EdgeInsets.all(0),
              primaryXAxis: DateTimeAxis(
                isVisible: false,),
              primaryYAxis: NumericAxis(isVisible: false, maximum: 4),
              series: <SplineAreaSeries<Data, DateTime>>[
                SplineAreaSeries<Data, DateTime>(
                    dataSource: _chartData,
                    xValueMapper: (Data sales, _) => sales.x,
                    yValueMapper: (Data sales, _) => sales.y)
              ],
            ),
            height: 250,
          ),
        ),
      ),
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

![Default range selector](images/getting-started/default-range-selector.png)

## Add tick with numeric labels

Add the range selector with ticks, numeric labels, minimum and maximum values to restrict the slider range.

N> The label type like numeric or date time can be determined based on the `min` and `max` properties.

{% tabs %}
{% highlight Dart %}

final double _min = 10;
final double _max = 90;
final SfRangeValues _initialValues = SfRangeValues(40.0, 60.0);

@override
Widget build(BuildContext context) {
  return Container(
      child: Center(
        child: SfRangeSelector(
          min: _min,
          max: _max,
          initialValues: _initialValues,
          interval: 10,
          showLabels: true,
          showTicks: true,
          child: Container(
            child: SfCartesianChart(
              margin: const EdgeInsets.all(0),
              primaryXAxis: DateTimeAxis(
                isVisible: false,),
              primaryYAxis: NumericAxis(isVisible: false, maximum: 4),
              series: <SplineAreaSeries<Data, DateTime>>[
                SplineAreaSeries<Data, DateTime>(
                    dataSource: _chartData,
                    xValueMapper: (Data sales, _) => sales.x,
                    yValueMapper: (Data sales, _) => sales.y)
              ],
            ),
            height: 250,
          ),
        ),
      ),
  );
}

{% endhighlight %}
{% endtabs %}

![Numeric range selector](images/getting-started/numeric-range-selector.png)

## Add tick with date labels

Add range selector with ticks and date labels.

N> You must import the 'package:intl/intl.dart' show DateFormat` package to add the date format in the range selector.

{% tabs %}
{% highlight Dart %}

final DateTime _dateTimeMin = DateTime(2003, 01, 01);
final DateTime _dateTimeMax = DateTime(2010, 01, 01);
final SfRangeValues _dateTimeValues = SfRangeValues(DateTime(2005, 01, 01), DateTime(2008, 01, 01));

@override
Widget build(BuildContext context) {
  return Container(
      child: Center(
        child: SfRangeSelector(
          min: _dateTimeMin,
          max: _dateTimeMax,
          initialValues: _dateTimeValues,
          labelPlacement: LabelPlacement.betweenTicks,
          dateIntervalType: DateIntervalType.months,
          interval: 12,
          dateFormat: DateFormat.y(),
          showLabels: true,
          showTicks: true,
          child: Container(
            child: SfCartesianChart(
              margin: const EdgeInsets.all(0),
              primaryXAxis: DateTimeAxis(
                minimum: dateTimeMin,
                maximum: dateTimeMax,
                isVisible: false,),
              primaryYAxis: NumericAxis(isVisible: false, maximum: 4),
              series: <SplineAreaSeries<Data, DateTime>>[
                SplineAreaSeries<Data, DateTime>(
                    dataSource: chartData,
                    xValueMapper: (Data sales, _) => sales.x,
                    yValueMapper: (Data sales, _) => sales.y)
              ],
            ),
            height: 250,
          ),
        ),
      ),
  );
}

{% endhighlight %}
{% endtabs %}

![Date time range selector](images/getting-started/date-time-range-selector.png)
