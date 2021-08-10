---
layout: post
title: Mirror in Flutter Linear Gauge widget | Syncfusion
description: Learn here about mirroring the Syncfusion Flutter Linear Gauge (SfLinearGauge) widget with isMirrored property
platform: Flutter
control: SfLinearGauge
documentation: ug
---

# Mirrored in Flutter Linear Gauge (SfLinearGauge)

The [`isMirrored`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/isMirrored.html) property in [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html) mirrors all the Gauge elements in the `SfLinearGauge`. The following code sample demonstrates how to setting the [`isMirrored`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/isMirrored.html) property.

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

The following screenshot provides a comparison for the mirrored and normal Linear Gauge. 

![Mirrored linear gauge comparsion](images/mirrored/mirror_comparison.png)