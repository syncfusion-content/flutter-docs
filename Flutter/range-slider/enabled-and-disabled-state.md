---
layout: post
title: Disable state in Syncfusion Flutter Range Slider | Syncfusion
description: This section helps to learn about the disabled state of the range slider and its feature in the Flutter platform
platform: Flutter
control: SfRangeSlider
documentation: ug
---

# Disabled state in range slider

This section helps to learn about the disabled state in the Flutter range slider.

## Disabled state

The range slider will goes to disabled state when setting [`onChanged`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/onChanged.html) property to `null`.

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

![Disabled range slider](images/enabled-and-disabled/disabled-state.png)

## Disabled color

You can change the color of the range slider features in disabled state.

* The color of the active and inactive track using the [`disabledActiveTrackColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledActiveTrackColor.html) and [`disabledInactiveTrackColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledInactiveTrackColor.html) properties.
* The color of the active and inactive major ticks using the [`disabledActiveTickColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledActiveTickColor.html) and [`disabledInactiveTickColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledInactiveTickColor.html) properties.
* The color of the active and inactive minor ticks using the [`disabledActiveMinorTickColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledActiveMinorTickColor.html) and [`disabledInactiveMinorTickColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledInactiveMinorTickColor.html) properties.
* The color of the active and inactive divisors using the [`disabledActiveDivisorColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledActiveDivisorColor.html) and [`disabledInactiveDivisorColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledInactiveDivisorColor.html) properties.
* The color of the thumb using the [`disabledThumbColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledThumbColor.html) property.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderTheme-class.html).

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
                        disabledActiveTrackColor: Colors.orange,
                        disabledInactiveTrackColor: Colors.orange[200],
                        disabledActiveTickColor: Colors.orange,
                        disabledInactiveTickColor: Colors.orange[200],
                        disabledActiveMinorTickColor: Colors.orange,
                        disabledInactiveMinorTickColor: Colors.orange[200],
                        disabledActiveDivisorColor: Colors.purple,
                        disabledInactiveDivisorColor: Colors.purple[200],
                        disabledThumbColor: Colors.orange,
                    ),
                    child:  SfRangeSlider(
                     min: 2.0,
                     max: 10.0,
                     interval: 2,
                     showTicks: true,
                     minorTicksPerInterval: 1,
                     showDivisors: true,
                     values: _values,
                  ),
              )
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Disabled color support](images/enabled-and-disabled/slider-disabled-color.png)
