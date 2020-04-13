---
layout: post
title: RTL feature in Syncfusion Flutter Range Selector | Syncfusion
description: This section helps to learn about how to change the layout direction in the right to left direction in range selector for Flutter platform
platform: Flutter
control: SfRangeSelector
documentation: ug
---

# Right to Left (RTL) in range selector

The SfRangeSelector supports changing the layout direction of the widget in the right-to-left direction by setting the [`textDirection`](https://api.flutter.dev/flutter/widgets/Directionality/textDirection.html) property to `rtl` in the [`Directionality`](https://api.flutter.dev/flutter/widgets/Directionality-class.html) widget.

You can also change the right to left direction by specifying locale, that supports RTL language such as (Arabic ,Persian ,Hebrew, Pashto and Urdu) by specifying the MaterialApp properties and adding the flutter_localizations package to your application.

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _initialValues = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          backgroundColor: Colors.white,
          body: Directionality(
            textDirection: TextDirection.rtl,
            child: Center(
              child: SfRangeSelector(
                min: _min,
                max: _max,
                interval: 1,
                showLabels: true,
                showTicks: true,
                initialValues: _initialValues,
                child: Container(
                    color: Colors.pink[200],
                    height: 150,
                 ),
              ),
            )
         ),
      )
  );
}

{% endhighlight %}
{% endtabs %}

![RTL support](images/right-to-left/right-to-left-support.png)
