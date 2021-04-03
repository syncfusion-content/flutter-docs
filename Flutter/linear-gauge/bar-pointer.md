---
layout: post
title: Customize bar pointer in linear gauge|Linear Gauge widget| Syncfusion
description: Detailed tutorial about the bar pointer on Linear Gauge Flutter widget.| Flutter Linear Gauge widget|
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Linear Gauge bar pointer

A bar pointer is an accenting line or shaded background that can be placed on a linear gauge to mark any current value in the axis track. The bar pointers always starts from the minimum value of the axis and ends in the specified value. So the [`value`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/value.html) property is a required parameter for creating a bar pointer.

## Default Linear Gauge bar pointer

The code snippet creates a default bar pointer with the value 50. 

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            barPointers: [
              LinearBarPointer(
                value: 50
              )
            ],
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Initialize linear gauge for bar pointer](images/bar-pointer/default_bar_pointer.png)

## Change the bar pointer thickness

The thickness can be changed by the [`thickness`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/thickness.html) property of the bar pointer. The below code snippet demonstrates the same. 

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            barPointers: [
              LinearBarPointer(
                value: 50,
                thickness: 10
              )
            ],
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change the bar pointer thickness](images/bar-pointer/bar_thickness.png)

## Change the edge style

The edge style can be changed with the [`edgeStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/edgeStyle.html) property of bar pointer. The edge style can be any of the `startCurve`, `endCurve`, `bothCurve`, and `bothFlat` options.The default value is `bothFlat`.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            barPointers: [
              LinearBarPointer(
                value: 50,
                // Changed the thickness to make the curve visible
                thickness: 10,
                //Updated the edge style as curve at end position
                edgeStyle: LinearEdgeStyle.endCurve
              )
            ],
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Change the bar pointer edge style](images/bar-pointer/edge_style.png)

## Change the position

By default, the bar pointer is positioned cross to the axis. This position can be changed by the [`position`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/position.html) property of a bar pointer. It is possible to position the bar pointer 'inside', 'cross', and 'outside' the axis. The below code snippet demonstrates changing the bar pointer position to inside the axis. 

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            barPointers: [
              LinearBarPointer(
                value: 50,
                position: LinearElementPosition.inside
              )
            ],
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Customize linear gauge for bar pointer position](images/bar-pointer/bar_pointer_change_position.png)

## Change the offset

In addition to position the bar pointer, it is also possible to change the offset of the bar pointer. The [`offset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/offset.html) is the distance from the axis. The [`offset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/offset.html) cannot be negative and the cross positioned elements will not get affected by the [`offset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/offset.html) value. The below code snippet demonstrates changing the offset value of the bar pointer. 

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            barPointers: [
              LinearBarPointer(
                value: 50,
                position: LinearElementPosition.outside,
                offset: 5
              )
            ],
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Customize linear gauge bar pointer offset](images/bar-pointer/bar_pointer_offset.png)

## Apply color to bar pointer

The color of the bar pointer can be changed by the [`color`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/color.html) property. The below code snippet demonstrates the same. 

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            barPointers: [
              LinearBarPointer(
                value: 50,
                //Change the color
                color: Colors.redAccent
              )
            ],
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Apply color to bar pointer](images/bar-pointer/bar_color.png)

## Apply radial gradient

The gradient can be applied by using the [`shaderCallback`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/shaderCallback.html) property of bar pointer. The below code snippet demonstrates applying a radial gradient to the bar pointer.

{% highlight dart %} 

   @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            barPointers: [
              LinearBarPointer(
                  value: 100,
                  //Apply radial gradient
                  shaderCallback: (bounds) => RadialGradient(
                        radius: 30,
                        colors: [
                          Colors.redAccent,
                          Colors.blueAccent,
                          Colors.greenAccent,
                        ],
                      ).createShader(bounds))
            ],
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Apply radial gradient to bar pointer](images/bar-pointer/radial_gradient_bar.png)

## Apply linear gradient

The gradient can be applied by using the [`shaderCallback`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/shaderCallback.html) property of bar pointer. The below code snippet demonstrates applying a linear gradient to the bar pointer.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            barPointers: [
              LinearBarPointer(
                value: 100,
                thickness: 10,
                //Apply linear gradient
                shaderCallback: (bounds) => LinearGradient(
                        begin: Alignment.centerLeft,
                        end: Alignment.centerRight,
                        colors: [Colors.redAccent, Colors.blueAccent])
                    .createShader(bounds)
              ),
            ],
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Apply linear gradient to bar pointer](images/bar-pointer/linear_gradient_bar.png)

## Apply sweep gradient

The gradient can be applied by using the [`shaderCallback`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/shaderCallback.html) property of bar pointer. The below code snippet demonstrates applying a sweep gradient to the bar pointer.

{% highlight dart %} 

   @override
  Widget build(BuildContext context) {
    return MaterialApp(
      color: Colors.white,
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            barPointers: [
              LinearBarPointer(
                  value: 100,
                  thickness: 10,
                  //Apply linear gradient
                  shaderCallback: (bounds) => SweepGradient(
                  startAngle: 0.1,
                  endAngle: 0.2,
                  colors: [
                    Colors.blueAccent,
                    Colors.greenAccent,
                    Colors.orangeAccent,
                  ],
                  tileMode: TileMode.mirror,
                  center: Alignment.bottomRight,
                ).createShader(bounds))
            ],
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Apply sweep gradient to bar pointer](images/bar-pointer/sweep_gradient_bar.png)


## Customize the border

The border can be customized with [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/borderWidth.html) and [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/LinearBarPointer/borderColor.html) properties of bar pointer. The below code examples demonstrates the same.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: SfLinearGauge(
            barPointers: [
              LinearBarPointer(
                  value: 80,
                  thickness: 10,
                  borderWidth: 3,
                  borderColor: Colors.cyanAccent)
            ],
          ),
        ),
      ),
    );
  }
  
{% endhighlight %}

![Customize linear gauge bar pointer border](images/bar-pointer/bar_border.png)