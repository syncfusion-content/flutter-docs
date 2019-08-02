---
layout: post
title: Syncfusion Flutter Chart Trackball and Crosshair
description: How to enable and customize the trackball and corsshair behavior in Essential Flutter Chart
platform: flutter
control: Chart
documentation: ug
---

# Trackball and Crosshair

## Trackball

Trackball feature displays the tooltip for the data points that are closer to the point where you touch on the chart area. This feature, especially, can be used instead of data label feature when you cannot show data labels for all data points due to space constraint. This feature can be enabled using [`enable`]() property of [`trackballBehavior`](). Trackball will be activated once you long-press anywhere on the chart area. Once it is activated, it will appear in the UI and move based on your touch movement until you stop touching on the chart.

You can use the following properties to customize the appearance of trakball tooltip.

* [`lineType`]() - specifies the type of trackball line. By default, vertical line will be displayed.
* [`lineColor`]() - specifies the color of the trackball line.
* [`lineWidth`]() - specifies the stroke width of the trackball line.
* [`lineDashArray`]()- used to render trackball line with dashes.
* [`shouldAlwaysShow`]() - used to show the trackball even after the touch end.
* [`tooltipSettings.borderWidth`]() – used to change the stroke width of the axis tooltip.
* [`tooltipSettings.borderColor`]() – used to change the stroke color of the axis tooltip.
* [`tooltipSettings.arrowLength`]() - specifies the length of the tooltip arrow.
* [`tooltipSettings.arrowWidth`]() - specifies the width of the tooltip arrow.
* [`tooltipSettings.format`]() - by default, axis value will be displayed in the tooltip, and it can be customized by adding desired text as prefix or suffix.
* [`tooltipSettings.textStyle`]() – used to change the text color, size, font family, fontStyle, and font weight.
* [`tooltipSettings.textStyle.color`]() – used to change the color of the tooltip text.
* [`tooltipSettings.textStyle.fontFamily`]() - used to change the font family for tooltip text.
* [`tooltipSettings.textStyle.fontStyle`]() – used to change the font style for tooltip text.
* [`tooltipSettings.textStyle.fontSize`]() - used to change the font size for tooltip text.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          child: SfCartesianChart(
            trackballBehavior: TrackballBehavior(
                enable: true,
                tooltipSettings: InteractiveTooltip(
                  enable: true,
                  color: Colors.red,
                )
            )
          )
        ),
      )),
    );
  }

{% endhighlight %}

### Label display mode

The [`tooltipDisplayMode`]() property is used to specify whether to display label for all the data points along the vertical line or display only single label. Following are the options you can set to this property,

* [`floatAllPoints`]() – Displays label for all the data points along the vertical line.
* [`nearestPoint`]() – Displays label for single data point that is nearer to the touch contact position.
* [`groupAllPoints`]() – Displays label for all the data points grouped and positioned at the top of the chart area.
* [`none`]() - Doesn't display the label.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          child: SfCartesianChart(
            trackballBehavior: TrackballBehavior(
                enable: true,
                tooltipDisplayMode: TrackballDisplayMode.floatAllPoints
            )
          )
        ),
      )),
    );
  }

{% endhighlight %}

### Label alignment

The position of trackball tooltip can be changed using the [`tooltipAlignment`]() property of [`trackballBehavior`](). The following options are available in [`tooltipAlignment`]().

* [`near`]() - aligns the trackball tooltip to the top position of plot area.
* [`far`]() - aligns the trackball tooltip to the bottom position of plot area.
* [`center`]() - aligns the trackball tooltip to the center position of plot area. 

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          child: SfCartesianChart(
            trackballBehavior: TrackballBehavior(
                enable: true,
                tooltipAlignment: ChartAlignment.near,
                tooltipDisplayMode: TrackballDisplayMode.groupAllPoints
            )
          )
        ),
      )),
    );
  }

{% endhighlight %}

N> This is applicable only when the [`tooltipDisplayMode`]() is set to [`groupAllPoints`]().

