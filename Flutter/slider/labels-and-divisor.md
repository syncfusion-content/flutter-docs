---
layout: post
title: Labels and Divisors in Flutter Slider widget | Syncfusion 
description: Learn here all about the Labels and Divisors feature of Syncfusion Flutter Slider (SfSlider) widget and more.
platform: Flutter
control: SfSlider
documentation: ug
---

# Labels and Divisors in Flutter Treemap (SfTreemap)
This section explains about how to add the labels and divisors in the slider.

## Show labels

The [`showLabels`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/showLabels.html) property is used to render the labels on given interval. The default value of [`showLabels`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/showLabels.html) property is `false`.

### Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
              min: 0.0,
              max: 10.0,
              interval: 2,
              showLabels: true,
              showTicks: true,
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

![Slider label support](images/label-and-divisor/show-labels.png)

### Vertical

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
              min: 0.0,
              max: 10.0,
              interval: 2,
              showLabels: true,
              showTicks: true,
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

![Slider label support](images/label-and-divisor/vertical-show-labels.png)

N>
* Refer the [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/numberFormat.html) and [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dateFormat.html) for formatting the numeric and date labels respectively.
* Refer the [`SfSliderThemeData`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData-class.html) for customizing the appearance of the labels.

## Number format

The [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/numberFormat.html) property is used to format the numeric labels. The default value of [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/numberFormat.html) property is `null`.

N> You must import [`intl`](https://pub.dev/packages/intl) package for formatting numeric slider using the [`NumberFormat`](https://pub.dev/documentation/intl/latest/intl/NumberFormat-class.html) class.

### Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
              min: 0.0,
              max: 10.0,
              value: _value,
              interval: 2,
              showTicks: true,
              showLabels: true,
              numberFormat: NumberFormat("\$"),
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

![Number format support](images/label-and-divisor/number-format.png)

### Vertical

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
              min: 0.0,
              max: 10.0,
              value: _value,
              interval: 2,
              showTicks: true,
              showLabels: true,
              numberFormat: NumberFormat("\$"),
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

![Number format support](images/label-and-divisor/vertical-number-format.png)

## Date format

The [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dateFormat.html) property is used to format the date labels. It is mandatory for date [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html). For date values, the slider does not have auto interval support. So, it is mandatory to set [`interval`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/interval.html), [`dateIntervalType`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dateIntervalType.html), and [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dateFormat.html) for date values. The default value of [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dateFormat.html) property is `null`.

N> You must import [`intl`](https://pub.dev/packages/intl) package for formatting date slider using the [`DateFormat`](https://pub.dev/documentation/intl/latest/intl/DateFormat-class.html) class.

### Year format

#### Horizontal

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2002, 01, 01);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
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

![Year date format support](images/label-and-divisor/year-date-format.png)

#### Vertical

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2002, 01, 01);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
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

![Year date format support](images/label-and-divisor/vertical-year-date-format.png)

### Month format

#### Horizontal

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2000, 03, 01);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
              min: DateTime(2000, 01, 01, 00),
              max: DateTime(2000, 09, 01, 24),
              value: _value,
              interval: 2,
              showLabels: true,
              showTicks: true,
              dateFormat: DateFormat.yM(),
              dateIntervalType: DateIntervalType.months,
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

![Month date format support](images/label-and-divisor/month-date-format.png)

#### Vertical

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2000, 03, 01);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
              min: DateTime(2000, 01, 01, 00),
              max: DateTime(2000, 09, 01, 24),
              value: _value,
              interval: 2,
              showLabels: true,
              showTicks: true,
              dateFormat: DateFormat.yM(),
              dateIntervalType: DateIntervalType.months,
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

![Month date format support](images/label-and-divisor/vertical-month-date-format.png)


### Hour format

#### Horizontal

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2000, 01, 01, 12, 00, 00);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
              min: DateTime(2000, 01, 01, 02, 00, 00),
              max: DateTime(2000, 01, 01, 22, 00, 00),
              value: _value,
              interval: 5,
              showLabels: true,
              showTicks: true,
              dateFormat: DateFormat('h:mm a'),
              dateIntervalType: DateIntervalType.hours,
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

