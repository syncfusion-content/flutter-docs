---
layout: post
title: Zooming and Panning in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about Zooming and Panning feature of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Zooming and Panning in Flutter Cartesian Charts (SfCartesianChart)


## Pinch zooming

Pinch zooming can be enabled by [`enablePinching`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/enablePinching.html) property and defaults to `false`. Pinching can be performed by moving two fingers over the chart.

{% tabs %}
{% highlight dart hl_lines="7" %}

    late ZoomPanBehavior _zoomPanBehavior;
    
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
{% endtabs %}

## Directional zooming

The directional zooming feature improves the zoom experience by allowing users to zoom in and out in a specific direction (horizontal, vertical, or diagonal) depending on the angle of their pinch or drag gesture. To enable this feature, set the [`enableDirectionalZooming`]() property to `true`, the default value is `false`. The following code sample demonstrates how to enable directional zooming.

{% tabs %}
{% highlight dart hl_lines="7" %}

    late ZoomPanBehavior _zoomPanBehavior;
    
    @override
    void initState(){
      _zoomPanBehavior = ZoomPanBehavior(
                  // Enables directional zooming
                  enableDirectionalZooming: true,
                  enablePinching: true,
                  zoomMode: ZoomMode.xy,
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
{% endtabs %}

>**Note**: 
* Directional zooming functions when both [`enableDirectionalZooming`]() and [`enablePinching`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/enablePinching.html) are set to `true`, and [`zoomMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomMode.html) is set to [`ZoomMode.xy`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomMode.html#xy).
* This feature is intended for touch gestures and is ineffective with a mouse or trackpad.

![Directional Zooming](images/zooming-panning/directional-zooming.gif)

## Double tap zooming

Double tap zooming can be enabled using [`enableDoubleTapZooming`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/enableDoubleTapZooming.html) property. Defaults to `false`.

{% tabs %}
{% highlight dart hl_lines="7" %}
    
    late ZoomPanBehavior _zoomPanBehavior;
    
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
{% endtabs %}

## Selection zooming

By specifying [`enableSelectionZooming`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/enableSelectionZooming.html) property to true, you can long press and drag to select a range on the chart to be zoomed in.

**Selection rectangle customization**

You can customize the selection rectangle using the below properties.

* [`selectionRectBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/selectionRectBorderWidth.html) - used to change the stroke width of the selection rectangle.
* [`selectionRectBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/selectionRectBorderColor.html) - used to change the stroke color of the selection rectangle.
* [`selectionRectColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/selectionRectColor.html) - used to change the background color of the selection rectangle.

{% tabs %}
{% highlight dart hl_lines="6" %}
    
    late ZoomPanBehavior _zoomPanBehavior;
    
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
{% endtabs %}

![Selection Zooming](images/zooming-panning/before_zooming.jpg)

Following screenshot shows the zoomed area

![Selection Zooming](images/zooming-panning/after_zooming.jpg)

**Show axis tooltip**

The axis tooltip on selection zooming can be enabled using [`enable`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/enable.html) property of [`InteractiveTooltip`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/InteractiveTooltip-class.html). You can customize the appearance of axis tooltip using the following properties.

* [`enable`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/InteractiveTooltip/enable.html) - used to enable the axis tooltip.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/InteractiveTooltip/borderWidth.html) - used to change the stroke width of the axis tooltip.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/InteractiveTooltip/borderColor.html) - used to change the stroke color of the axis tooltip.
* [`format`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/InteractiveTooltip/format.html) - by default, axis value will be displayed in the tooltip, and it can be customized by adding desired text as prefix or suffix.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/InteractiveTooltip/textStyle.html) - used to change the text color, size, font family, fontStyle, and font weight.
* [`color`](https://api.flutter.dev/flutter/painting/TextStyle/color.html) - used to change the color of the text.
* [`fontFamily`](https://api.flutter.dev/flutter/painting/TextStyle/fontFamily.html) - used to change the font family for chart title. 
* [`fontStyle`](https://api.flutter.dev/flutter/painting/TextStyle/fontStyle.html) - used to change the font style for the chart title.
* [`fontSize`](https://api.flutter.dev/flutter/painting/TextStyle/fontSize.html) - used to change the font size for the chart title.

{% tabs %}
{% highlight dart %} 

    late ZoomPanBehavior _zoomPanBehavior;
    
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
                  interactiveTooltip: InteractiveTooltip(
                  // Displays the x-axis tooltip
                  enable: true,
                  borderColor: Colors.red,
                  borderWidth: 2
                )
              ),
                primaryYAxis: NumericAxis(
                  interactiveTooltip: InteractiveTooltip(
                  // Displays the y-axis tooltip
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
{% endtabs %}

## Mouse wheel zooming

The [`enableMouseWheelZooming`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/enableMouseWheelZooming.html) can be performed by rolling the mouse wheel up or down. The place where the cursor is hovering gets zoomed in or out according to the mouse wheel rolling up or down.

{% tabs %}
{% highlight dart hl_lines="5" %}

    late ZoomPanBehavior _zoomPanBehavior;
    
    @override
    void initState(){
     _zoomPanBehavior = ZoomPanBehavior(enableMouseWheelZooming : true);
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
{% endtabs %}

## Auto interval on zooming

The [`enableAutoIntervalOnZooming`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/enableAutoIntervalOnZooming.html) property determines the update of axis interval based on the current visible range while zooming and panning the chart. Default value of this property is true. If this property is false, the nice interval will not be calculated for new range after zoom in and actual interval will be sustained.

{% tabs %}
{% highlight dart hl_lines="10" %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              child: SfCartesianChart(
                primaryXAxis: DateTimeAxis(
                  // Intervals will be fixed, not calculated automatically based on the visible range on zooming and panning
                  enableAutoIntervalOnZooming: false
                )
              )
            )
          )
        ) 
      );
    }

{% endhighlight %}
{% endtabs %}

## Maximum zoom level

The [`maximumZoomLevel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/maximumZoomLevel.html) property defines the maximum zooming level. Zooming will be stopped after reaching this value. This defaults to `null`.

{% tabs %}
{% highlight dart hl_lines="5" %} 

    late ZoomPanBehavior _zoomPanBehavior;
    
    @override
    void initState(){
     _zoomPanBehavior = ZoomPanBehavior(maximumZoomLevel: 0.3);
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
{% endtabs %}

## Panning 

Panning can be performed on a zoomed axis. You can pan the zoomed chart with [`enablePanning`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/enablePanning.html) property. Defaults to `false`.

If zoom mode is set to [`zoomMode.x`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomMode.html) means you can only pan to the  horizontal direction, in case the [`zoomMode.y`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomMode.html) means you can pan only to the  vertical direction and [`zoomMode.xy`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomMode.html) means you can pan to both horizontal and vertical directions on the chart.

{% tabs %}
{% highlight dart hl_lines="7" %}  
    
    late ZoomPanBehavior _zoomPanBehavior;
    
    @override
    void initState(){
     _zoomPanBehavior = ZoomPanBehavior(
                    enablePinching: true,
                    zoomMode: ZoomMode.x,
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
{% endtabs %}

![Panning](images/zooming-panning/panning.gif)

Also refer [`zooming`](./callbacks#onzooming), [`zoom start`](./callbacks#onzoomstart) and [`zoom end`](./callbacks#onzoomend) events for customizing the zooming further.

### Calculate range based on visible points

The [`anchorRangeToVisiblePoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/anchorRangeToVisiblePoints.html)  property can be used to calculate the value axis range based on the visible points. When the property is set to false the value axis range will be calculated based on all the data points in the chart irrespective of visible points. For further reference, check this [AutoRangeCalculation](https://help.syncfusion.com/flutter/cartesian-charts/axis-customization#auto-range-calculation) section.

#### See Also

* [To Synchronize panning in multiple charts](https://support.syncfusion.com/kb/article/9939/how-to-synchronize-panning-in-multiple-charts-sfcartesianchart).
