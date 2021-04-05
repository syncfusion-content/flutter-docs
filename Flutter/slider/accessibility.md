---
layout: post
title:  Accessibility of Syncfusion Flutter Slider | Syncfusion
description: This section explains about the accessibility support in Syncfusion Flutter SfSlider widget in Flutter.
platform: Flutter
control: SfSlider
documentation: ug
---

# Accessibility with Flutter Slider (SfSlider)

The [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html) can easily be accessed by screen readers. By default, it will read the current value. You can change the reading format using the [`semanticFormatterCallback`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/semanticFormatterCallback.html) property.

You can adjust the value of thumb by tapping it and then pressing the volume buttons to increase or decrease the value.

## Horizontal

{% tabs %}
{% highlight Dart %}

double _value = 40.0;

@override
Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider(
              min: 0.0,
              max: 100.0,
              value: _value,
              interval: 20,
              showTicks: true,
              showLabels: true,
              semanticFormatterCallback: (dynamic value){
                return 'The selected value is $value';
              },
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
                });
              },
            ),
          )
      ),
   );
}

{% endhighlight %}
{% endtabs %}


## Vertical

{% tabs %}
{% highlight Dart %}

double _value = 40.0;

@override
Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfSlider.vertical(
              min: 0.0,
              max: 100.0,
              value: _value,
              interval: 20,
              showTicks: true,
              showLabels: true,
              semanticFormatterCallback: (dynamic value){
                return 'The selected value is $value';
              },
              onChanged: (dynamic newValue) {
                setState(() {
                  _value = newValue;
                });
              },
            ),
          )
      ),
   );
}

{% endhighlight %}
{% endtabs %}
