---
layout: post
title: Customize marker pointers in a linear gauge | Syncfusion
description: Detailed tutorial about the marker pointers on Linear Gauge Flutter widget | Flutter Linear Gauge widget|
platform: flutter
control: Overview
documentation: ug
---

# Linear Gauge Shape Marker Pointers

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

![Initialize linear gauge for shape pointer](images/shape-pointer/default_shape_pointer.png)

## Change the size

The size of the marker pointer can be changed by the 'height' and 'width' properties of 'LinearShapePointer'. The below code snippet demonstrates changing the size of a shape pointer.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearShapePointer(
              value: 50,
              height: 25,
              width: 25,
            ),
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Initialize linear gauge for shape pointer](images/shape-pointer/shape_pointer_size.png)

## Change the color

The color of the shape pointer can be changed by the 'color' property. The below code example demonstrates the same.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearShapePointer(
              value: 50,
              color: Colors.redAccent,
            ),
          ]),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change shape pointer color](images/shape-pointer/shape_pointer_color.png)

## Customize the border

The border can be customized by the 'borderColor' and 'borderWidth' of the 'LinearShapePointer'.

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(markerPointers: [
            LinearShapePointer(
              value: 50,
              borderColor: Colors.redAccent,
              borderWidth: 2,
            ),
          ]),
        ),
      ),
    );
  }

![Change shape pointer border](images/shape-pointer/shape_border.png)

## Customize the elevation

The elevation can be customized by the 'elevation' and 'elevationColor' properties.

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
                elevationColor: Colors.blueGrey,
              ),
            ]),
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change shape pointer elevation](images/shape-pointer/pointer_elevation.png)



