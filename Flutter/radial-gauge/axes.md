---
layout: post
title: Axis of Syncfusion Flutter Gauge
description: Learn how to add and customizes axis and its element
platform: flutter
control: SfRadialGauge
documentation: ug
---

# Axes

The [`radial axis`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis-class.html) is a circular arc in which a set of values are displayed along a linear or custom scale based on the design requirements. Axis elements, such as labels, ticks, and axis line, can be easily customized with built-in properties.

## Axis minimum and maximum 

The [`minimum`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/minimum.html) and [`maximum`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/maximum.html) property of the axis can be used to customize the axis range. The default value of [minimum](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/minimum.html) is 0 and the default value of [‘maximum`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/maximum.html) is 100.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(minimum: -60, maximum: 60)]
     ),
    ),

  );
}

{% endhighlight %}

![axis range](images/axis/axis_range.jpg)

## Angle Customization

The radial axis’s start, and the end angle can be customized using its [`startAngle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/startAngle.html) and [`endAngle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/startAngle.html) property

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(startAngle: 180, endAngle: 90,)]
     ),
    ),

  );
}

{% endhighlight %}

![axis angle customization](images/axis/axis_angle.jpg)

## Radius customization

The radius of the radial axis can be customized using its [`radiusFactor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/radiusFactor.html) property. The default value of the [`radiusFactor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/radiusFactor.html) is 0.95. The value of [`radiusFactor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/radiusFactor.html) ranges from 0 to 1. For example, When the [`radiusFactor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/radiusFactor.html) value is 1, the full radius will be considered for rendering the axis and when when the [‘radiusFactor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/radiusFactor.html) value is 0.5, then half of the radius value will be considered for rendering the circle.

{% highlight dart %}

@@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(),
         RadialAxis(radiusFactor: 0.5)]
     ),
    ),

  );
}

{% endhighlight %}

![axis radius customization](images/axis/axis_radius.jpg)

## Axis position customization

The position of the [`radial axis`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis-class.html) can be customized using its [`centerX`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/centerX.html) and [`centerY`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/centerY.html) value. The default value of [`centerX`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/centerX.html) and [`centerY`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/centerY.html) property is 0.5. Therefore, the axis will be positioned in the center of provided size of gauge.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(startAngle: 270, endAngle: 270, interval: 10),
         RadialAxis( centerY: 0.55, centerX: 0.35,
             radiusFactor: 0.3, startAngle: 270, endAngle: 270, interval: 20)]
     ),
    ),

  );
}

{% endhighlight %}

![axis position customization](images/axis/axis_center.jpg)

## Axis label rotation

The axis label can be rotated based on its current angle by using [‘needsRotateLabels`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/needsRotateLabels.html) property of axis. The default value of [‘needsRotateLabels`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/needsRotateLabels.html) is false.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis( needsRotateLabels: true)]
     ),
    ),

  );
}

{% endhighlight %}

![axis label rotation](images/axis/axis_rotate.jpg)

## Edge label customization

The visibility of the first and the label of the axis can be customized with [`showFirstLabel`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/showFirstLabel.html) and [`showLastLabel`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/showLastLabel.html) property. 

* [`showFirstLabel`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/showFirstLabel.html) – used to enable or disable the first label of the axis
* [`showLastLabel`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/showLastLabel.html) – used to enable or disable the last label of the axis
The default value of both the [`showFirstLabel`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/showFirstLabel.html) and the [`showLastLabel`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/showLastLabel.html) property is true.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis( interval: 1, showFirstLabel: false,
           startAngle: 270, endAngle: 270, minimum: 0, maximum: 12),
        ]
     ),
    ),

  );
}

{% endhighlight %}

![axis edge label](images/axis/axis_showfirstlabel.jpg)

## Axis direction customization

The direction of [`radial axis`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis-class.html) can be customized by its [isInversed`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/isInversed.html) property. 

When the [`isInversed`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/isInversed.html) property is true, the axis can be placed is anti-clockwise direction. When the [`isInversed`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/isInversed.html) property is set as false, the axis will be positioned in clock-wise direction

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis( isInversed: true)]
     ),
    ),

  );
}

{% endhighlight %}

![axis direction](images/axis/axis_inversed.jpg)

## Maximum number of labels per 100 logical pixels

