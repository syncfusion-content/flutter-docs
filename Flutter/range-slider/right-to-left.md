---
layout: post
title: RTL feature in Syncfusion Flutter Range Slider | Syncfusion
description: This section explains about how to render the Flutter range slider in right to left direction using Directionality widget.
platform: Flutter
control: SfRangeSlider
documentation: ug
---

# Right to Left (RTL) in range slider

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

![RTL support](images/right-to-left/right-to-left-support.png)

N> This RTL support is not applicable for the vertical orientation of the range slider.
