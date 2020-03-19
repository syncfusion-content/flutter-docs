---
layout: post
title: Labels features in Syncfusion Flutter Range Slider | Syncfusion
description: This section helps to learn about how to add labels and divisor in the range slider for flutter platform
platform: flutter
control: SfRangeSlider
documentation: ug
---

# Labels and divisors in range slider
This section explains about how to add the labels and divisors in the range slider.

## Show labels

Option to render the labels on given interval. The default value of `showLabels` property is `false`.

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
                    showLabels: true,
                    showTicks: true,
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

![Range slider label support](images/label-and-divisor/show-labels.png)

N>
* Refer the `numberFormat` and `dateFormat` for formatting the numeric and date labels respectively.
* Refer the `SfRangeSliderThemeData` for customizing the appearance of the labels.

## Show divisors

Option to render the divisors on the track. The default value of `showDivisors` property is `false`. It is a shape which is used to represent the major interval points of the track.

For example, if `min` is 0.0 and `max` is 10.0 and `interval` is 2.0, the range slider will render the divisors at 0.0, 2.0, 4.0 and so on.

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
                    showDivisors: true,
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

![Range slider divisor support](images/label-and-divisor/show-divisor.png)

## Number format

Formats the numeric labels. The default value of `numberFormat` property is `null`.

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
                     values: _values,
                     interval: 2,
                     showTicks: true,
                     showLabels: true,
                     numberFormat: NumberFormat("\$"),
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

![Number format support](images/label-and-divisor/number-format.png)

## Date format

Formats the date labels. It is mandatory for date `SfRangeSlider`. For date values, the range slider does not have auto interval support. So, it is mandatory to set `interval`, `dateIntervalType`, and `dateFormat` for date values. The default of `dateFormat` property is `null`.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2002, 01, 01), DateTime(2003, 01, 01));

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

![Date format support](images/label-and-divisor/date-format.png)

## Label placement

Option to place the labels either between the major ticks or on the major ticks. The default value of `labelPlacement` property is `LabelPlacement.onTicks`.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2002, 01, 01), DateTime(2003, 01, 01));

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
                    showTicks: true,
                    labelPlacement: LabelPlacement.betweenTicks,
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

![Label placement support](images/label-and-divisor/label-placement.png)

## Label formatter callback

You can format or change the whole numeric or date label text. Its arguments contains the following parameters:

* actualValue – either `DateTime` or `double` based on given `values`.
* formattedText – If the actual value is `double`, it is formatted by `numberFormat` and if the actual value is `DateTime`, it is formatted by `dateFormat`.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(100.0, 9900.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider(
                    min: 100.0,
                    max: 10000.0,
                    values: _values,
                    showLabels: true,
                    interval: 9900,
                    labelFormatterCallback: (dynamic actualValue, String formattedText) {
                        return actualValue == 10000 ? '\$ $formattedText+' : '\$ $formattedText';
                    },
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

![Label formatter support](images/label-and-divisor/label-formattercallback.png)
