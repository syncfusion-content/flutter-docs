---
layout: post
title: Tooltip in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about Tooltip feature of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Tooltip in Flutter Cartesian Charts (SfCartesianChart)

Chart provides tooltip support for all the series. It is used to show information about the segment when you tap on the segment. To enable the tooltip, you can set the [`enable`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/enable.html) property of [`tooltipBehavior`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior-class.html) to *true*. By default, the tooltip is set to *false*. You need to set [`enableTooltip`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/enableTooltip.html) property to *true* to enable tooltip for a particular series alone.

The tooltip state will be preserved on the device's orientation change and on browser resize. For example, if the tooltip's [`duration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/duration.html) is set to 10,000ms, and when you change the orientation of your device from portrait to landscape after 5,000ms of tooltip display, the tooltip will be displayed for the next 5,000ms in landscape mode before disappearing.

{% tabs %}
{% highlight dart hl_lines="5 16 20" %}
    
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState() {
      _tooltipBehavior = TooltipBehavior(enable: true);
      super.initState();
    }
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: Container(
            child: SfCartesianChart(
              primaryXAxis: CategoryAxis(),
              //Enables the tooltip for all the series
              tooltipBehavior: _tooltipBehavior,
              series: <CartesianSeries>[
                LineSeries<ChartData, String>(
                  //Enables the tooltip for individual series
                  enableTooltip: true, 
                )
              ]
            )
          )
        )
      );
    }

    class ChartData {
        ChartData(this.x, this.y);
        final String x;
        final double? y;
      }

{% endhighlight %}
{% endtabs %}

![Tooltip](images/tooltip/default_tooltip.jpg)

#### See Also

* [Activate chart tooltip after the chart got rendered](https://support.syncfusion.com/kb/article/10627/how-to-activate-chart-tooltip-initially-after-the-chart-widget-got-rendered).

## Customizing the appearance

You can use the following properties to customize the tooltip appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/color.html) - used to change the background color of tooltip.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/borderWidth.html) - used to change the stroke width of the tooltip.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/borderColor.html) - used to change the stroke color of the tooltip.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/opacity.html) - used to control the transparency of the tooltip.
* [`duration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/duration.html) - specifies the duration for displaying the tooltip that defaults to `3000`.
* [`animationDuration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/animationDuration.html) - specifies the duration for animating the tooltip that defaults to 350.
* [`elevation`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/elevation.html) - specifies the elevation of tooltip.
* [`canShowMarker`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/canShowMarker.html) - toggles the visibility of the marker in the tooltip.
* [`header`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/header.html) - specifies the header for tooltip. By default, the series name will be displayed in the header.
* [`format`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/format.html) - formats the tooltip text. By default, the tooltip will be rendered with x and y-values. You can add prefix or suffix to x, y, and series name values in the tooltip by formatting them.
* [`shadowColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/shadowColor.html) - specifies the color of the tooltip shadow.
* [`shouldAlwaysShow`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/shouldAlwaysShow.html) - shows or hides the tooltip. By default, the tooltip will be hidden on touch. To avoid this, set this property to true.
* [`textAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/textAlignment.html) - alignment of the text in the tooltip.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/textStyle.html) - customizes the tooltip text.
* [`shared`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/shared.html) - share the tooltip with same index points.

{% tabs %}
{% highlight dart %} 
    
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState() {
      _tooltipBehavior = TooltipBehavior(
                  enable: true,
                  borderColor: Colors.red,
                  borderWidth: 5,
                  color: Colors.lightBlue
                );
      super.initState();
    }
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: Container(
            child: SfCartesianChart(
              primaryXAxis: CategoryAxis(),
              tooltipBehavior: _tooltipBehavior,
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

![Customized tooltip](images/tooltip/customized_tooltip.jpg)

## Label format

By default, x and y value will be displayed in the tooltip, and it can be customized using [`format`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/format.html) property as depicted in the below code snippet. You can show the below values in the tooltip. Also, you can add prefix or suffix to these values.

* X value - `point.x`
* Y value - `point.y`
* Bubble size - `point.size`
* Name of the series - `series.name`
* Stores the cumulative value for stacked series - `point.cumulative `

{% tabs %}
{% highlight dart hl_lines="8" %}     

    late TooltipBehavior _tooltipBehavior;

    @override
    void initState() {
      _tooltipBehavior = TooltipBehavior(
                  enable: true, 
                  // Formatting the tooltip text
                  format: 'point.y%'
                );
      super.initState();
    }
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: Container(
            child: SfCartesianChart(
              tooltipBehavior: _tooltipBehavior,
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

## Tooltip positioning

The tooltip can be made to display in the fixed location or at the pointer location itself using the [`tooltipPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/tooltipPosition.html) property. This defaults to [`TooltipPosition.auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipPosition.html#auto).

{% tabs %}
{% highlight dart hl_lines="7" %}  

    late TooltipBehavior _tooltipBehavior;

    @override
    void initState() {
    _tooltipBehavior = TooltipBehavior(
                enable: true, 
                tooltipPosition: TooltipPosition.pointer
              );
    super.initState();
    } 
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: Container(
            child: SfCartesianChart(
               primaryXAxis: CategoryAxis(),
              tooltipBehavior: _tooltipBehavior,
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

![pointer tooltip](images/tooltip/tooltip_pointer.png)

## Tooltip template

You can customize the appearance of the tooltip with your own widget by using the [`builder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/builder.html) property of [`tooltipBehavior`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/tooltipBehavior.html).

{% tabs %}
{% highlight dart %} 
    
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState() {
    _tooltipBehavior = TooltipBehavior(
                enable: true,
                // Templating the tooltip
                builder: (dynamic data, dynamic point, dynamic series,
                int pointIndex, int seriesIndex) {
                  return Container(
                    child: Text(
                      'PointIndex : ${pointIndex.toString()}'
                    )
                  );
                }
              );
    super.initState();
    } 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: Container(
            child: SfCartesianChart(
              primaryXAxis: CategoryAxis(),
              tooltipBehavior: _tooltipBehavior,
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

![Tooltip template](images/tooltip/tooltip_template.jpg)

## Activation mode

The [`activationMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/activationMode.html) property is used to restrict the visibility of tooltip based on the touch actions. The default value of this property is [`ActivationMode.singleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html#singleTap).

The ActivationMode enum contains the following values:

* [`ActivationMode.longPress`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html#longPress) - Activates tooltip only when performing the long press action.
* [`ActivationMode.singleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html#singleTap) - Activates tooltip only when performing single tap action.
* [`ActivationMode.doubleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html#doubleTap) - Activates tooltip only when performing double tap action.
* [`ActivationMode.none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html#none) - Hides the visibility of tooltip when setting activation mode to none.

{% tabs %}
{% highlight dart hl_lines="8" %}   
    
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState() {
    _tooltipBehavior = TooltipBehavior(
                enable: true,
                // Tooltip will be displayed on long press
                activationMode: ActivationMode.longPress
              );
    super.initState();
    } 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: Container(
            child: SfCartesianChart(
              tooltipBehavior: _tooltipBehavior,
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

Also refer [`tooltip event`](./callbacks#ontooltiprender) for customizing the tooltip further.
