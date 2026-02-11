---
layout: post
title: Track in Flutter Range Slider widget | Syncfusion
description: Learn here all about adding the Track feature in Syncfusion Flutter Range Slider (SfRangeSlider) widget and more.
platform: Flutter
control: SfRangeSlider
documentation: ug
---

# Track in Flutter Range Slider (SfRangeSlider)

This section helps to learn about how to customize the track in the range slider.

## Track color

You can change the active and inactive track color of the range slider using the [`activeTrackColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/activeTrackColor.html) and [`inactiveTrackColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/inactiveTrackColor.html) properties respectively.

The active side of the range slider is between start and end thumbs.

The inactive side of the range slider is between the [`min`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/min.html) value and the left thumb, and the right thumb and the [`max`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/max.html) value.

For RTL, the inactive side is between the [`max`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/max.html) value and the left thumb, and the right thumb and the [`min`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/min.html) value.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderTheme-class.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

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
                        min: 2.0,
                        max: 10.0,
                        values: _values,
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

![Track color support](images/track/slider-track-color.png)

### Vertical

{% tabs %}
{% highlight Dart %}

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
                    child:  SfRangeSlider.vertical(
                        min: 2.0,
                        max: 10.0,
                        values: _values,
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

![Track color support](images/track/vertical-slider-track-color.png)

## Track height

You can change the track height of the range slider using the [`activeTrackHeight`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/activeTrackHeight.html) and the [`inactiveTrackHeight`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/inactiveTrackHeight.html) properties. The default value of the [`activeTrackHeight`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/activeTrackHeight.html) and the [`inactiveTrackHeight`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/inactiveTrackHeight.html) properties are `6.0` and `4.0`.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderTheme-class.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        activeTrackHeight: 8,
                        inactiveTrackHeight: 8,
                    ),
                    child:  SfRangeSlider(
                        min: 2.0,
                        max: 10.0,
                        values: _values,
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

![Track size support](images/track/slider-track-size.png)

### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        activeTrackHeight: 8,
                        inactiveTrackHeight: 8,
                    ),
                    child:  SfRangeSlider.vertical(
                        min: 2.0,
                        max: 10.0,
                        values: _values,
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

![Track size support](images/track/vertical-slider-track-size.png)

## Track corner radius

You can change the corner of the track to be round in the range slider using the [`trackCornerRadius`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/trackCornerRadius.html) property. The default value of the [`trackCornerRadius`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfSliderThemeData/trackCornerRadius.html) property is `1.0`.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderTheme-class.html).

### Horizontal

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        activeTrackHeight: 10,
                        inactiveTrackHeight: 10,
                        trackCornerRadius: 5,
                    ),
                    child: SfRangeSlider(
                        min: 2.0,
                        max: 10.0,
                        values: _values,
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

![Track corner radius support](images/track/slider-track-corner-radius.png)

### Vertical

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 7.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSliderTheme(
                    data: SfRangeSliderThemeData(
                        activeTrackHeight: 10,
                        inactiveTrackHeight: 10,
                        trackCornerRadius: 5,
                    ),
                    child: SfRangeSlider.vertical(
                        min: 2.0,
                        max: 10.0,
                        values: _values,
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

![Track corner radius support](images/track/vertical-slider-track-corner-radius.png)