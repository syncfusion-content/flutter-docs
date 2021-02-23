---
layout: post
title: Zooming and Panning in Syncfusion Flutter Charts
description: Learn how to enable zooming and panning and its features available in the Syncfusion Flutter Charts widget.
platform: flutter
control: Chart
documentation: ug
---

# Zooming and Panning in Cartesian charts


## Pinch zooming

Pinch zooming can be enabled by [`enablePinching`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/enablePinching.html) property and defaults to *false*. Pinching can be performed by moving two fingers over the chart.

{% highlight dart %} 

    ZoomPanBehavior _zoomPanBehavior;
    
    @override
    void initState(){
     _zoomPanBehavior = ZoomPanBehavior(
                  // Enables pinch zooming
                  enablePinching: true
                );
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              height: 300, 
              width: 350, 
              child: SfCartesianChart(
                zoomPanBehavior: _zoomPanBehavior
              )
            )
          )
        )
      );
    }

{% endhighlight %}

## Double tap zooming

Double tap zooming can be enabled using [`enableDoubleTapZooming`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/enableDoubleTapZooming.html) property. Defaults to *false*.

{% highlight dart %} 
    
    ZoomPanBehavior _zoomPanBehavior;
    
    @override
    void initState(){
     _zoomPanBehavior = ZoomPanBehavior(
                  // Performs zooming on double tap
                  enableDoubleTapZooming: true
                );
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              height: 300, 
              width: 350, 
              child: SfCartesianChart(
                zoomPanBehavior: _zoomPanBehavior
              )
            )
          )
        )
      );
    }

{% endhighlight %}

## Selection zooming

By specifying [`enableSelectionZooming`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/enableSelectionZooming.html) property to true, you can long press and drag to select a range on the chart to be zoomed in.

**Selection rectangle customization**

You can customize the selection rectangle using the below properties.

* [`selectionRectBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/selectionRectBorderWidth.html) - used to change the stroke width of the selection rectangle.
* [`selectionRectBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/selectionRectBorderColor.html) - used to change the stroke color of the selection rectangle.
* [`selectionRectColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/selectionRectColor.html) - used to change the background color of the selection rectangle.

{% highlight dart %} 
    
    ZoomPanBehavior _zoomPanBehavior;
    
    @override
    void initState(){
     _zoomPanBehavior = ZoomPanBehavior(
                  enableSelectionZooming: true,
                  selectionRectBorderColor: Colors.red,
                  selectionRectBorderWidth: 1,
                  selectionRectColor: Colors.grey
                );
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              height: 300, 
              width: 350, 
              child: SfCartesianChart(
                zoomPanBehavior: _zoomPanBehavior
              )
            )
          )
        )
      );
    }

{% endhighlight %}

![Selection Zooming](images/zooming-panning/before_zooming.jpg)

Following screenshot shows the zoomed area

![Selection Zooming](images/zooming-panning/after_zooming.jpg)

**Show axis tooltip**

The axis tooltip on selection zooming can be enabled using [`enable`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/enable.html) property of [`crosshairTooltip`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/crosshairTooltip.html). You can customize the appearance of axis tooltip using the following properties.

* [`enable`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/InteractiveTooltip/enable.html) - used to enable the axis tooltip.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/InteractiveTooltip/borderWidth.html) - used to change the stroke width of the axis tooltip.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/InteractiveTooltip/borderColor.html) - used to change the stroke color of the axis tooltip.
* [`format`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/InteractiveTooltip/format.html) - by default, axis value will be displayed in the tooltip, and it can be customized by adding desired text as prefix or suffix.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/InteractiveTooltip/textStyle.html) - used to change the text color, size, font family, fontStyle, and font weight.
* [`textStyle.color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/color.html) - used to change the color of the text.
* [`textStyle.fontFamily`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontFamily.html) - used to change the font family for chart title. 
* [`textStyle.fontStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontStyle.html) - used to change the font style for the chart title.
* [`textStyle.fontSize`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontStyle.html) - used to change the font size for the chart title.

{% highlight dart %} 
    ZoomPanBehavior _zoomPanBehavior;
    
    @override
    void initState(){
     _zoomPanBehavior = ZoomPanBehavior(
                  enableDoubleTapZooming: true,
                  enablePinching: true,
                  // Enables the selection zooming
                  enableSelectionZooming: true
                );
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              child: SfCartesianChart(
                primaryXAxis: NumericAxis(
                  crosshairTooltip: InteractiveTooltip(
                  // Displays the axis tooltip
                  enable: true,
                  borderColor: Colors.red,
                  borderWidth: 2
                )
              ),
                primaryYAxis: NumericAxis(
                  crosshairTooltip: InteractiveTooltip(
                  enable: true,
                  borderColor: Colors.red,
                  borderWidth: 2
                )
              ),
                zoomPanBehavior: _zoomPanBehavior
              )
            )
          )
        )
      );
    }

{% endhighlight %}

## Auto interval on zooming

The [`enableAutoIntervalOnZooming`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/enableAutoIntervalOnZooming.html) property determines the update of axis internal based on the current visible range while zooming the chart. Default value of this property is true. If this property is false, the nice internal will not be calculated for new range after zoom in and actual interval will be sustained.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              child: SfCartesianChart(
                primaryXAxis: DateTimeAxis(
                  // Intervals will be fixed, not calculated automatically based on the visible range on zooming
                  enableAutoIntervalOnZooming: false
                )
              )
            )
          );
        }

{% endhighlight %}

## Maximum zoom level

The [`maximumZoomLevel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/maximumZoomLevel.html) property defines the maximum zooming level. Zooming will be stopped after reaching this value. This defaults to null.

{% highlight dart %} 
    ZoomPanBehavior _zoomPanBehavior;
    
    @override
    void initState(){
     _zoomPanBehavior = ZoomPanBehavior(
                  maximumZoomLevel: 3);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              child: SfCartesianChart(
                zoomPanBehavior: _zoomPanBehavior
              )
            )
          )
        )
      );
    }

{% endhighlight %}

## Panning 

Panning can be performed on a zoomed axis. You can pan the zoomed chart with [`enablePanning`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/enablePanning.html) property. Defaults to `false`.

If zoom mode is set to [`zoomMode.x`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomMode-class.html) means you can only pan to the  horizontal direction, in case the [`zoomMode.y`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomMode-class.html) means you can pan only to the  vertical direction and [`zoomMode.xy`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomMode-class.html) means you can pan to both horizontal and vertical directions on the chart.

{% highlight dart %} 
    
    ZoomPanBehavior _zoomPanBehavior;
    
    @override
    void initState(){
     _zoomPanBehavior = ZoomPanBehavior(
                    enablePinching: true,
                    zoomMode: zoomMode.x,
                    enablePanning: true,
                );
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              child: SfCartesianChart(
                zoomPanBehavior: _zoomPanBehavior
              )
            )
          )
        )
      );
    }

{% endhighlight %}

![Panning](images/zooming-panning/panning.gif)

Also refer [zooming](./events#onzooming), [zoom start](./events#onzoomstart) and [zoom end](./events#onzoomend) events for customizing the zooming further.

## See Also

* [To Synchronize panning in multiple charts](https://www.syncfusion.com/kb/11533/how-to-synchronize-panning-in-multiple-charts-sfcartesianchart).