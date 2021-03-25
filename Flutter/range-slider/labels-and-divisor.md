---
layout: post
title: Labels features in Syncfusion Flutter Range Slider | Syncfusion
description: This section explains about how to show labels, divisors and how to customize them in the range slider.
platform: Flutter
control: SfRangeSlider
documentation: ug
---

# Labels and divisors in range slider
This section explains about how to add the labels and divisors in the range slider.

## Show labels

The [`showLabels`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/showLabels.html) property is used to render the labels on given interval. The default value of [`showLabels`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/showLabels.html) property is `false`.

### Horizontal

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

### Vertical
{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 6.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider.vertical(
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

![Range slider label support](images/label-and-divisor/vertical-show-labels.png)

N>
* Refer the [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/numberFormat.html) and [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/dateFormat.html) for formatting the numeric and date labels respectively.
* Refer the [`SfRangeSliderThemeData`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData-class.html) for customizing the appearance of the labels.

## Number format

The [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/numberFormat.html) property is used to format the numeric labels. The default value of [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/numberFormat.html) property is `null`.

N> You must import [`intl`](https://pub.dev/packages/intl) package for formatting numeric range slider using the [`NumberFormat`](https://pub.dev/documentation/intl/latest/intl/NumberFormat-class.html) class.

### Horizontal

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

### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 6.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider.vertical(
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

![Number format support](images/label-and-divisor/vertical-number-format.png)

## Date format

The [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/dateFormat.html) property is used to format the date labels. It is mandatory for date [`SfRangeSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider-class.html). For date values, the range slider does not have auto interval support. So, it is mandatory to set [`interval`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/interval.html), [`dateIntervalType`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/dateIntervalType.html), and [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/dateFormat.html) for date values. The default value of [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/dateFormat.html) property is `null`.

N> You must import [`intl`](https://pub.dev/packages/intl) package for formatting date range slider using the [`DateFormat`](https://pub.dev/documentation/intl/latest/intl/DateFormat-class.html) class.

### Year format

#### Horizontal

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2002, 01, 01), DateTime(2003, 01, 01));

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider.vertical(
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

![Year date format support](images/label-and-divisor/year-date-format.png)

#### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2002, 01, 01), DateTime(2003, 01, 01));

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider.vertical(
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

![Year date format support](images/label-and-divisor/vertical-year-date-format.png)

### Month format

#### Horizontal

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2000, 03, 01), DateTime(2000, 07, 01));

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider(
                    min: DateTime(2000, 01, 01, 00),
                    max: DateTime(2000, 09, 01, 24),
                    values: _values,
                    interval: 2,
                    showLabels: true,
                    showTicks: true,
                    dateFormat: DateFormat.yM(),
                    dateIntervalType: DateIntervalType.months,
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

![Month date format support](images/label-and-divisor/month-date-format.png)

#### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2000, 03, 01), DateTime(2000, 07, 01));

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider.vertical(
                    min: DateTime(2000, 01, 01, 00),
                    max: DateTime(2000, 09, 01, 24),
                    values: _values,
                    interval: 2,
                    showLabels: true,
                    showTicks: true,
                    dateFormat: DateFormat.yM(),
                    dateIntervalType: DateIntervalType.months,
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

![Month date format support](images/label-and-divisor/vertical-month-date-format.png)

### Hour format

#### Horizontal

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2000, 01, 01, 07, 00, 00), DateTime(2000, 01, 01, 17, 00, 00));

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider(
                  min: DateTime(2000, 01, 01, 02, 00, 00),
                  max: DateTime(2000, 01, 01, 22, 00, 00),
                  values: _values,
                  interval: 5,
                  showLabels: true,
                  showTicks: true,
                  dateFormat: DateFormat('h:mm a'),
                  dateIntervalType: DateIntervalType.hours,
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

![Hour date format support](images/label-and-divisor/hour-date-format.png)

#### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2000, 01, 01, 07, 00, 00), DateTime(2000, 01, 01, 17, 00, 00));

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider.vertical(
                  min: DateTime(2000, 01, 01, 02, 00, 00),
                  max: DateTime(2000, 01, 01, 22, 00, 00),
                  values: _values,
                  interval: 5,
                  showLabels: true,
                  showTicks: true,
                  dateFormat: DateFormat('h:mm a'),
                  dateIntervalType: DateIntervalType.hours,
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

![Hour date format support](images/label-and-divisor/vertical-hour-date-format.png)

N> Refer the [`DateFormat`](https://api.flutter.dev/flutter/intl/DateFormat-class.html) class for other date format.

## Label placement

The [`labelPlacement`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/labelPlacement.html) property is used to place the labels either between the major ticks or on the major ticks. The default value of [`labelPlacement`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/labelPlacement.html) property is `LabelPlacement.onTicks`.

### Horizontal

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

### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2002, 01, 01), DateTime(2003, 01, 01));

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider.vertical(
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

![Label placement support](images/label-and-divisor/vertical-label-placement.png)

## Customize label text

You can format or change the whole numeric or date label text using the [`labelFormatterCallback`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/labelFormatterCallback.html). Its arguments are,

* actualValue – either `DateTime` or `double` based on given [`values`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/values.html).
* formattedText – If the actual value is `double`, it is formatted by [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/numberFormat.html) and if the actual value is `DateTime`, it is formatted by [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/dateFormat.html).

### Horizontal

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

### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(100.0, 9900.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider.vertical(
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

![Label formatter support](images/label-and-divisor/vertical-label-formattercallback.png)

## Label style

You can change the active and inactive label appearance of the range slider using the [`activeLabelStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/activeLabelStyle.html) and [`inactiveLabelStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/inactiveLabelStyle.html) properties respectively.

The active side of the range slider is between start and end thumbs.

The inactive side of the range slider is between the [`min`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/min.html) value and the left thumb, and the right thumb and the [`max`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/max.html) value.

For RTL, the inactive side is between the [`max`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/max.html) value and the left thumb, and the right thumb and the [`min`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/min.html) value.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderTheme-class.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                         activeLabelStyle: TextStyle(color: Colors.red, fontSize: 12, fontStyle: FontStyle.italic),
                         inactiveLabelStyle: TextStyle(color: Colors.red[200], fontSize: 12, fontStyle: FontStyle.italic),
                    ),
                    child:  SfRangeSlider(
                       min: 2.0,
                       max: 10.0,
                       values: _values,
                       interval: 1,
                       showLabels: true,
                       showTicks: true,
                       onChanged: (SfRangeValues newValues){
                            setState(() {
                                _values = newValues;
                            });
                        },
                    ),
              )
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Labels style support](images/label-and-divisor/slider-labels-color.png)

### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                         activeLabelStyle: TextStyle(color: Colors.red, fontSize: 12, fontStyle: FontStyle.italic),
                         inactiveLabelStyle: TextStyle(color: Colors.red[200], fontSize: 12, fontStyle: FontStyle.italic),
                    ),
                    child:  SfRangeSlider.vertical(
                       min: 2.0,
                       max: 10.0,
                       values: _values,
                       interval: 1,
                       showLabels: true,
                       showTicks: true,
                       onChanged: (SfRangeValues newValues){
                            setState(() {
                                _values = newValues;
                            });
                        },
                    ),
              )
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Labels style support](images/label-and-divisor/vertical-slider-labels-color.png)

## Label offset

You can adjust the space between ticks and labels of the range slider using the [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/labelOffset.html) property.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderTheme-class.html).

### Horizontal

The default value of [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/labelOffset.html) property is `Offset(0.0, 13.0)` if the [`showTicks`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/showTicks.html) property is `false`.
The default value of [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/labelOffset.html) property is `Offset(0.0, 5.0)` if the [`showTicks`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/showTicks.html) property is `true`.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        labelOffset: Offset(0.0, 10.0),
                    ),
                    child:  SfRangeSlider(
                       min: 2.0,
                       max: 10.0,
                       values: _values,
                       interval: 2,
                       showTicks: true,
                       showLabels: true,
                       onChanged: (SfRangeValues newValues){
                            setState(() {
                                _values = newValues;
                            });
                        },
                    ),
              )
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Labels offset support](images/label-and-divisor/slider-labels-offset.png)

### Vertical

The default value of [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/labelOffset.html) property is `Offset(13.0, 0.0)` if the [`showTicks`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/showTicks.html) property is `false`.
The default value of [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/labelOffset.html) property is `Offset(5.0, 0.0)` if the [`showTicks`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/showTicks.html) property is `true`.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        labelOffset: Offset(10.0, 0.0),
                    ),
                    child:  SfRangeSlider.vertical(
                       min: 2.0,
                       max: 10.0,
                       values: _values,
                       interval: 2,
                       showTicks: true,
                       showLabels: true,
                       onChanged: (SfRangeValues newValues){
                            setState(() {
                                _values = newValues;
                            });
                        },
                    ),
              )
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Labels offset support](images/label-and-divisor/vertical-slider-labels-offset.png)

## Show divisors

The [`showDivisors`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/showDivisors.html) property is used to render the divisors on the track. The default value of [`showDivisors`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/showDivisors.html) property is `false`. It is a shape which is used to represent the major interval points of the track.

For example, if [`min`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/min.html) is 0.0 and [`max`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/max.html) is 10.0 and [`interval`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/interval.html) is 2.0, the range slider will render the divisors at 0.0, 2.0, 4.0 and so on.

### Horizontal

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 6.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                 data: SfRangeSliderThemeData(
                    activeTrackHeight: 5,
                    inactiveTrackHeight: 5,
                 ),
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
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Range slider divisor support](images/label-and-divisor/show-divisor.png)

### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 6.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                 data: SfRangeSliderThemeData(
                    activeTrackHeight: 5,
                    inactiveTrackHeight: 5,
                 ),
                 child: SfRangeSlider.vertical(
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
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Range slider divisor support](images/label-and-divisor/vertical-show-divisor.png)

## Divisor radius

You can change the active and inactive divisor radius of the range slider using the [`activeDivisorRadius`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/activeDivisorRadius.html) and the [`inactiveDivisorRadius`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/inactiveDivisorRadius.html) properties respectively.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderTheme-class.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(3.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                 data: SfRangeSliderThemeData(
                    activeTrackHeight: 10,
                    inactiveTrackHeight: 10,
                    activeDivisorRadius: 5,
                    inactiveDivisorRadius: 5
                 ),
                 child: SfRangeSlider(
                    min: 0.0,
                    max: 10.0,
                    interval: 1,
                    showDivisors: true,
                    values: _values,
                    onChanged: (SfRangeValues newValues) {
                        setState(() {
                           _values = newValues;
                        });
                    },
                 ),
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Divisor radius support](images/label-and-divisor/range-slider-divisor-radius.png)

### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(3.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                 data: SfRangeSliderThemeData(
                    activeTrackHeight: 10,
                    inactiveTrackHeight: 10,
                    activeDivisorRadius: 5,
                    inactiveDivisorRadius: 5
                 ),
                 child: SfRangeSlider.vertical(
                    min: 0.0,
                    max: 10.0,
                    interval: 1,
                    showDivisors: true,
                    values: _values,
                    onChanged: (SfRangeValues newValues) {
                        setState(() {
                           _values = newValues;
                        });
                    },
                 ),
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Divisor radius support](images/label-and-divisor/vertical-range-slider-divisor-radius.png)

## Divisor stroke width and stroke color

You can change the active and inactive divisor stroke width of the range slider using the [`activeDivisorStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/activeDivisorStrokeWidth.html) and the [`inactiveDivisorStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/inactiveDivisorStrokeWidth.html) properties respectively.

Also, you can change the active and inactive divisor stroke color of the range slider using the [`activeDivisorStrokeColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/activeDivisorStrokeColor.html) and the [`inactiveDivisorStrokeColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/inactiveDivisorStrokeColor.html) properties respectively.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderTheme-class.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(3.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                 data: SfRangeSliderThemeData(
                     activeTrackHeight: 10,
                     inactiveTrackHeight: 10,
                     activeDivisorRadius:4 ,
                     inactiveDivisorRadius: 4,
                     activeDivisorStrokeColor: Colors.red,
                     activeDivisorStrokeWidth: 2,
                     inactiveDivisorStrokeWidth: 2,
                     inactiveDivisorStrokeColor: Colors.red,
                 ),
                 child: SfRangeSlider(
                    min: 0.0,
                    max: 10.0,
                    interval: 1,
                    showDivisors: true,
                    values: _values,
                    onChanged: (SfRangeValues newValues) {
                        setState(() {
                           _values = newValues;
                        });
                    },
                 ),
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Divisor stroke width and color support](images/label-and-divisor/range-slider-divisor-stroke-color.png)

### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(3.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                 data: SfRangeSliderThemeData(
                     activeTrackHeight: 10,
                     inactiveTrackHeight: 10,
                     activeDivisorRadius:4 ,
                     inactiveDivisorRadius: 4,
                     activeDivisorStrokeColor: Colors.red,
                     activeDivisorStrokeWidth: 2,
                     inactiveDivisorStrokeWidth: 2,
                     inactiveDivisorStrokeColor: Colors.red,
                 ),
                 child: SfRangeSlider.vertical(
                    min: 0.0,
                    max: 10.0,
                    interval: 1,
                    showDivisors: true,
                    values: _values,
                    onChanged: (SfRangeValues newValues) {
                        setState(() {
                           _values = newValues;
                        });
                    },
                 ),
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Divisor stroke width and color support](images/label-and-divisor/vertical-range-slider-divisor-stroke-color.png)

## Divisor color

You can change the active and inactive divisor color of the range slider using the [`activeDivisorColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/activeDivisorColor.html) and [`inactiveDivisorColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/inactiveDivisorColor.html) properties respectively.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderTheme-class.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(2.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                         activeTrackHeight: 5,
                         inactiveTrackHeight: 5,
                         activeDivisorColor: Colors.red,
                         inactiveDivisorColor: Colors.red[200],
                    ),
                    child:  SfRangeSlider(
                      min: 0.0,
                      max: 10.0,
                      interval: 1,
                      showDivisors: true,
                      values: _values,
                      onChanged: (SfRangeValues newValues){
                            setState(() {
                                _values = newValues;
                            });
                        },
                    )
              )
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Divisor color support](images/label-and-divisor/slider-divisor-color.png)

### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(2.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                         activeTrackHeight: 5,
                         inactiveTrackHeight: 5,
                         activeDivisorColor: Colors.red,
                         inactiveDivisorColor: Colors.red[200],
                    ),
                    child:  SfRangeSlider.vertical(
                      min: 0.0,
                      max: 10.0,
                      interval: 1,
                      showDivisors: true,
                      values: _values,
                      onChanged: (SfRangeValues newValues){
                            setState(() {
                                _values = newValues;
                            });
                        },
                    )
              )
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Divisor color support](images/label-and-divisor/vertical-slider-divisor-color.png)