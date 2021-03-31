---
layout: post
title: Customize shape pointers in a linear gauge | Syncfusion
description: Detailed tutorial about the shape pointers on Linear Gauge Flutter widget | Flutter Linear Gauge widget|
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Linear Gauge Shape Marker Pointers

The `LinearShapePointer` in `SfLinearGauge` have the below pre-defined shapes to mark a specific value. The default shape pointer is inverted `invertedTriangle`. 

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

The size of the marker pointer can be changed by the `height` and `width` properties of `LinearShapePointer`. The below code snippet demonstrates changing the size of a shape pointer.

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

The color of the shape pointer can be changed by the `color` property. The below code example demonstrates the same.

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

The border can be customized by the `borderColor` and `borderWidth` of the `LinearShapePointer`.

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

The elevation can be customized by the `elevation` and `elevationColor` properties.

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

The marker pointer alignment can be changed by the `markerAlignment` property of `LinearShapePointer`.The available marker pointer alignments are `start`, `end`, and `center`.

{% highlight dart %} 

 @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(axisTrackExtent: 30, markerPointers: [
            LinearShapePointer(
                value: 0, markerAlignment: LinearMarkerAlignment.center)
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change shape pointer alignment](images/shape-pointer/shape_marker_alignment.png)

## Change the position

By default, the shape pointer is positioned `outside` to the axis. This position can be changed by the `position` property of a `LinearShapePointer`. It is possible to position the shape pointer `inside`, `cross`, and `outside` the axis. The below code snippet demonstrates changing the shape pointer position to inside the axis.  

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

In addition to position the shape pointer, it is also possible to change the offset of the shape pointer. The `offset` is the distance from the axis. The `offset` cannot be negative and the cross positioned elements will not get affected by the `offset` value. The below code snippet demonstrates changing the `offset` value of the shape pointer. 

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