![Hour date format support](images/label-and-divisor/hour-date-format.png)

#### Vertical

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2000, 01, 01, 12, 00, 00);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
              min: DateTime(2000, 01, 01, 02, 00, 00),
              max: DateTime(2000, 01, 01, 22, 00, 00),
              value: _value,
              interval: 5,
              showLabels: true,
              showTicks: true,
              dateFormat: DateFormat('h:mm a'),
              dateIntervalType: DateIntervalType.hours,
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

![Hour date format support](images/label-and-divisor/vertical-hour-date-format.png)

N> Refer the [`DateFormat`](https://api.flutter.dev/flutter/intl/DateFormat-class.html) class for other date format.

## Label placement

The [`labelPlacement`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/labelPlacement.html) property is used to place the labels either between the major ticks or on the major ticks. The default value of the [`labelPlacement`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/labelPlacement.html) property is `LabelPlacement.onTicks`.

### Horizontal

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2002, 01, 01);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
              min: DateTime(2000, 01, 01, 00),
              max: DateTime(2004, 12, 31, 24),
              value: _value,
              interval: 1,
              showLabels: true,
              showTicks: true,
              labelPlacement: LabelPlacement.betweenTicks,
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

![Label placement support](images/label-and-divisor/label-placement.png)

### Vertical

{% tabs %}
{% highlight Dart %}

DateTime _value = DateTime(2002, 01, 01);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
              min: DateTime(2000, 01, 01, 00),
              max: DateTime(2004, 12, 31, 24),
              value: _value,
              interval: 1,
              showLabels: true,
              showTicks: true,
              labelPlacement: LabelPlacement.betweenTicks,
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

![Label placement support](images/label-and-divisor/vertical-label-placement.png)

## Customize label text

You can format or change the whole numeric or date label text using the [`labelFormatterCallback`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/labelFormatterCallback.html). Its arguments are,

