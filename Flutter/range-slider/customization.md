---
layout: post
title: Customize the Syncfusion Flutter Range Slider | Syncfusion
description: This customization section explains about how to customize the range slider features for flutter platform
platform: flutter
control: SfRangeSlider
documentation: ug
---

# Customization of range slider
This section explains about how to customize the range slider elements.

## Track customization

### Track color

You can change the active and inactive track color of the range slider using the `activeTrackColor` and `inactiveTrackColor` properties respectively.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _values = SfRangeValues(4.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        activeTrackColor: Colors.red,
                        inactiveTrackColor: Colors.red[100],
                    ),
                    child:  SfRangeSlider(
                        min: _min,
                        max: _max,
                        values: _values,
                        onChanged: (dynamic newValue){
                            setState(() {
                                _values = newValue;
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

![Track color support](images/customization/slider-track-color.png)

### Track size

You can change the track height of the range slider using the `trackHeight` property.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _values = SfRangeValues(4.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        trackHeight: 8,
                    ),
                    child:  SfRangeSlider(
                        min: _min,
                        max: _max,
                        values: _values,
                        onChanged: (dynamic newValue){
                            setState(() {
                                _values = newValue;
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

![Track size support](images/customization/slider-track-size.png)

### Track corner radius

You can change the corner of the track to be round in the range slider using the `trackCornerRadius` property.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _values = SfRangeValues(4.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        trackHeight: 10,
                        trackCornerRadius: 5,
                    ),
                    child:  SfRangeSlider(
                        min: _min,
                        max: _max,
                        values: _values,
                        onChanged: (dynamic newValue){
                            setState(() {
                                _values = newValue;
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

![Track corner radius support](images/customization/slider-track-corner-radius.png)

## Ticks customization

### Ticks color

**Major ticks color**

You can change the active and inactive major ticks color of the range slider using the `activeTickColor` and `inactiveTickColor` properties respectively.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _values = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        activeTickColor: Colors.red,
                        inactiveTickColor: Colors.red[100],
                    ),
                    child:  SfRangeSlider(
                        min: _min,
                        max: _max,
                        values: _values,
                        interval: 1,
                        showTicks: true,
                        onChanged: (dynamic newValue){
                            setState(() {
                                _values = newValue;
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

![Major ticks color](images/customization/slider-major-ticks.png)

**Minor ticks color**

You can change the active and inactive minor ticks color of the range slider using the `activeMinorTickColor` and `inactiveMinorTickColor` properties respectively.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _values = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        activeMinorTickColor: Colors.red,
                        inactiveMinorTickColor: Colors.red[200],
                    ),
                    child:  SfRangeSlider(
                        min: _min,
                        max: _max,
                        values: _values,
                        interval: 2,
                        minorTicksPerInterval: 1,
                        showTicks: true,
                        onChanged: (dynamic newValue){
                            setState(() {
                                _values = newValue;
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

![Minor ticks color](images/customization/slider-minor-ticks.png)

### Ticks size

You can change the major and minor ticks size of the range slider using the `tickSize` and `minorTickSize` properties respectively.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _values = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                         tickSize: Size(3.0, 12.0),
                         minorTickSize: Size(3.0, 8.0),
                    ),
                    child:  SfRangeSlider(
                         min: _min,
                         max: _max,
                         interval: 2,
                         minorTicksPerInterval: 1,
                         showTicks: true,
                         values: _values,
                        onChanged: (dynamic newValue){
                            setState(() {
                                _values = newValue;
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

![Ticks size support](images/customization/slider-ticks-size.png)

### Ticks offset

You can provide the empty space between the track and ticks of the range slider using the `tickOffset` property in the `SfRangeSliderThemeData`.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _values = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        tickOffset: Offset(0.0, 10.0),
                    ),
                    child:  SfRangeSlider(
                         min: _min,
                         max: _max,
                         interval: 2,
                         minorTicksPerInterval: 1,
                         showTicks: true,
                         values: _values,
                        onChanged: (dynamic newValue){
                            setState(() {
                                _values = newValue;
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

![Ticks offset support](images/customization/slider-ticks-offset.png)

## Labels customization

### Labels color

You can change the active and inactive label style of the range slider using the `activeLabelStyle` and `inactiveLabelStyle` properties respectively.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
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
                       min: _min,
                       max: _max,
                       values: _values,
                       interval: 1,
                       showLabels: true,
                       showTicks: true,
                       onChanged: (dynamic newValue){
                            setState(() {
                                _values = newValue;
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

![Labels color support](images/customization/slider-labels-color.png)

### Labels offset

You can provide the empty space between the ticks and labels of the range slider using the `labelOffset` property.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
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
                       min: _min,
                       max: _max,
                       interval: 2,
                       showTicks: true,
                       showLabels: true,
                       onChanged: (dynamic newValue){
                            setState(() {
                                _values = newValue;
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

![Labels offset support](images/customization/slider-labels-offset.png)

## Divisor customization

### Divisor color

You can change the active and inactive divisor color of the range slider using the `activeDivisorColor` and `inactiveDivisorColor` properties respectively.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _values = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                         activeDivisorColor: Colors.red,
                         inactiveDivisorColor: Colors.red[200],
                    ),
                    child:  SfRangeSlider(
                      min: _min,
                      max: _max,
                      interval: 1,
                      showDivisors: true,
                      values: _values,
                      onChanged: (dynamic newValue){
                            setState(() {
                                _values = newValue;
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

![Divisor color support](images/customization/slider-divisor-color.png)

## Tooltip customization

### Tooltip color

You can change the background color of the tooltip in the range slider using the `tooltipBackgroundColor` property.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _values = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        tooltipBackgroundColor: Colors.red[300],
                    ),
                    child:  SfRangeSlider(
                     min: _min,
                     max: _max,
                     interval: 1,
                     showTicks: true,
                     showLabels: true,
                     showTooltip: true,
                     values: _values,
                     onChanged: (dynamic newValue){
                            setState(() {
                                _values = newValue;
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

![Tooltip color support](images/customization/slider-tooltip-color.png)

## Common

### Active color

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

![Active color support](images/customization/active-color.png)

N> Refer the `SfRangeSliderThemeData` to know about updating the individual active range slider element’s visual.

### Inactive color

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

![Inactive color support](images/customization/inactive-color.png)

N> Refer the `SfRangeSliderThemeData` to know about updating the individual inactive range slider element’s visual.
