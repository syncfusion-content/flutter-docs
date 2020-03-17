---
layout: post
title: Labels and divisor features in Syncfusion Flutter Range Slider | Syncfusion
description: This section helps to learn about how to add labels and divisor in the range slider for flutter platform
platform: flutter
control: SfRangeSlider
documentation: ug
---

# Labels and divisor in range slider
This section explains about how to add the labels and divisor in the range slider.

## Show label

Option to render the labels on given interval. The default value of `showLabels` property is `false`.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 6.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider(
                    min: 0.0,
                    max: 10.0,
                    interval: 2,
                    showLabels: true,
                    values: _values,
                    onChanged: (SfRangeValues newValues) {
                        setState(() {
                            _values = newValues;
                        });
                   },
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Range slider label support](images/label-and-divisor/show-labels.png)

N>
* The `numberFormat` and `dateFormat` for formatting the numeric and date labels respectively.
* The `SfRangeSliderThemeData` to customize the appearance of the labels.

## Show divisor

Option to render the divisors on the track. The default value of `showDivisors` property is `false`. It is a shape which is used to represent the major interval points of the track.

For example, if `min` is 0.0 and `max` is 10.0 and `interval` is 2.0, the range slider will render the divisors at 0.0, 2.0, 4.0 and so on.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(4.0, 6.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSlider(
                    min: 0.0,
                    max: 10.0,
                    interval: 2,
                    showDivisors: true,
                    values: _values,
                    onChanged: (SfRangeValues newValues) {
                        setState(() {
                            _values = newValues;
                        });
                   },
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

![Range slider divisor support](images/label-and-divisor/show-divisor.png)
