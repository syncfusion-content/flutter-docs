---
layout: post
title:  Accessibility of Syncfusion Flutter Range Selector | Syncfusion
description: This section explains about the accessibility support in Syncfusion Flutter SfRangeSelector widget in Flutter.
platform: Flutter
control: SfRangeSelector
documentation: ug
---

# Accessibility with Flutter Range Selector (SfRangeSelector)

The [`SfRangeSelector`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html) can easily be accessed by screen readers. The default reading format is `The start value is ${values.start} and the end value is ${values.end}`. You can change the reading format using the [`semanticFormatterCallback`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector/semanticFormatterCallback.html) property.

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
              semanticFormatterCallback: (SfRangeValues values){
                return 'SfRangeValues ${values.start} ${values.end}';
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
