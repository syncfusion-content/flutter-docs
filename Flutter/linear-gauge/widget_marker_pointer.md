---
layout: post
title: Customize widget pointers in a linear gauge | Syncfusion
description: Detailed tutorial about the widget pointers on Linear Gauge Flutter widget | Flutter Linear Gauge widget|
platform: flutter
control: Overview
documentation: ug
---

# Linear Gauge Shape Marker Pointers

The 'LinearWidgetPointer' in 'SfLinearGauge' allows to use any Flutter widget as marker pointer. The below code snippet uses a container as marker widget.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearWidgetPointer(
              value: 50,
              child: Container(
                height: 14,
                width: 14,
                color: Colors.redAccent,
              ),
            ),
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change shape pointer elevation](images/widget-pointer/default_widget_pointer.png)

## Change marker alignment

The marker alignment can be changed by the 'markerAlignment' property of 'LinearWidgetPointer'. The available marker positions are 'start', 'end', and 'center'. 

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(axisTrackExtent: 30, markerPointers: [
            LinearWidgetPointer(
              value: 0,
              markerAlignment: LinearMarkerAlignment.center,
            ),
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change shape pointer elevation](images/widget-pointer/widget_alignment.png)

## Change the position

By default, the shape pointer is positioned outside to the axis. This position can be changed by the 'position' property of a 'LinearShapePointer'. It is possible to position the shape pointer 'inside', 'cross', and 'outside' the axis. The below code snippet demonstrates changing the shape pointer position to inside the axis. 

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearWidgetPointer(
              value: 55,
              position: LinearElementPosition.inside,
              child: Container(
                height: 14,
                width: 14,
                color: Colors.redAccent,
              ),
            ),
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change shape pointer elevation](images/widget-pointer/widget_pointer_position.png)

## Change the offset

In addition to position the shape pointer, it is also possible to change the offset of the shape pointer. The offset is calculated as the distance from the axis. The offset cannot be negative and the cross positioned elements will not get affected by the offset value. The below code snippet demonstrates changing the offset value of the shape pointer. 

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearShapePointer(
              value: 50,
              offset: 25,
              shapeType: LinearShapePointerType.triangle,
              position: LinearElementPosition.inside,
            ),
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Customize linear gauge bar pointer offset](images/widget-pointer/widget_pointer_offset.png)