### Label format

By default, axis value will be displayed in the tooltip, and it can be customized using [`format`]() property by adding desired text as prefix or suffix.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          child: SfCartesianChart(
            trackballBehavior: TrackballBehavior(
                    enable: true,
                    tooltipSettings: InteractiveTooltip(
                      format: 'point.x %')
                )
          )
        ),
      )),
    );
  }

{% endhighlight %}

###	Activation mode

The [`activationMode`]() property is used to restrict the visibility of trackball based on the touch actions. The default value of this property is [`ActivationMode.longPress`]().

The ActivationMode enum contains the following values:

* [`longPress`]() – Activates trackball only when performing the long press action.
* [`singleTap`]() – Activates trackball only when performing single tap action.
* [`doubleTap`]() - Activates trackball only when performing doule tap action.
* [`none`]() – Hides the visibility of trackball when setting activation mode to none. It will be activated when calling the [`show`]() method.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          child: SfCartesianChart(
            trackballBehavior: TrackballBehavior(
                    enable: true,
                    activationMode: ActivationMode.singleTap
                )
          )
        ),
      )),
    );
  }

{% endhighlight %}

## Crosshair

Crosshair has a vertical and horizontal line to view the value of the axis. 

Crosshair lines can be enabled by using [`enable`]() property in the [`crosshairBehavior`](). Likewise tooltip label for an axis can be enabled by using [`enable`] property of [`crosshairTooltip`]() in the corresponding axis.

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
                  enable: true
                )),
              crosshairBehavior: CrosshairBehavior(
                  enable: true
              )
          )
        ),
      )),
    );
  }

{% endhighlight %}

**Track line customization**

The appearance of the track line of crosshair can be customized using the following properties.

* [`lineType`]() - specifies the type of crosshair line.
* [`lineColor`]() - specifies the color of the crosshair line.
* [`lineWidth`]() - specifies the stroke width of the crosshair line.
* [`lineDashArray`]() - used to render crosshair line with dashes.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          child: SfCartesianChart(
              crosshairBehavior: CrosshairBehavior(
                  enable: true,
                  lineColor: Colors.red,
                  lineDashArray: <double>[5,5],
                  lineWidth: 2,
                  lineType: CrosshairLineType.horizontal
                ),
          )
        ),
      )),
    );
  }

{% endhighlight %}

**Show axis tooltip**

The axis tooltip can be enabled using [`enable`]() property of [`crosshairTooltip`](). You can cusotmize the appearance of axis tooltip using the following properties.

* [`enable`]() - used to enable the axis toolip.
* [`borderWidth`]() – used to change the stroke width of the axis tooltip.
* [`borderColor`]() – used to change the stroke color of the axis tooltip.
* [`format`]() - by default, axis value will be displayed in the tooltip, and it can be customized by adding desired text as prefix or suffix.
* [`textStyle`]() – used to change the text color, size, font family, fontStyle, and font weight.
* [`textStyle.color`]() – used to change the color of the text.
* [`textStyle.fontFamily`]() - used to change the font family for chart title. 
* [`textStyle.fontStyle`]() – used to change the font style for the chart title.
* [`textStyle.fontSize`]() - used to change the font size for the chart title.

**Activation mode**

The [`activationMode`]() property is used to restrict the visibility of trackball based on the touch actions. The default value of this property is [`ActivationMode.longPress`]().

The ActivationMode enum contains the following values:

* [`longPress`]() – Activates crosshair only when performing the long press action.
* [`singleTap`]() – Activates crosshair only when performing single tap action.
* [`doubleTap`]() - Activates crosshair only when performing doule tap action.
* [`none`]() – Hides the visibility of crosshair when setting activation mode to none. It will be activated when calling the [`show`]() method.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
          child: Center(
        child: Container(
          child: SfCartesianChart(
            crosshairBehavior: CrosshairBehavior(
                  enable: true,
                  activationMode: ActivationMode.singleTap
                ),
          )
        ),
      )),
    );
  }

{% endhighlight %}
