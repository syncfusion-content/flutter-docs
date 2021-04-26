---
layout: post
title: RTL in Flutter Slider widget | Syncfusion
description: Learn here all about enabling the RTL rendering in the Syncfusion Flutter Slider (SfSlider) widget and more.
platform: Flutter
control: SfSlider
documentation: ug
---

# Right to Left (RTL) in Flutter Slider (SfSlider) 

The Slider supports changing the layout direction of the widget in the right-to-left direction by setting the [`textDirection`](https://api.flutter.dev/flutter/widgets/Directionality/textDirection.html) property to `rtl` in the [`Directionality`](https://api.flutter.dev/flutter/widgets/Directionality-class.html) widget.

{% tabs %}
{% highlight Dart %}

double _value = 40.0;

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

![RTL support](images/right-to-left/right-to-left-support.png)

N> RTL is not applicable for vertical orientation of the slider.