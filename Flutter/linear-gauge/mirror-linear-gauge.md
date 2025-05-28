---
layout: post
title: Mirror in Flutter Linear Gauge widget | Syncfusion
description: Learn here about mirroring the Syncfusion Flutter Linear Gauge (SfLinearGauge) widget with isMirrored property
platform: Flutter
control: SfLinearGauge
documentation: ug
---

# Mirrored in Flutter Linear Gauge (SfLinearGauge)

The [`isMirrored`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/isMirrored.html) property in [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html) allows you to mirror all the gauge elements. This feature is useful when you need to display the gauge in the opposite direction.

{% highlight dart %}

  @override
  Widget build(BuildContext context) {
    return Center(
      child: SfLinearGauge(isMirrored: true)
    );
  }

{% endhighlight %}

![Mirror linear gauge](images/mirrored/mirrored.png)

## Comparison for the mirrored and normal gauge

The following screenshot provides a visual comparison between a mirrored Linear Gauge and a normal Linear Gauge. 

![Mirrored linear gauge comparsion](images/mirrored/mirror_comparison.png)