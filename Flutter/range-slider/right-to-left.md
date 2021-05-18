---
layout: post
title: RTL in Flutter Range Slider widget | Syncfusion
description: Learn here all about the RTL rendering in Syncfusion Flutter Range Slider (SfRangeSlider) widget and more.
platform: Flutter
control: SfRangeSlider
documentation: ug
---

# Right To Left (RTL) in Flutter Range Slider (SfRangeSlider)

## RTL rendering ways

Right to left rendering can be switched in the following ways:

### Wrapping the SfRangeSlider with Directionality widget

The SfRangeSlider supports changing the layout direction of the widget in the right-to-left direction by setting the [`textDirection`](https://api.flutter.dev/flutter/widgets/Directionality/textDirection.html) property to `rtl` in the [`Directionality`](https://api.flutter.dev/flutter/widgets/Directionality-class.html) widget.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(40.0, 60.0);

@override
Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
            body: Directionality(
              textDirection: TextDirection.rtl,
              child: Center(
                child: SfRangeSlider(
                  min: 0.0,
                  max: 100.0,
                  values: _values,
                  interval: 20,
                  showTicks: true,
                  showLabels: true,
                  onChanged: (SfRangeValues newValues){
                    setState(() {
                      _values = newValues;
                    });
                  },
                ),
              )
            ),
        )
    );
}

{% endhighlight %}
{% endtabs %}

N> This RTL support is not applicable for the vertical orientation of the range slider.

### Changing the locale to RTL languages

To change the range slider rendering direction from right to left, you can change the locale to any of the RTL languages such as Arabic, Persian, Hebrew, Pashto, and Urdu.

{% tabs %}
{% highlight Dart %}

dependencies:
  flutter_localizations:
    sdk: flutter

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(40.0, 60.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
    localizationsDelegates: [
      GlobalMaterialLocalizations.delegate,
      GlobalWidgetsLocalizations.delegate,
    ],
    supportedLocales: [
      Locale("fa", "IR"),
    ],
    locale: Locale("fa", "IR"),
    home: Scaffold(
      backgroundColor: Colors.white,
      body: SfRangeSlider(
        min: 0.0,
        max: 100.0,
        values: _values,
        interval: 20.0,
        showLabels: true,
        showTicks: true,
        onChanged: (SfRangeValues newValues) {
          setState(() {
            _values = newValues;
          });
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![RTL support](images/right-to-left/right-to-left-support.png)