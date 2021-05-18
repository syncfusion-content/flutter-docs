---
layout: post
title: RTL in Flutter Slider widget | Syncfusion
description: Learn here all about enabling the RTL rendering in the Syncfusion Flutter Slider (SfSlider) widget and more.
platform: Flutter
control: SfSlider
documentation: ug
---

# Right To Left (RTL) in Flutter Slider (SfSlider)

## RTL rendering ways

Right to left rendering can be switched in the following ways:

### Wrapping the SfSlider with Directionality widget

The Slider supports changing the layout direction of the widget in the right-to-left direction by setting the [`textDirection`](https://api.flutter.dev/flutter/widgets/Directionality/textDirection.html) property to `rtl` in the [`Directionality`](https://api.flutter.dev/flutter/widgets/Directionality-class.html) widget.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
        body: Directionality(
            textDirection: TextDirection.rtl,
            child: Center(
              child: SfSlider(
                min: 0.0,
                max: 100.0,
                value: _value,
                interval: 20,
                showTicks: true,
                showLabels: true,
                onChanged: (dynamic newValue){
                  setState(() {
                    _value = newValue;
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

N> RTL is not applicable for vertical orientation of the slider.

### Changing the locale to RTL languages

To change the slider rendering direction from right to left, you can change the locale to any of the RTL languages such as Arabic, Persian, Hebrew, Pashto, and Urdu.

{% tabs %}
{% highlight Dart %}

dependencies:
  flutter_localizations:
    sdk: flutter

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight Dart %}

double _value = 40.0;

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
      body: SfSlider(
        min: 0.0,
        max: 100.0,
        value: _value,
        interval: 20.0,
        showLabels: true,
        showTicks: true,
        onChanged: (dynamic newValue) {
          setState(() {
            _value = newValue;
          });
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![RTL support](images/right-to-left/right-to-left-support.png)