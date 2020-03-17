---
layout: post
title: Tooltip features in Syncfusion Flutter Range Slider | Syncfusion
description: This section helps to learn about how to add tooltip and its features in range slider for flutter platform
platform: flutter
control: SfRangeSlider
documentation: ug
---

# Tooltip features in range slider

This section helps to learn about how to add tooltip in the range slider.

## Show tooltip

You can enable tooltips for both thumbs. It is used to clearly indicate the current selection of the ranges during interaction. By default, tooltip text is formatted with either `numberFormat` or `dateFormat`.

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
                    showTooltip: true,
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

![Range slider tooltip support](images/tooltip/show-tooltip.png)

N>
* The `tooltipTextFormatterCallback` for changing the default tooltip text.
* The `SfRangeSliderThemeData` to customize the appearance of the tooltip text.
