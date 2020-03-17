---
layout: post
title: Basic features for Syncfusion Flutter Range Slider | Syncfusion
description: This basic features section explains how to add the numeric and date range slider for flutter platform
platform: flutter
control: SfRangeSlider
documentation: ug
---

# Basic features of Range Slider
This section explains about how to add the numeric and date range slider.

## Minimum

The minimum value that the user can select. The default value of `min` property is 0.0.

## Maximum

The maximum value that the user can select. The default value of `max` property is 1.0.

## onChanged

The `onChanged` callback is called when the user selects a value through interaction. The range slider passes the new values to the callback but does not change its state until the parent widget rebuilds the range slider with new values.

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

## Values

The values currently selected in the range slider. The range slider's thumb is drawn corresponding to this value. For date values, the range slider doesn’t have auto interval support. So, it is necessary to set `interval`, `dateIntervalType`, and `dateFormat` for date values.

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

## Interval

Represents the certain interval between two labels. It is necessary for date `SfRangeSlider`. Based on this value, labels, major ticks and divisions are drawn. For example, if `min` is 0.0 and `max` is 4.0 and `interval` is 2.0, then the range slider will render the major ticks at 0.0, 2.0, and 4.0.

I> The default value is null. Must be greater than 0.

N>
* `showDivisions` can be used to render divisors at given interval.
* `showTicks` can be used to render major ticks at given interval.
* `showLabels` can be used to render labels at given interval.

## Active color

Represents the color applied to the active track, thumb, overlay, and inactive divisors. The `active` side of the range slider is between the left and right thumbs.

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
                    activeColor: Colors.red,
                    showDivisors: true,
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

![Active color support](images/basic-features/active-color.png)

## Inactive color

Represents the color applied to the inactive track and active divisors. The "inactive" side of the range slider is between the `min` value and the left thumb, and the right thumb and the `max` value.

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
                    activeColor: Colors.red,
                    inactiveColor: Colors.red.withOpacity(0.2),
                    showDivisors: true,
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

![Inactive color support](images/basic-features/inactive-color.png)