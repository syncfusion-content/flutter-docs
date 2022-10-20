---
layout: post
title: Interval in Flutter Slider widget | Syncfusion 
description: Learn here all about adding the Interval feature of Syncfusion Flutter Slider (SfSlider) widget and more.
platform: Flutter
control: SfSlider
documentation: ug
---

# Interval in Flutter Slider (SfSlider)
This section explains about how to add the interval for numeric and date slider.

## Numeric interval

Slider elements like labels, ticks and dividers are rendered based on the [`interval`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/interval.html), [`min`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/min.html) and [`max`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/max.html) properties. The default value is `null` and it must be greater than 0.

For example, if [`min`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/min.html) is 0.0 and [`max`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/max.html) is 10.0 and [`interval`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/interval.html) is 2.0, the slider will render the labels, major ticks, and dividers at 0.0, 2.0, 4.0 and so on.

### Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 4.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
              min: 0.0,
              max: 10.0,
              interval: 2,
              showTicks: true,
              showLabels: true,
              value: _value,
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
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

### Vertical

{% tabs %}
{% highlight Dart %}

double _value = 4.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
              min: 0.0,
              max: 10.0,
              interval: 2,
              showTicks: true,
              showLabels: true,
              value: _value,
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
                });
              },
            ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Numeric interval support](images/interval/vertical-numeric-interval.png)

N>
* Refer the [`showDividers`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/showDividers.html) to know about the rendering of dividers at given interval.
* Refer the [`showTicks`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/showTicks.html) to know about the rendering of major ticks at given interval.
* Refer the [`showLabels`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/showLabels.html) to know about the rendering of labels at given interval.

## Date interval

The type of date interval. It can be years to seconds. It is mandatory for date [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html). The default value of [`dateIntervalType`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dateIntervalType.html) property is `null`.

For date values, the slider does not have auto interval support. So, it is mandatory to set [`interval`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/interval.html), [`dateIntervalType`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dateIntervalType.html), and [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dateFormat.html) for date values.

For example, if [`min`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/min.html) is `DateTime(2000, 01, 01)` and [`max`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/max.html) is `DateTime(2005, 01, 01)` and [`interval`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/interval.html) is `1`, [`dateIntervalType`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dateIntervalType.html) is `DateIntervalType.years`, [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dateFormat.html) is `DateFormat.y()` then the slider will render the labels, major ticks, and dividers at 2000, 2001, 2002 and so on.

### Horizontal

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2002, 01, 01);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child:  SfSlider(
              min: DateTime(2000, 01, 01, 00),
              max: DateTime(2004, 12, 31, 24),
              value: _value,
              interval: 1,
              showLabels: true,
              showTicks: true,
              dateFormat: DateFormat.y(),
              dateIntervalType: DateIntervalType.years,
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
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

### Vertical

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2002, 01, 01);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child:  SfSlider.vertical(
              min: DateTime(2000, 01, 01, 00),
              max: DateTime(2004, 12, 31, 24),
              value: _value,
              interval: 1,
              showLabels: true,
              showTicks: true,
              dateFormat: DateFormat.y(),
              dateIntervalType: DateIntervalType.years,
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
                });
              },
            ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Date interval type support](images/interval/vertical-date-interval-type.png)

## Discrete selection for numeric values

You can move the thumb in discrete manner for numeric values using the [`stepSize`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/stepSize.html) property in the slider.

### Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 4.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
              min: 0.0,
              max: 10.0,
              interval: 2,
              stepSize: 2,
              showTicks: true,
              minorTicksPerInterval: 1,
              showLabels: true,
              value: _value,
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
                });
              },
            ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Step size support](images/interval/step-size-support.gif)

### Vertical

{% tabs %}
{% highlight Dart %}

double _value = 4.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
              min: 0.0,
              max: 10.0,
              interval: 2,
              stepSize: 2,
              showTicks: true,
              minorTicksPerInterval: 1,
              showLabels: true,
              value: _value,
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
                });
              },
            ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

## Discrete selection for date values

You can move the thumb in discrete manner for date values using the [`stepDuration`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/stepDuration.html) property in the slider.

For example, if [min](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/min.html) is DateTime(2015, 01, 01) and [max](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/max.html) is DateTime(2020, 01, 01) and [stepDuration](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/stepDuration.html) is SliderDuration(years: 1, months: 6),the slider will move the thumbs at DateTime(2015, 01, 01), DateTime(2016, 07, 01), DateTime(2018, 01, 01),and DateTime(2019, 07, 01).

### Horizontal

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2004, 01, 01);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
              min: DateTime(2000, 01, 01),
              max: DateTime(2010, 01, 01),
              interval: 2,
              stepDuration: SliderStepDuration(years: 2),
              dateFormat: DateFormat.y(),
              dateIntervalType: DateIntervalType.years,
              showTicks: true,
              showLabels: true,
              value: _value,
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
                });
              },
            ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Step duration support](images/interval/step-duration-support.gif)

### Vertical

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2004, 01, 01);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
              min: DateTime(2000, 01, 01),
              max: DateTime(2010, 01, 01),
              interval: 2,
              stepDuration: SliderStepDuration(years: 2),
              dateFormat: DateFormat.y(),
              dateIntervalType: DateIntervalType.years,
              showTicks: true,
              showLabels: true,
              value: _value,
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
                });
              },
            ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

