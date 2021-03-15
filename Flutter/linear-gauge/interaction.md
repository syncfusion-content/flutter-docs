---
layout: post
title: Interaction in linear gauge | Linear Gauge widget| Syncfusion
description: Tutorial about deatils of the interaction on Linear Gauge Flutter widget | Flutter Linear Gauge widget documentation|
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Flutter Linear Gauge Interaction

The shape and widget marker pointers in a Linear Gauge can be moved from one value to another with swipe or drag gestures.

## Interaction with marker pointer

The `onValueChanged` call back is used to change the value of the marker pointer.

The below code snippet demonstrates updating the marker pointer value based on swipe or drag gesture.

{% highlight dart %}

class _InteractionDemoState extends State<MyHomePage> {
  //Pointer value for shape pointer
  double shapePointerValue = 80;

  //Pointer value for widget pointer
  double widgetPointerValue = 40;

  @override
  Widget build(BuildContext context) {
    //Adds linear gauge widget
    return SfLinearGauge(
      markerPointers: [
        //Adds a shape marker pointer
        LinearShapePointer(
          //Assign the pointer value to the shape pointer
          value: shapePointerValue,
          onValueChanged: (value) {
            setState(() {
              //Update the pointer value inside state
              shapePointerValue = value;
            });
          },
          color: Colors.blue[800],
        ),

        // Adds a widget marker pointer
        LinearWidgetPointer(
          //Assign the pointer value to the widget pointer
          value: widgetPointerValue,
          onValueChanged: (value) {
            setState(() {
              //Update the pointer value inside state
              widgetPointerValue = value;
            });
          },
          child: Container(
            height: 20,
            width: 20,
            decoration: BoxDecoration(
                color: Colors.orange[500], shape: BoxShape.circle),
          ),
        ),
      ],
    );
  }
}

{% endhighlight %}

![shape pointer in linear gauge](images/getting-started/add_shape_pointer.png)