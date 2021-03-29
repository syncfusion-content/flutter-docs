---
layout: post
title: Customize widget pointers in a linear gauge | Syncfusion
description: Detailed tutorial about the widget pointers on Linear Gauge Flutter widget | Flutter Linear Gauge widget|
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Linear Gauge Widget Marker Pointers

The `LinearWidgetPointer` in `SfLinearGauge` allows to use any Flutter widget as marker pointer. The below code snippet uses a [`container`](https://api.flutter.dev/flutter/widgets/Container-class.html) as marker widget.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearWidgetPointer(
              value: 50,
              child: Container(height: 14, width: 14, color: Colors.redAccent),
            ),
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Initialize linear gauge for widget pointer](images/widget-pointer/default_widget_pointer.png)

## Change marker alignment

The widget marker pointer's alignment can be changed by the `markerAlignment` property of `LinearWidgetPointer`. The available marker positions are `start`, `end`, and `center`. 

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
                child:
                    Container(height: 14, width: 14, color: Colors.redAccent)),
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Customize size of widget pointer](images/widget-pointer/widget_alignment.png)

## Change the position

By default, the shape pointer is positioned `outside` to the axis. This position can be changed by the `position` property of a `LinearShapePointer`. It is possible to position the shape pointer as `inside`, `cross`, and `outside` to the axis. The below code snippet demonstrates changing the shape pointer position to `inside` the axis. 

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
              child: Container(height: 14, width: 14, color: Colors.redAccent),
            ),
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change widget pointer position](images/widget-pointer/widget_pointer_position.png)

## Change the offset

In addition to position the widget marker pointer, it is also possible to change the offset of the shape pointer. The `offset` is the distance from the axis and it cannot be negative. The cross positioned elements will not get affected by the `offset` value. The below code snippet demonstrates changing the offset value of the shape pointer. 

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearWidgetPointer(
              value: 50,
              offset: 25,
              position: LinearElementPosition.inside,
              child: Container(
                height: 14,
                width: 14,
                color: Colors.redAccent
              ),
            ),  
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Customize linear gauge bar pointer offset](images/widget-pointer/widget_pointer_offset.png)