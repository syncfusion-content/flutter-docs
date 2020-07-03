---
layout: post
title:  Accessibility of Syncfusion Flutter Slider | Syncfusion
description: This section explains about the accessibility support in Syncfusion Flutter SfSlider widget in Flutter.
platform: Flutter
control: SfSlider
documentation: ug
---

# Accessibility with Flutter Slider (SfSlider)

The `SfSlider` can easily be accessed by screen readers. The default reading format is `$value`. You can change the reading format using the `semanticFormatterCallback` property.

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
                return 'The selected value is ${value}';
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
