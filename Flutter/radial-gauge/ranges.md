---
layout: post
title: Syncfusion Flutter Gauge Range
description: Learn how to add and customizes ranges of radial gauge control
platform: flutter
control: SfRadialGauge
documentation: ug
---

# Range

Gauge range is a visual element that helps to quickly visualize where a value falls on the axis. The text can be easily annotated in range to improve the readability.

**Setting start and end value**

Start and end values of ranges are set by using the [`startValue`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/startValue.html) and [`endValue`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/endValue.html) properties

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(

              child: SfRadialGauge(
                axes: <RadialAxis>[RadialAxis( radiusFactor: 0.9, centerY: 0.65,
                  ranges: <GaugeRange>[GaugeRange(startValue: 30, endValue: 65)]
                )
                ],
              )


    ),
  );
}


{% endhighlight %}

![default range](images/range/range_default.jpg)

## Range Customization

 The following properties are used for the range customization,

* [`color`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/color.html) – used to specifies the color for the range
* [`startWidth`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/startWidth.html) – used to specify the star width of the range either in logical pixel or factor
* [`endWidth`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/endWidth.html) – used to specify the end width of the range either in logical pixel or factor
* [`sizeUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/sizeUnit.html) – specifies whether the start and end width of the range is set in logical pixel or factor

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(

              child: SfRadialGauge(
                axes: <RadialAxis>[RadialAxis( radiusFactor: 0.9, centerY: 0.65,
                  ranges: <GaugeRange>[GaugeRange(startValue: 30, endValue: 65,
                    startWidth: 5, endWidth: 20
                  )]
                )
                ],
              )


    ),
  );
}

{% endhighlight %}

![range thickness](images/range/range_thickness.jpg)

When the [`sizeUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/sizeUnit.html) is set as logical pixel, then range will be rendered based on the provided logical pixel value in [startWidth`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/startWidth.html) and [`endWidth`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/endWidth.html)

If the [`sizeUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/sizeUnit.html) is set as factor, the provided factor value in the start and end width will be multiplied with the axis radius respectively. The factor value ranges from 0 to 1.

**Position customization**

 The range an be moved far or near to the axis line with its [`rangeOffset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/rangeOffset.html) property. The property can be specified either in the logical pixel and the factor value. 

If the [‘sizeUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/sizeUnit.html) is set as logical pixel, then the range will be moved based on the provided logical pixel value.

If the [`sizeUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/sizeUnit.html) is set as factor, the factor value will be multiplied with the axis radius.Then the pointer will be moved to the corresponding value
The [`sizeUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/sizeUnit.html) property is common for [rangeOffset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/rangeOffset.html), [`startWidth`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/startWidth.html) and the [`endWidth`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/endWidth.html) property. The default value of [`sizeUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/sizeUnit.html) is logicalPixel.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(

              child: SfRadialGauge(
                axes: <RadialAxis>[RadialAxis( radiusFactor: 0.9, centerY: 0.65,
                  ranges: <GaugeRange>[GaugeRange(startValue: 30, endValue: 65,
                  rangeOffset: 50,
                  )]
                )
                ],
              )
    ),
  );
}
 
{% endhighlight %}

![range offset](images/range/range_offset.jpg)

## Setting range color to axis elements

You can set the range color to axis labels and ticks with the [`useRangeColorForAxis`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/useRangeColorForAxis.html) property of axis,

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
              child: SfRadialGauge(
                axes: <RadialAxis>[
                  RadialAxis(showAxisLine: false, 
                      ticksPosition: ElementsPosition.outside,
                      labelsPosition: ElementsPosition.outside,
                      startAngle: 270, endAngle: 270, useRangeColorForAxis: true,
                       interval: 10,
                      axisLabelStyle:GaugeTextStyle(
                          fontWeight: FontWeight.w500,
                          fontSize: 12),
                      majorTickStyle: MajorTickStyle(length: 0.15,
                          lengthUnit: GaugeSizeUnit.factor,
                          thickness: 1),
                      minorTicksPerInterval: 4, labelOffset: 15,
                      minorTickStyle: MinorTickStyle(length: 0.04,
                          lengthUnit: GaugeSizeUnit.factor,
                          thickness: 1),
                      ranges: <GaugeRange>[GaugeRange(startValue: 0, endValue: 35,
                          color: Color(0xFFF8B195),
                          sizeUnit: GaugeSizeUnit.factor,
                          rangeOffset: 0.06,
                          startWidth: 0.05, endWidth: 0.25),
                        GaugeRange(startValue: 35, endValue: 70,
                            rangeOffset: 0.06,
                            sizeUnit: GaugeSizeUnit.factor,
                            color: Color(0xFFC06C84),
                            startWidth: 0.05, endWidth: 0.25),
                        GaugeRange(startValue: 70, endValue: 100,
                            rangeOffset: 0.06,
                            sizeUnit: GaugeSizeUnit.factor,
                            color: Color(0xFF355C7D),
                            startWidth: 0.05, endWidth: 0.25),
                      ]
                  )
                ],
              )
    ),
  );
}

{% endhighlight %}

![range color to axis element](images/range/range_axislabels.jpg)

## Range label

A text can be displayed on the range with its [`label`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/label.html) property. The provided text can be customized with the [`labelStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeRange/labelStyle.html) property.

{% highlight dart %}
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
              child: SfRadialGauge(
                axes:<RadialAxis>[
                  RadialAxis(showLabels: false, showAxisLine: false, showTicks: false,
                      minimum: 0, maximum: 99, 
                      ranges: <GaugeRange>[GaugeRange(startValue: 0, endValue: 33,
                          color: Color(0xFFFE2A25), label: 'Slow',
                          sizeUnit: GaugeSizeUnit.factor,
                          labelStyle: GaugeTextStyle(fontFamily: 'Times', fontSize:  20),
                          startWidth: 0.65, endWidth: 0.65
                      ),GaugeRange(startValue: 33, endValue: 66,
                        color:Color(0xFFFFBA00), label: 'Moderate',
                        labelStyle: GaugeTextStyle(fontFamily: 'Times', fontSize:   20),
                        startWidth: 0.65, endWidth: 0.65, sizeUnit: GaugeSizeUnit.factor,
                      ),
                        GaugeRange(startValue: 66, endValue: 99,
                          color:Color(0xFF00AB47), label: 'Fast',
                          labelStyle: GaugeTextStyle(fontFamily: 'Times', fontSize:   20),
                          sizeUnit: GaugeSizeUnit.factor,
                          startWidth: 0.65, endWidth: 0.65,
                        ),

                      ],
                      pointers: <GaugePointer>[NeedlePointer(value: 60
                      )]
                  )
                ],
              )
    ),
  );
}

{% endhighlight %}

![range label](images/range/range_datalabel.jpg)



