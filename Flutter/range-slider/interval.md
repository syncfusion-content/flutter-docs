---
layout: post
title: Interval in Syncfusion Flutter Range Slider | Syncfusion
description: This section explains about how to add the interval for numeric and date range slider for flutter platform
platform: flutter
control: SfRangeSlider
documentation: ug
---

# Range slider interval
This section explains about how to add the interval for numeric and date range slider.

## Numeric interval

Splits the range slider into given interval. It is mandatory if labels, major ticks and divisions are needed. The default value is null. Must be greater than 0.

For example, if `min` is 0.0 and `max` is 10.0 and `interval` is 2.0, the range slider will render the labels,  major ticks, and divisors at 0.0, 2.0, 4.0 and so on.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 6.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider(
                    min: 0.0,
                    max: 10.0,
                    interval: 2,
                    showTicks: true,
                    showLabels: true,
                    values: _values,
                    onChanged: (SfRangeValues newValues) {
                        setState(() {
                            _values = newValues;
                        });
                   },
               ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Numeric interval support](images/interval/numeric-interval.png)

N>
* Refer the `showDivisions` to know about the rendering of divisors at given interval.
* Refer the `showTicks` to know about the rendering of major ticks at given interval.
* Refer the `showLabels` to know about the rendering of labels at given interval.

## Date interval

The type of date interval. It can be years to seconds. It is mandatory for date `SfRangeSlider`. The default value of `dateIntervalType` property is `null`.

For date values, the range slider does not have auto interval support. So, it is mandatory to set `interval`, `dateIntervalType`, and `dateFormat` for date values.

For example, if `min` is `DateTime(2000, 01, 01)` and `max` is `DateTime(2005, 01, 01)` and `interval` is `1`, `dateIntervalType` is `DateIntervalType.years`, `dateFormat` is `DateFormat.y()` then the range selector will render the labels,  major ticks, and divisors at 2000, 2001, 2002 and so on.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2002, 01, 01), DateTime(2003, 01, 01));

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child:  SfRangeSlider(
                    min: DateTime(2000, 01, 01, 00),
                    max: DateTime(2004, 12, 31, 24),
                    values: _values,
                    interval: 1,
                    showLabels: true,
                    showTicks: true,
                    dateFormat: DateFormat.y(),
                    dateIntervalType: DateIntervalType.years,
                    onChanged: (SfRangeValues newValues) {
                        setState(() {
                            _values = newValues;
                        });
                   },
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Date interval type support](images/interval/date-interval-type.png)
