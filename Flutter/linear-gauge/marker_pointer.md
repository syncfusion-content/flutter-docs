---
layout: post
title: Customize marker pointers in a linear gauge | Syncfusion
description: Detailed tutorial about the marker pointers on Linear Gauge Flutter widget | Flutter Linear Gauge widget|
platform: flutter
control: Overview
documentation: ug
---

# Linear Gauge Marker Pointers

A marker pointer is used to indicate a specific value on an axis. So the 'value' is a required property in marker pointers.  In Linear Gauge there are two marker pointers - shape pointer and widget pointer. The shape pointer is having built-in shapes and the widget pointer allows to use any FLutter widgets to mark a specific value in axis. 

## Shape Pointer

The shapePointer in 'SfLinearGauge' have the below pre-defined shapes to mark a specific value. The default shape pointer is inverted triangle. 

1. Triangle
2. Inverted Triangle
3. Circle
4. Diamond
5. Rectangle

The below is the default appearance of default shape pointer.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            markerPointers: [LinearShapePointer(value: 50,)],
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Initialize linear gauge for shape pointer](images/bar-pointer/shape-pointer.png)

