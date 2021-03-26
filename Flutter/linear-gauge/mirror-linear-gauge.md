---
layout: post
title: Mirroring the a linear gauge | Linear Gauge widget| Syncfusion
description: Tutorial about deatils of the merroring on Linear Gauge Flutter widget | Flutter Linear Gauge widget documentation|
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Flutter Linear Gauge Mirroring

The `isMirrored` property in `SfLinearGauge` mirrors all the gauge elements in the `SfLinearGauge`. The below code snippet demonstrates setting the `isMirrored` property.

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

The below screenshot provides a comparison for the mirrored and normal linear gauge. 

![Mirrored linear gauge comparsion](images/mirrored/mirror_comparison.png)