* actualValue – either `DateTime` or `double` based on given [`value`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/value.html).
* formattedText – If the actual value is `double`, it is formatted by [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/numberFormat.html) and if the actual value is `DateTime`, it is formatted by [`dateFormat`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dateFormat.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 9900.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
              min: 100.0,
              max: 10000.0,
              value: _value,
              showLabels: true,
              interval: 9900,
              labelFormatterCallback: (dynamic actualValue, String formattedText) {
                return actualValue == 10000 ? '\$ $formattedText+' : '\$ $formattedText';
              },
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

![Label formatter support](images/label-and-divisor/label-formattercallback.png)

### Vertical

{% tabs %}
{% highlight Dart %}

double _value = 9900.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
              min: 100.0,
              max: 10000.0,
              value: _value,
              showLabels: true,
              interval: 9900,
              labelFormatterCallback: (dynamic actualValue, String formattedText) {
                return actualValue == 10000 ? '\$ $formattedText+' : '\$ $formattedText';
              },
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

![Label formatter support](images/label-and-divisor/vertical-label-formattercallback.png)

## Label style

You can change the active and inactive label appearance of the slider using the [`activeLabelStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/activeLabelStyle.html) and [`inactiveLabelStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/inactiveLabelStyle.html) properties respectively.

The active side of the slider is between the [`min`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/min.html) value and the thumb.

The inactive side of the slider is between the thumb and the [`max`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/max.html) value.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderTheme-class.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfSliderTheme(
                data: SfSliderThemeData(
                  activeLabelStyle: TextStyle(color: Colors.red, fontSize: 12, fontStyle: FontStyle.italic),
                  inactiveLabelStyle: TextStyle(color: Colors.red[200], fontSize: 12, fontStyle: FontStyle.italic),
                ),
                child:  SfSlider(
                  min: 2.0,
                  max: 10.0,
                  value: _value,
                  interval: 1,
                  showLabels: true,
                  showTicks: true,
                  onChanged: (dynamic newValue){
                    setState(() {
                      _value = newValue;
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

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfSliderTheme(
                data: SfSliderThemeData(
                  activeLabelStyle: TextStyle(color: Colors.red, fontSize: 12, fontStyle: FontStyle.italic),
                  inactiveLabelStyle: TextStyle(color: Colors.red[200], fontSize: 12, fontStyle: FontStyle.italic),
                ),
                child:  SfSlider.vertical(
                  min: 2.0,
                  max: 10.0,
                  value: _value,
                  interval: 1,
                  showLabels: true,
                  showTicks: true,
                  onChanged: (dynamic newValue){
                    setState(() {
                      _value = newValue;
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

You can adjust the space between ticks and labels of the slider using the [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/labelOffset.html) property.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderTheme-class.html).

### Horizontal

The default value of [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/labelOffset.html) property is `Offset(0.0, 13.0)` if the [`showTicks`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/showTicks.html) property is `false`.
The default value of [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/labelOffset.html) property is `Offset(0.0, 5.0)` if the [`showTicks`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/showTicks.html) property is `true`.

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfSliderTheme(
                data: SfSliderThemeData(
                  labelOffset: Offset(0.0, 10.0),
                ),
                child:  SfSlider(
                  min: 2.0,
                  max: 10.0,
                  value: _value,
                  interval: 2,
                  showTicks: true,
                  showLabels: true,
                  onChanged: (dynamic newValue){
                    setState(() {
                      _value = newValue;
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

The default value of [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/labelOffset.html) property is `Offset(13.0, 0.0)` if the [`showTicks`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/showTicks.html) property is `false`.
The default value of [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/labelOffset.html) property is `Offset(5.0, 0.0)` if the [`showTicks`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/showTicks.html) property is `true`.

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfSliderTheme(
                data: SfSliderThemeData(
                  labelOffset: Offset(10.0, 0.0),
                ),
                child:  SfSlider.vertical(
                  min: 2.0,
                  max: 10.0,
                  value: _value,
                  interval: 2,
                  showTicks: true,
                  showLabels: true,
                  onChanged: (dynamic newValue){
                    setState(() {
                      _value = newValue;
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

The [`showDivisors`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/showDivisors.html) property is used to render the divisors on the track. The default value of the [`showDivisors`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/showDivisors.html) property is `false`. It is a shape which is used to represent the major interval points of the track.

For example, if [`min`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/min.html) is 0.0 and [`max`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/max.html) is 10.0 and [`interval`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/interval.html) is 2.0, the slider will render the divisors at 0.0, 2.0, 4.0 and so on.

### Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSliderTheme(
              data: SfSliderThemeData(
                activeTrackHeight: 5,
                inactiveTrackHeight: 5,
              ),
              child: SfSlider(
                min: 0.0,
                max: 10.0,
                interval: 2,
                showDivisors: true,
                value: _value,
                onChanged: (dynamic newValue) {
                  setState(() {
                    _value = newValue;
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

![Slider divisor support](images/label-and-divisor/show-divisor.png)

### Vertical

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSliderTheme(
              data: SfSliderThemeData(
                activeTrackHeight: 5,
                inactiveTrackHeight: 5,
              ),
              child: SfSlider.vertical(
                min: 0.0,
                max: 10.0,
                interval: 2,
                showDivisors: true,
                value: _value,
                onChanged: (dynamic newValue) {
                  setState(() {
                    _value = newValue;
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

![Slider divisor support](images/label-and-divisor/vertical-show-divisor.png)

## Divisor radius

You can change the active and inactive divisor radius of the slider using the [`activeDivisorRadius`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/activeDivisorRadius.html) and the [`inactiveDivisorRadius`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/inactiveDivisorRadius.html) properties respectively.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderTheme-class.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfSliderTheme(
                  data: SfSliderThemeData(
                    activeTrackHeight: 10,
                    inactiveTrackHeight: 10,
                    activeDivisorRadius: 5,
                    inactiveDivisorRadius: 5,
                  ),
                  child: SfSlider(
                    min: 2.0,
                    max: 10.0,
                    interval: 1,
                    showDivisors: true,
                    value: _value,
                    onChanged: (dynamic newValue){
                      setState(() {
                        _value = newValue;
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

![Divisor radius support](images/label-and-divisor/slider-divisor-radius.png)

### Vertical

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfSliderTheme(
                  data: SfSliderThemeData(
                    activeTrackHeight: 10,
                    inactiveTrackHeight: 10,
                    activeDivisorRadius: 5,
                    inactiveDivisorRadius: 5,
                  ),
                  child: SfSlider.vertical(
                    min: 2.0,
                    max: 10.0,
                    interval: 1,
                    showDivisors: true,
                    value: _value,
                    onChanged: (dynamic newValue){
                      setState(() {
                        _value = newValue;
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

![Divisor radius support](images/label-and-divisor/vertical-slider-divisor-radius.png)


## Divisor stroke width and stroke color

You can change the active and inactive divisor stroke width of the slider using the [`activeDivisorStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/activeDivisorStrokeWidth.html) and the [`inactiveDivisorStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/inactiveDivisorStrokeWidth.html) properties respectively.

Also, you can change the active and inactive divisor stroke color of the slider using the [`activeDivisorStrokeColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/activeDivisorStrokeColor.html) and the [`inactiveDivisorStrokeColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/inactiveDivisorStrokeColor.html) properties respectively.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderTheme-class.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfSliderTheme(
                  data: SfSliderThemeData(
                    activeTrackHeight: 10,
                    inactiveTrackHeight: 10,
                    activeDivisorStrokeColor: Colors.red,
                    activeDivisorStrokeWidth: 2,
                    inactiveDivisorStrokeWidth: 2,
                    inactiveDivisorStrokeColor: Colors.red,
                  ),
                  child: SfSlider(
                    min: 2.0,
                    max: 10.0,
                    interval: 1,
                    showDivisors: true,
                    value: _value,
                    onChanged: (dynamic newValue){
                      setState(() {
                        _value = newValue;
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

![Divisor stroke width and color support](images/label-and-divisor/slider-divisor-stroke-color.png)

### Vertical

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfSliderTheme(
                  data: SfSliderThemeData(
                    activeTrackHeight: 10,
                    inactiveTrackHeight: 10,
                    activeDivisorStrokeColor: Colors.red,
                    activeDivisorStrokeWidth: 2,
                    inactiveDivisorStrokeWidth: 2,
                    inactiveDivisorStrokeColor: Colors.red,
                  ),
                  child: SfSlider.vertical(
                    min: 2.0,
                    max: 10.0,
                    interval: 1,
                    showDivisors: true,
                    value: _value,
                    onChanged: (dynamic newValue){
                      setState(() {
                        _value = newValue;
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

![Divisor stroke width and color support](images/label-and-divisor/vertical-slider-divisor-stroke-color.png)


## Divisor color

You can change the active and inactive divisor color of the slider using the [`activeDivisorColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/activeDivisorColor.html) and [`inactiveDivisorColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/inactiveDivisorColor.html) properties respectively.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderTheme-class.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfSliderTheme(
                  data: SfSliderThemeData(
                    activeTrackHeight: 5,
                    inactiveTrackHeight: 5,
                    activeDivisorColor: Colors.red,
                    inactiveDivisorColor: Colors.red[200],
                  ),
                  child: SfSlider(
                    min: 2.0,
                    max: 10.0,
                    interval: 1,
                    showDivisors: true,
                    value: _value,
                    onChanged: (dynamic newValue){
                      setState(() {
                        _value = newValue;
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

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfSliderTheme(
                  data: SfSliderThemeData(
                    activeTrackHeight: 5,
                    inactiveTrackHeight: 5,
                    activeDivisorColor: Colors.red,
                    inactiveDivisorColor: Colors.red[200],
                  ),
                  child: SfSlider.vertical(
                    min: 2.0,
                    max: 10.0,
                    interval: 1,
                    showDivisors: true,
                    value: _value,
                    onChanged: (dynamic newValue){
                      setState(() {
                        _value = newValue;
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

