---
layout: post
title: Customize shape pointers in a linear gauge | Syncfusion
description: Detailed tutorial about the shape pointers on Linear Gauge Flutter widget | Flutter Linear Gauge widget|
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Linear Gauge shape marker pointers

The [`LinearShapePointer`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer-class.html) in [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html) have the below pre-defined shapes to mark a specific value. The default shape pointer is inverted `invertedTriangle`. 

1. `Triangle`
2. `Inverted Triangle`
3. `Circle`
4. `Diamond`
5. `Rectangle`

The below is the default appearance of default shape pointer.

{% highlight dart %} 

 @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            markerPointers: [LinearShapePointer(value: 50)]
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Initialize linear gauge for shape pointer](images/shape-pointer/default_shape_pointer.png)

## Change the size

The size of the marker pointer can be changed by the [`height`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/height.html) and [`width`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/width.html) properties of [`LinearShapePointer`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer-class.html). The below code snippet demonstrates changing the size of a shape pointer.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearShapePointer(value: 50, height: 25, width: 25)
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Set size of linear gauge shape pointer](images/shape-pointer/shape_pointer_size.png)

## Change the color

The color of the shape pointer can be changed by the [`color`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/color.html) property. The below code example demonstrates the same.

{% highlight dart %} 

 @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearShapePointer(value: 50, color: Colors.redAccent)
          ]),
        ),
      ),
    );
  
{% endhighlight %}

![Change shape pointer color](images/shape-pointer/shape_pointer_color.png)

## Customize the border

The border can be customized by the [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/borderColor.html) and [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/borderWidth.html) of the [`LinearShapePointer`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer-class.html).

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearShapePointer(
                value: 50, borderColor: Colors.redAccent, borderWidth: 2)
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Customize shape pointer border](images/shape-pointer/shape_border.png)

## Customize the elevation

The elevation can be customized by the [`elevation`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/elevation.html) and [`elevationColor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/elevationColor.html) properties.

{% highlight dart %} 

   @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: Container(
            color: Colors.white,
            child: SfLinearGauge(markerPointers: [
              LinearShapePointer(
                  value: 50,
                  shapeType: LinearShapePointerType.circle,
                  elevation: 5,
                  elevationColor: Colors.blueGrey)
            ]),
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change shape pointer elevation](images/shape-pointer/pointer_elevation.png)

## Change marker alignment

The marker pointer alignment can be changed by the [`markerAlignment`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/markerAlignment.html) property of [`LinearShapePointer`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer-class.html).The available marker pointer alignments are `start`, `end`, and `center`.

{% highlight dart %} 

 @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(axisTrackExtent: 30, markerPointers: [
            LinearShapePointer(
                value: 0, markerAlignment: LinearMarkerAlignment.start)
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change shape pointer alignment](images/shape-pointer/shape_marker_alignment.png)

## Change the position

By default, the shape pointer is positioned `outside` to the axis. This position can be changed by the [`position`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/position.html) property of a [`LinearShapePointer`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer-class.html). It is possible to position the shape pointer `inside`, `cross`, and `outside` the axis. The below code snippet demonstrates changing the shape pointer position to inside the axis.  

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearShapePointer(
                value: 55,
                shapeType: LinearShapePointerType.triangle,
                position: LinearElementPosition.inside)
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change shape pointer position](images/shape-pointer/shape_pointer_position.png)

## Change the offset

In addition to position the shape pointer, it is also possible to change the offset of the shape pointer. The [`offset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/offset.html) is the distance from the axis. The [`offset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/offset.html) cannot be negative and the cross positioned elements will not get affected by the [`offset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/offset.html) value. The below code snippet demonstrates changing the [`offset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearShapePointer/offset.html) value of the shape pointer. 

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
                position: LinearElementPosition.inside)
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Customize linear gauge bar pointer offset](images/shape-pointer/shape_pointer_offset.png)