By default, a maximum of 3 labels are displayed for each 100 logical pixels in axis. The maximum number of labels that should be present within 100 logical pixels length can be customized using the [`maximumLabels`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/maximumLabels.html) property of an axis. This property is applicable only for automatic range calculation and will not work if you set value for interval property of an axis.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis( maximumLabels: 5),
        ]
     ),
    ),

  );
}

{% endhighlight %}

![axis maximum labels](images/axis/axis_maximumlabels.jpg)

## Interval

The [`interval`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/interval.html) between labels can be customized using the [‘interval’](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/interval.html) property of axis.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(interval: 20),
        ]
     ),
    ),

  );
}

{% endhighlight %}

![axis label interval](images/axis/axis_interval.jpg)

## Axis line customization

The radial axis line can be customized using its [axisLineStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/axisLineStyle.html) property. The following properties can be customized using [`axisLineStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/axisLineStyle.html).

* [`thickness`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLineStyle/thickness.html) – used to customize the thickness of axis line
* [`thicknessUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLineStyle/thicknessUnit.html) – allows to specify the thickness of the axis either in logical pixel or factor. Its default value is logicalPixel.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLineStyle/color.html) – used to customize the color of the axis line
* [`cornerStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLineStyle/cornerStyle.html) – allows to customize the corner of the axis line. 
* [dashArray](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLineStyle/dashArray.html) – allows to customize the axis line as dashed circular arc

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(
         axisLineStyle: AxisLineStyle(thickness: 0.1,
           thicknessUnit: GaugeSizeUnit.factor, color: Colors.deepPurple,)),
        ]
     ),
    ),

  );
}

{% endhighlight %}

![axis line customization](images/axis/axis_color.jpg)

##  Rounded Corners

The [`cornerStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLineStyle/cornerStyle.html) property of [`axisLineStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLineStyle-class.html) specifies the corner type for axis line. The corners can be customized using the bothFlat, bothCurve, startCurve, and endCurve options. The default value of this property is bothFlat.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(axisLineStyle: AxisLineStyle(thickness: 15,              
         cornerStyle:CornerStyle.bothCurve)),
        ]
     ),
    ),

  );
}
{% endhighlight %}

![axis corner](images/axis/axis_corner.jpg)

**Dashed axis line**

The [‘dashArray`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLineStyle/dashArray.html) property of [‘axisLineStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLineStyle-class.html) allows to render the dashed axis line.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(
         axisLineStyle: AxisLineStyle( dashArray: <double>[5,5])),
        ]
     ),
    ),

  );
}

{% endhighlight %}

![dashed axis line](images/axis/axis_dasharray.jpg)

**Axis line visibility**

The visibility of the axis line can be customized using [‘showAxisLine`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/showAxisLine.html) property of axis. By default, the property is set as true

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(showAxisLine: false)]
     ),
    ),

  );
}

{% endhighlight %}

![axis line visibility](images/axis/axis_showline.jpg)

## Label style customization

The axis labels can be customized using the [`axisLabelStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/axisLabelStyle.html) property of axis. The following properties can be customized using the [`axisLabelStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/axisLabelStyle.html)

* [`color`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTextStyle/color.html) – allows to customize the color of the labels
* [`fontFamily`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTextStyle/fontFamily.html) – allows to specify the font family for labels
* [`fontStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTextStyle/fontStyle.html) – allows to specify the font style for labels
* [‘fontWeight`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTextStyle/fontWeight.html) – allows to specify the font weight for labels
* [`fontSize`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeTextStyle/fontSize.html) – allows to specify the font size for labels

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(axisLabelStyle: GaugeTextStyle(
            color: Colors.red, fontSize: 15, 
             fontStyle:FontStyle.italic,
             fontWeight: FontWeight.bold, fontFamily: 'Times') ),
        ]
     ),
    ),

  );
}

{% endhighlight %}

![axis label customization](images/axis/axis_label.jpg)

**Formatting axis label**

The following property of the axis allows to customize the axis label text

* [‘labelFormat`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/labelFormat.html) - allows to add prefix or suffix with the axis labels

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(labelFormat: '{value}m' ),
        ]
     ),
    ),

  );
}

{% endhighlight %}

![axis label format](images/axis/axis_labelFormat.jpg)

* [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/numberFormat.html)- allows to customize the axis label with the [`globalized label format`]

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(
        numberFormat: NumberFormat.compactSimpleCurrency()),
        ]
     ),
    ),

  );
}


{% endhighlight %}

