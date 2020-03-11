---
layout: post
title: Label customization in Syncfusion Flutter Range Slider | Syncfusion
description: Learn how to customize the label in Syncfusion SfRangeSlider for flutter platform
platform: flutter
control: SfRangeSlider
documentation: ug
---

# Label Customization

The SfRangeSlider provides an option to show or hide the label and color customization.

## Show label

This property is used to display labels for the ticks. When it sets to true, it displays the label for all the ticks. The default value of the `showLabels` property is `false`.

{% tabs %}
{% highlight Dart %}

SfRangeSlider sliderWithLabel() {
   return
     SfRangeSlider(
        interval: 0.2,
        showLabels: true,
        values: _values,
        onChanged: (dynamic values) {
          setState(() {
            _values = values;
          });
       }
   );
}

{% endhighlight %}
{% endtabs %}

![Show slider labels](images/label-customization/show-labels.png)

## Label offset

This property is used to position the label based on the offset value from the track position. The default value of the `labelOffset` property is `Offset(0.0, 13.0)`.

{% tabs %}
{% highlight Dart %}

SfRangeSliderTheme sliderWithLabel() {
   return SfRangeSliderTheme(
     data: SfRangeSliderThemeData(
         labelOffset: Offset(0, -30),
     ),
     child: SfRangeSlider(
         interval: 0.2,
         showLabels: true,
         values: _values,
         onChanged: (dynamic values) {
           setState(() {
             _values = values;
           });
         }),
   );
}

{% endhighlight %}
{% endtabs %}

![Label offset support](images/label-customization/label-offset.png)
