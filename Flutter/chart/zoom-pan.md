---
layout: post
title: Zooming and Panning in Syncfusion Flutter Charts
description: Learn how to enable zooming and panning in Flutter Charts
platform: flutter
control: Chart
documentation: ug
---

# Zooming and Panning

## Pinch zooming

Pinch zooming can be enabled by [`enablePinching`]() property and defaults to *false*. Pinching can be performed by moving two fingers over the chart.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          height: 300, 
          width: 350, 
          child: SfCartesianChart(
            zoomPanBehavior: ZoomPanBehavior(
              enablePinching: true
            ),
            
          )
        ),
      )),
    );
  }

{% endhighlight %}

## Double tap zooming

Double tap zooming can be enabled using [`enableDoubleTapZooming`]() property. Defaults to *false*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          height: 300, 
          width: 350, 
          child: SfCartesianChart(
            zoomPanBehavior: ZoomPanBehavior(
              enableDoubleTapZooming: true,
            ),
            
          )
        ),
      )),
    );
  }

{% endhighlight %}

## Selection zooming

By specifying [`enableSelectionZooming`]() property to true, you can double tap and drag to select a range on the chart to be zoomed in.

**Selection rectangle customization**

You can customize the selection rectangle using the below properties.

* [`selectionRectBorderWidth`]() – used to change the stroke width of the selection rectangle.
* [`selectionRectBorderColor`]() – used to change the stroke color of the selection rectangle.
* [`selectionRectColor`]() - used to change the background color of the selection rectangle.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          height: 300, 
          width: 350, 
          child: SfCartesianChart(
            zoomPanBehavior: ZoomPanBehavior(
              enableSelectionZooming: true,
              selectionRectBorderColor: Colors.red,
              selectionRectBorderWidth: 1,
              selectionRectColor: Colors.grey,
            ),
          )
        ),
      )),
    );
  }

{% endhighlight %}

![Selection Zooming](images/zooming-panning/before_selection.png)

Following screenshot shows the zoomed area

![Selection Zooming](images/zooming-panning/after_selection.png)

**Show axis tooltip**

The axis tooltip on selection zooming can be enabled using [`enable`]() property of [`crosshairTooltip`](). You can customize the appearance of axis tooltip using the following properties.

* [`enable`]() - used to enable the axis tooltip.
* [`borderWidth`]() – used to change the stroke width of the axis tooltip.
* [`borderColor`]() – used to change the stroke color of the axis tooltip.
* [`format`]() - by default, axis value will be displayed in the tooltip, and it can be customized by adding desired text as prefix or suffix.
* [`textStyle`]() – used to change the text color, size, font family, fontStyle, and font weight.
* [`textStyle.color`]() – used to change the color of the text.
* [`textStyle.fontFamily`]() - used to change the font family for chart title. 
* [`textStyle.fontStyle`]() – used to change the font style for the chart title.
* [`textStyle.fontSize`]() - used to change the font size for the chart title.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          child: SfCartesianChart(
            primaryXAxis: NumericAxis(
                    crosshairTooltip: InteractiveTooltip(
                  enable: true,
                  borderColor: Colors.red,
                  borderWidth: 2,
                )),
                primaryYAxis: NumericAxis(
                    crosshairTooltip: InteractiveTooltip(
                  enable: true,
                  borderColor: Colors.red,
                  borderWidth: 2,
                )),
                zoomPanBehavior: ZoomPanBehavior(
                  enableDoubleTapZooming: true,
                  enablePinching: true,
                  enableSelectionZooming: true,
                ),
          )
        ),
      )),
    );
  }

{% endhighlight %}

## Auto interval on zooming

The [`enableAutoIntervalOnZooming`]() property determines the update of axis internal based on the current visible range while zooming the chart. Default value of this property is true. If this property is false, the nice internal will not be calculated for new range after zoom in and actual interval will be sustained.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(
                  enableAutoIntervalOnZooming: false
            ),
      )),
    );
  }

{% endhighlight %}

## Maximum zoom level

The [`maximumZoomLevel`]() property defines the maximum zooming level. Zooming will be stopped after reaching this value. This defaults to null.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          child: SfCartesianChart(
            zoomPanBehavior: ZoomPanBehavior(
                  maximumZoomLevel: 3
            ),
          )
        ),
      )),
    );
  }

{% endhighlight %}