![axis number format](images/axis/axis_numberFormat.jpg)

**Label visibility**

The [`showLabels`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/showLabels.html) property of axis allows to enable or disable the visibility of labels. The default value of the property is true.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(showLabels: false ),
        ]
     ),
    ),

  );
}


{% endhighlight %}

![axis label visibility](images/axis/axis_showLabels.jpg)

## Tick customization

The major and minor tick lines of the axis can be customized with its [`majorTickStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/majorTickStyle.html) and [`minorTickStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/minorTickStyle.html) property respectively.  The following properties can be customized for both the major and the minor ticks
* [`color`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MajorTickStyle/color.html) – allows to customize the tick color
* [`thickness`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MajorTickStyle/thickness.html) – allows to customize the thickness of ticks
* [`length`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MajorTickStyle/length.html) – specifics the length of ticks
* [`lengthUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MajorTickStyle/lengthUnit.html) – allows to specifics the tick length either in logical pixel or factor
* [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MajorTickStyle/dashArray.html) – specifies the dash array to draw the dashed tick line

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(majorTickStyle: MajorTickStyle(length: 0.1, lengthUnit: GaugeSizeUnit.factor, thickness: 1.5, color: Colors.black),
         minorTickStyle: MinorTickStyle(length: 0.05, lengthUnit: GaugeSizeUnit.factor, thickness: 1.5, color: Colors.black)

          ),
        ]
     ),
    ),

  );
}

{% endhighlight %}

![axis tick customization](images/axis/axis_ticks.jpg)

**Dashed tick lines**

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MajorTickStyle/dashArray.html) property of both the [`majorTickStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/majorTickStyle.html) and [`minorTickStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/minorTickStyle.html) allows to draw the tick line as dashed line.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(
         majorTickStyle: MajorTickStyle(length: 20, dashArray: <double>[5,2.5]),
         minorTickStyle: MinorTickStyle(length: 15, dashArray: <double>[3,2.5])

          ),
        ]
     ),
    ),

  );
}

{% endhighlight %}

![dashed tick lines](images/axis/axis_tickdash.jpg)

**Minor tick interval**

The major ticks are generated based on the [`interval`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/interval.html) property. Like major ticks, the minor ticks are calculated the [`minorTicksPerInterval`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/minorTicksPerInterval.html) property of axis. By default, the value is 1.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(minorTicksPerInterval: 4
          ),
        ]
     ),
    ),
  );
}

{% endhighlight %}

![minor tick line](images/axis/axis_minortick.jpg)

**Tick line visibility**

The [`showTicks`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/showTicks.html) property of the axis is used to enable or disable the visibility of both the major and the minor ticks of axis. The default value of the property is true

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(showTicks: false),
        ]
     ),
    ),
  );
}

{% endhighlight %}

![tick line visibilty](images/axis/axis_showticks.jpg)

**Label and tick Placement**

The [`radial axis`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis-class.html) allows to position the labels and ticks either inside or outside to the axis line by using its [`labelsPosition`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/labelsPosition.html) and [`ticksPosition`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/ticksPosition.html) property. By default, both labels and ticks are positioned inside to the axis line

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(
          labelsPosition: ElementsPosition.outside,
         ticksPosition: ElementsPosition.outside
          ),
        ]
     ),
    ),
  );
}

{% endhighlight %}

![label and tick placement](images/axis/axis_outside.jpg)

**Tick position customization**

The ticks can be moved near or far to the axis line with the [`tickOffset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/tickOffset.html) property. The [‘offsetUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/offsetUnit.html) property of axis allows to specify the tick offset either in factor or logical pixel and the default value of [`offsetUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/offsetUnit.html) is logicalPixel
By default, the value of tick offset is 0.
While setting offset for the ticks, the axis labels also moved along with the ticks.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(
          tickOffset: 20
          ),
        ]
     ),
    ),
  );
}

{% endhighlight %}

![axis tick offset](images/axis/axis_tickOffset.jpg)

The code example shows how to tick offset with the [`offsetUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/offsetUnit.html) property of axis

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(tickOffset: 0.2,
          labelOffset: 0.2, offsetUnit: GaugeSizeUnit.factor
          ),
        ]
     ),
    ),
  );
}


{% endhighlight %}

![axis tick and label offset](images/axis/axis_bothOffset.jpg)

**Label position customization**

