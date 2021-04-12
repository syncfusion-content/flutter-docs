---
layout: post
title:  Accessibility of Syncfusion Flutter Range Selector | Syncfusion
description: This section explains about the accessibility support in Syncfusion Flutter SfRangeSelector widget in Flutter.
platform: Flutter
control: SfRangeSelector
documentation: ug
---

# Accessibility with Flutter Range Selector (SfRangeSelector)

The [`SfRangeSelector`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html) can easily be accessed by screen readers. The default reading format for start thumb is `The start value is ${values.start}` and end thumb is `the end value is ${values.end}`. You can change the reading format using the [`semanticFormatterCallback`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector/semanticFormatterCallback.html) property.

For android, you can adjust the value of each thumb by tapping it and then pressing the volume buttons to increase or decrease the value.

For iOS, you can adjust the value of each thumb by tapping it and then swiping up or down to increase or decrease the value respectively.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(40.0, 60.0);

@override
Widget build(BuildContext context) {
   return MaterialApp(
      home: Scaffold(
          body: Center(
            child: SfRangeSelector(
              min: 0.0,
              max: 100.0,
              initialValues: _values,
              interval: 20,
              showTicks: true,
              showLabels: true,
              semanticFormatterCallback: (dynamic value, SfThumb thumb){
                return 'The $thumb value is $value';
              },
              onChanged: (SfRangeValues newValues) {
                setState(() {
                  _values = newValues;
                });
              },
              child: Container(
                height: 200,
                color: Colors.pink[200],
              ),
            ),
          )
      ),
   );
}

{% endhighlight %}
{% endtabs %}
