---
layout: post
title: Basic features for Syncfusion Flutter Range Slider | Syncfusion
description: This basic features section explains how to add the numeric and date range slider for Flutter platform
platform: Flutter
control: SfRangeSlider
documentation: ug
---

# Basic features of range slider
This section explains about how to add the numeric and date range slider.

## Minimum

The minimum value that the user can select. The default value of `min` property is 0.0. Must be less than the `max` value.

## Maximum

The maximum value that the user can select. The default value of `max` property is 1.0. Must be greater than the `min`.

## Values

The values currently selected in the range slider. The range slider's thumb is drawn corresponding to this value.

For date values, the range slider does not have auto interval support. So, it is mandatory to set `interval`, `dateIntervalType`, and `dateFormat` for date values.

N> The `onChanged` callback can be used to update the visual appearance of the range slider when the user drags the thumb through interaction.

**Numeric range slider**

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(3.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider(
                    min: 0.0,
                    max: 10.0,
                    values: _values,
                    interval: 2,
                    showLabels: true,
                    onChanged: (SfRangeValues newValues) {
                        setState(() {
                            _values = newValues;
                        });
                    },
              )
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Numeric range slider](images/basic-features/numeric-labels.png)

**Date range slider**

You must add the [`intl`](https://pub.dev/packages/intl) package for using date format in the range slider.

{% tabs %}
{% highlight Dart %}

 SfRangeValues _values = SfRangeValues(DateTime(2002, 01, 01), DateTime(2004, 01, 01));

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider(
                    min: DateTime(2000, 01, 01, 00),
                    max: DateTime(2004, 12, 31, 24),
                    values: _values,
                    interval: 1,
                    showLabels: true,
                    dateFormat: DateFormat.y(),
                    dateIntervalType: DateIntervalType.years,
                    onChanged: (SfRangeValues newValues) {
                          setState(() {
                                _values = newValues;
                          });
                    },
              )
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Date range slider](images/basic-features/date-labels.png)

## OnChanged callback

The `onChanged` callback is called when the user selects a value through interaction.

N> The range slider passes the new values to the callback but does not change its state until the parent widget rebuilds the range slider with new values.

N> If it is null, the range slider will be disabled.

**Enabled state**

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(3.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider(
                    min: 0.0,
                    max: 10.0,
                    values: _values,
                    onChanged: (SfRangeValues newValues) {
                       setState(() {
                           _values = newValues;
                        });
                   },
              )
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Enabled range slider](images/basic-features/enabled-state.png)

**Disabled state**

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(3.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider(
                    min: 0.0,
                    max: 10.0,
                    values: _values,
              )
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Disabled range slider](images/basic-features/disabled-state.png)
