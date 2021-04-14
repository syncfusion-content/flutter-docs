---
layout: post
title: Mirroring the a linear gauge | Linear Gauge widget| Syncfusion
description: This section explains about how to mirror linear gauge in Flutter platform.
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Flutter Linear Gauge Mirroring

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