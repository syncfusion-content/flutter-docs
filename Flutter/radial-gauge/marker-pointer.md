---
layout: post
title: Syncfusion Flutter Gauge Pointers
description: This article describes how to add and customizes the appearence of pointers of radial gauge control in flutter platform
platform: flutter
control: SfRadialGauge
documentation: ug
---

# Marker pointer

Different types of markers are used to mark the pointer values in a scale. You can change the marker type using the [`markerType`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/markerType.html) property. 

{% highlight dart %}
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
              child: SfRadialGauge(
                axes: <RadialAxis>[RadialAxis(
                  pointers: <GaugePointer>[MarkerPointer(value: 60)]
                )],
              )
            ),
          );
        }

{% endhighlight %}

![default marker pointer](images/marker-pointers/marker_default.jpg)

Gauge supports the following types of marker:

* Circle
* Diamond
* Image
* Inverted triangle
* Rectangle
* Text
* Triangle

![default marker pointer](images/marker-pointers/markers.png)

## Image pointer

Image is used to denote the current pointer values instead of shape. It can be achieved by specifying the  [`markerType`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/markerType.html) as image and specifying the [`imageUrl`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/imageUrl.html) property of marker pointer.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
              child: SfRadialGauge(
                axes: <RadialAxis>[RadialAxis(
                  pointers: <GaugePointer>[MarkerPointer(value: 60,
                      markerType: MarkerType.image,markerHeight: 30,
                       markerWidth: 30,
                      imageUrl: 'images/pin.png')]
                )],
              )
            ),
          );
        }

{% endhighlight %}

![image pointer](images/marker-pointers/image_marker.jpg)

## Text pointer

Text is used to denote the current pointer value instead of any marker shape. It can be achieved by setting the [`markerType`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/markerType.html)  as text. The provided text can be customized using the [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/textStyle.html) property of marker pointer.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
              child: SfRadialGauge(
                axes: <RadialAxis>[RadialAxis(
                  pointers: <GaugePointer>[MarkerPointer(value: 50,
                      markerType: MarkerType.text, text: 'Average',
                    textStyle: GaugeTextStyle(fontSize: 15,
                     fontWeight: FontWeight.bold,
                        fontStyle: FontStyle.italic)
                  )]
                )],
              )
            ),
          );
        }

{% endhighlight %}

![text pointer](images/marker-pointers/text_marker.jpg)

## Marker Customization

The marker pointer can be customized using the following properties:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/color.html) – Allows to customize the marker color.
* [`markerHeight`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/markerHeight.html) – Allows to specify the marker height.
* [`markerWidth`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/markerWidth.html) – Allows to specify the marker width.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/borderColor.html) – Allows to specify the border color for the marker.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/borderWidth.html) –  Allows to specify the border width of the marker.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
              child: SfRadialGauge(
                axes: <RadialAxis>[RadialAxis(
                  pointers: <GaugePointer>[MarkerPointer(value: 60, 
                  markerHeight: 30, markerWidth: 30,
                      markerType: MarkerType.circle, color: Colors.lightBlue,
                      borderWidth: 3, borderColor: Colors.black)]
                )],
              )
            ),
          );
        }

{% endhighlight %}

![marker pointer customization](images/marker-pointers/marker_customization.jpg)

## Position customization

The marker pointer can be moved near or far from its actual position using the [`markerOffset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/markerOffset.html) and [`offsetUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/offsetUnit.html) properties. 

When you set [`offsetUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/offsetUnit.html) to logical pixel, then the marker pointer will be moved based on the logical pixel value. If you set [`offsetUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/offsetUnit.html) to factor, then provided factor will be multiplied with the axis radius value, and then the pointer will be moved to corresponding value. The default value of [`offsetUnit`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/MarkerPointer/offsetUnit.html) is GaugeSizeUnit.logicalPixel.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
              child: SfRadialGauge(
                axes: <RadialAxis>[RadialAxis( radiusFactor: 0.9, centerY: 0.65,
                  pointers: <GaugePointer>[MarkerPointer(value: 60,
                    markerOffset: -5
                    )
                  ]
                )],
              )
            ),
          );
        }

{% endhighlight %}

![marker offset](images/marker-pointers/marker_offset.jpg)