The [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/labelOffset.html) property allows the adjust the distance between the tick end and the labels. [‘offsetUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/offsetUnit.html) property of axis allows to specify the label offset either in factor or logical pixel. By default, the value of the label offset is 15.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(
          labelOffset: 0.3, offsetUnit: GaugeSizeUnit.factor
          ),
        ]
     ),
    ),
  );
}

{% endhighlight %}

![axis label offset](images/axis/axis_labelOffset.jpg)

The [`offsetUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/offsetUnit.html) property of axis is common for both the [`tickOffset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/tickOffset.html) and [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeAxis/labelOffset.html)

N > [`GaugeSizeUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/GaugeSizeUnit-class.html) allows to specify the value either in logical pixel or in factor. GaugeSizeUnit.factor ranges from 0 to 1. For example, when setting factor as 0.5, the half of axis radius value will be considered.

## Multiple axis

The [`Radial Gauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge-class.html) allows you to add n number of radial axis in its axes collection. Also, we can customize individual axis added in the [`axes`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge/axes.html) collection.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes: <RadialAxis>[ RadialAxis(minimum:  0 , maximum: 100, interval: 10,
           ticksPosition: ElementsPosition.outside,
           labelsPosition: ElementsPosition.outside,

           minorTicksPerInterval: 5,
           radiusFactor: 0.9, labelOffset: 15,
           minorTickStyle: MinorTickStyle(thickness: 1.5,
            color: Color.fromARGB(255, 143, 20, 2),
            length: 0.07, lengthUnit: GaugeSizeUnit.factor),
           majorTickStyle: MinorTickStyle(thickness: 1.5,
             color: Color.fromARGB(255, 143, 20, 2),
             length: 0.15, lengthUnit: GaugeSizeUnit.factor,),
           axisLineStyle: AxisLineStyle( thickness: 3, 
            color: Color.fromARGB(255, 143, 20, 2), ),
           axisLabelStyle: GaugeTextStyle(fontSize: 12,
             color:Color.fromARGB(255, 143, 20, 2),),),

         RadialAxis(minimum:  0 , maximum: 60, interval: 10,
           radiusFactor:  0.6, labelOffset: 15, isInversed: true,
           minorTicksPerInterval: 5,
           minorTickStyle: MinorTickStyle(color: Colors.black, thickness: 1.5,
               lengthUnit: GaugeSizeUnit.factor, length: 0.07),
           majorTickStyle: MajorTickStyle(color: Colors.black, thickness: 1.5,
               lengthUnit: GaugeSizeUnit.factor, length: 0.15),
           axisLineStyle: AxisLineStyle(color: Colors.black, thickness: 3, ),
           axisLabelStyle: GaugeTextStyle(color:  Colors.black, fontSize: 12),

         ),
       ],
     )
    ),
  );
}

{% endhighlight %}

![axis label offset](images/axis/axis_multiplescale.jpg)

## Events

**onLabelCreated**

The [`onLabelCreated`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/onLabelCreated.html) event is called when the axis label is created. The following property can be customized for the corresponding axis label when this event args.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLabelCreatedArgs/text.html) – allows to customize the text property of label
* [`labelStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLabelCreatedArgs/labelStyle.html) – used to customize the label color, font style, font family, font weight
* [`canRotate`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/AxisLabelCreatedArgs/canRotate.html) – used to specify whether to rotate the label based on its current angle


{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(
          onLabelCreated:axisLabelCreated,
          ),
        ]
     ),
    ),
  );
}

void axisLabelCreated(AxisLabelCreatedArgs args){
  if(args.text == '100'){
    args.labelStyle = GaugeTextStyle(color: Colors.red,fontStyle: FontStyle.italic,
        fontFamily: 'Times', fontWeight: FontWeight.bold, fontSize: 15);
    args.canRotate = true;
    args.text = '100 %';
  }
}


{% endhighlight %}

![axis label offset](images/axis/axis_labelCreated.jpg)

**onAxisTapped**

The [`onAxisTapped`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/RadialAxis/onAxisTapped.html) is called when the axis is tapped. The corresponding axis value at tapped positioned will be get from the event.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
     child: SfRadialGauge(
       axes:<RadialAxis>[RadialAxis(
          onAxisTapped: axisTapped
          ),
        ]
     ),
    ),
  );
}


void axisTapped(double _tappedValue){
  final double _value = _tappedValue;
}

{% endhighlight %}

