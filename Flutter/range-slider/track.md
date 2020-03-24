---
layout: post
title: Track features in Syncfusion Flutter Range Slider | Syncfusion
description: This section helps to learn about how to customize the track features in range slider for flutter platform
platform: flutter
control: SfRangeSlider
documentation: ug
---

# Track features in range slider

This section helps to learn about how to customize the track in the range slider.

## Track color

You can change the active and inactive track color of the range slider using the `activeTrackColor` and `inactiveTrackColor` properties respectively.

N> You must import the `theme.dart' library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSliderTheme`](https://help.syncfusion.com/flutter/range-slider/customization).

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

![Track color support](images/track/slider-track-color.png)

## Track height

You can change the track height of the range slider using the `trackHeight` property. The default value of the `trackHeight` property is `2.0`

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

![Track size support](images/track/slider-track-size.png)

## Track corner radius

You can change the corner of the track to be round in the range slider using the `trackCornerRadius` property. The default value of the `trackCornerRadius` property is `1.0`

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

![Track corner radius support](images/track/slider-track-corner-radius.png)
