---
layout: post
title: Tick features in Syncfusion Flutter Range Slider | Syncfusion
description: This section helps to learn about how to add major and minor tick in the range slider for flutter platform
platform: flutter
control: SfRangeSlider
documentation: ug
---

# Ticks features for Range Slider

This section helps to learn about how to add major and minor tick in the range slider.

## Show tick

You can enable the major ticks on the track. It is a shape which is used to represent the major interval points of the track. The default value of `showTicks` property is `false`. For example, if `min` is 0.0 and `max` is 4.0 and `interval] is 2.0, the range slider will render the major ticks at 0.0, 2.0, and 4.0.

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
                    showTicks: true,
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

![Range slider tick support](images/tick/major-tick.png)

N> The `tickShape` and `SfRangeSliderThemeData` for customizing the major tick’s visual appearance.

## Show minor tick

Represents the number of smaller ticks between two major ticks. For example, if `min` is 0.0 and `max` is 10.0 and `interval` is 2.0, the range slider will render the major ticks at 0.0, 2.0, 4.0 and so on. If `minorTicksPerInterval` is 1, then smaller ticks will be rendered on 1.0 and 3.0 and so on.

I> The default value of `minorTicksPerInterval` property is null. Must be greater than 0.

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
                    showTicks: true,
                    minorTicksPerInterval: 1,
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

![Range slider minor tick support](images/tick/minor-tick.png)

N>
* The 'showTicks' to render major ticks at given interval.
* The `minorTickShape` and `SfRangeSliderThemeData` for customizing the minor tick’s visual appearance.
