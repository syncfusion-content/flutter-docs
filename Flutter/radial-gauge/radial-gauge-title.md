---
layout: post
title: Syncfusion Flutter Gauge Title
description: Learn how to add gauge title and customize its appearance in the Flutter Charts.
platform: flutter
control: SfRadialGauge
documentation: ug
---

# Title

You can define and customize the gauge title using [`title`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge/title.html) property of [`SfRadialGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge-class.html). The [`text`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTitle/text.html) property of [`GaugeTitle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTitle-class.html) is used to set the text for the title.

Following properties are used to customize its appearance.

* [`backgroundColor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTitle/backgroundColor.html) - – used to change the background color.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTitle/borderWidth.html) – used to change the border width
* [` borderColor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTitle/borderColor.html) – used to change the border color
*  [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTitle/textStyle.html) -used to change the text color, size, font family, fontStyle, and font weight.


## Text Alignment

You can align the title text content horizontally to the near, center or far of the chart using the [`alignment`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTitle/alignment.html) property of the [`title`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTitle-class.html).

{% highlight dart %} 

     @override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
        title: GaugeTitle(text: 'SfRadialGauge', 
        backgroundColor: Colors.lightBlueAccent,
        textStyle: TextStyle(fontSize: 15, fontWeight: FontWeight.bold, 
         fontStyle: FontStyle.italic,
         color: Colors.black, fontFamily: 'Times'),
        borderColor: Colors.indigo, borderWidth: 3, 
           alignment: GaugeAlignment.near),
        axes: <RadialAxis>[RadialAxis()],)
    ),
  );
}


{% endhighlight %}

![Gauge title](images/title/gauge_title.jpg)