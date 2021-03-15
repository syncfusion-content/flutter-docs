---
layout: post
title: Interaction in linear gauge | Linear Gauge widget| Syncfusion
description: Tutorial about deatils of the interaction on Linear Gauge Flutter widget | Flutter Linear Gauge widget documentation|
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Flutter Linear Gauge Interaction

The shape and widget marker pointers in a Linear Gauge can be moved from one value to another with swipe or drag gestures.

## Interaction with marker pointer

The `onValueChanged` call back is used to change the value of the marker pointer.

The below code snippet demonstrates updating the marker pointer value based on swipe or drag gesture.

{% highlight dart %}

  @override
  Widget build(BuildContext context) {
    return SfLinearGauge(
      isMirrored: true,
    );
  }

{% endhighlight %}

![shape pointer in linear gauge](images/getting-started/add_shape_pointer.png)