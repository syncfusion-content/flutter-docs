---
layout: post
title: Syncfusion Flutter Chart Tooltip
description: How to enable and customize the tooltip in Essential Flutter Chart
platform: flutter
control: Chart
documentation: ug
---

# Tooltip

Chart provides tooltip support for all series. It is used to show information about the segment, when you tap on the segment. To enable the tooltip, you need to set [`enableTooltip`] property as *true*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(

              //Enables the tooltip for all the series
              tooltipBehavior: TooltipBehavior(
                enable: true
              ),
          series: <CartesianSeries>[
            LineSeries<ChartData, double>(

              //Enables the tooltip for individual series
              enableTooltip: true,
              
            )
          ],
        )
            )
        ));
    }

{% endhighlight %}

## Customizing the appearance

You can use the following properties to customize the tooltip appearance.

* [`color`]() – used to change the background color of tooltip.
* [`borderWidth`]() – used to change the stroke width of the tooltip.
* [`borderColor`]() – used to change the stroke color of the tooltip.
* [`opacity`]() - used to control the transparency of the tooltip.
* [`duration`]() - specifies the duration for displaying the tooltip that defualts to 3000.
* [`animationDuration`]() - specifies the duration for animating the tooltip that default to 350.
* [`elevation`] - specifies the elevation of tooltip.
* [`canShowMarker`] - toggles the visibility of the marker in the tooltip.
* [`header`] - specifies the header for tooltip. By default, the series name will be displayed in the header.
* ['format'] - formats the tooltip text. By default, the tooltip will be rendered with x and y-values. You can add prefix or suffix to x, y, and series name values in the tooltip by formatting them.
* [`shadowColor`]() - specifes the color of the tooltip shadow.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
              tooltipBehavior: TooltipBehavior(
                enable: true,
                borderColor: Colors.red,
                borderWidth: 5,
                color: Colors.lightBlue,
              ),
        ))
        ));
    }

{% endhighlight %}

## Tooltip template

You can customize the appearance of the tooltip with your own widget by using the [`builder`]() property of [`tooltipBehavior`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
              tooltipBehavior: TooltipBehavior(
                enable: true,
               builder: (dynamic data, dynamic point, dynamic series,
                  int pointIndex, int seriesIndex) {
                return Container(
                  child: Text('PointIndex : ${pointIndex.toString()}'),
                );
              }),
        ))
        ));
    }

{% endhighlight %}

##	Activation mode

The [`activationMode`]() property is used to restrict the visibility of tooltip based on the touch actions. The default value of this property is [`ActivationMode.singleTap`]().

The ActivationMode enum contains the following values:

* [`longPress`]() – Activates tooltip only when performing the long press action.
* [`singleTap`]() – Activates tooltip only when performing single tap action.
* [`doubleTap`]() - Activates tooltip only when performing doule tap action.
* [`none`] – Hides the visibility of tooltip when setting activation mode to none.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
              tooltipBehavior: TooltipBehavior(
                enable: true,
                activationMode: ActivationMode.longPress),
        ))
        ));
    }

{% endhighlight %}