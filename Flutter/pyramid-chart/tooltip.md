---
layout: post
title: Tooltip in Flutter Pyramid Chart widget | Syncfusion 
description: Learn here all about Tooltip feature of Syncfusion Flutter Pyramid Chart (SfPyramidChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Tooltip in Flutter Pyramid Chart (SfPyramidChart)

Chart provides tooltip support for all the series. It is used to show information about the segment, when you tap on the segment. To enable the tooltip, you need to set [`enableTooltip`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/enableTooltip.html) property as `true`.

The tooltip state will be preserved on the device's orientation change and on browser resize. For example, if the tooltip's [`duration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/duration.html) is set to 10,000ms, and when you change the orientation of your device from portrait to landscape after 5,000ms of tooltip display, the tooltip will be displayed for the next 5,000ms in landscape mode before disappearing.

{% tabs %}
{% highlight Dart %} 
    
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
        _tooltipBehavior = TooltipBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = [
        ChartData('Jan', 35),
        ChartData('Feb', 28),
        ChartData('Mar', 38),
        ChartData('Apr', 32),
        ChartData('May', 40)
      ];
      return Scaffold(
        body: Center(
          child: Container(
            child: SfPyramidChart(
              tooltipBehavior: _tooltipBehavior,
              series: PyramidSeries<ChartData, String>(
                  dataSource: chartData,
                  xValueMapper: (ChartData data, _) =>   data.x,
                  yValueMapper: (ChartData data, _) => data.y
                )
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

![Tooltip](images/tooltip/default_tooltip.png)

## Customizing the appearance

You can use the following properties to customize the tooltip appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/color.html) - used to change the background color of tooltip.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/borderWidth.html) - used to change the stroke width of the tooltip.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/borderColor.html) - used to change the stroke color of the tooltip.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/opacity.html) - used to control the transparency of the tooltip.
* [`duration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/duration.html) - specifies the duration for displaying the tooltip that defaults to `3000`.
* [`animationDuration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/animationDuration.html) - specifies the duration for animating the tooltip that default to `350`.
* [`elevation`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/elevation.html) - specifies the elevation of tooltip.
* [`canShowMarker`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/canShowMarker.html) - toggles the visibility of the marker in the tooltip.
* [`header`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/header.html) - specifies the header for tooltip. By default, the series name will be displayed in the header.
* [`format`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/format.html) - formats the tooltip text. By default, the tooltip will be rendered with x and y-values. You can add prefix or suffix to x, y, and series name values in the tooltip by formatting them.
* [`shadowColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/shadowColor.html) - specifies the color of the tooltip shadow.
* [`shouldAlwaysShow`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/shouldAlwaysShow.html) - used to shows or hides the tooltip.
* [`textAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/textAlignment.html) - alignment of the text in the tooltip.
* [`decimalPlaces`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/decimalPlaces.html) - used to specify the number decimals to be displayed in tooltip text.
* [`shared`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/shared.html) - used to share the tooltip with same index points.


{% tabs %}
{% highlight Dart %} 
    
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
        _tooltipBehavior = TooltipBehavior(
                enable: true,
                borderColor: Colors.red,
                borderWidth: 2,
                color: Colors.lightBlue
              );
        super.initState();
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: Container(
            height: 350,
            width: 350,
            child: SfPyramidChart(
              tooltipBehavior: _tooltipBehavior,
              series: PyramidSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y)
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

![Customized tooltip](images/tooltip/customized_tooltip.png)

## Label format

By default, x and y value will be displayed in the tooltip, and it can be customized using [`format`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/format.html) property as depicted in the below code snippet. You can show the below values in the tooltip. Also you can add prefix or suffix to these values.

* X value - `point.x`
* Y value - `point.y`
* Name of the series - `series.name`

{% tabs %}
{% highlight Dart %} 
    
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
        _tooltipBehavior =  TooltipBehavior(
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
            child: SfPyramidChart(
              tooltipBehavior: _tooltipBehavior,
              series: PyramidSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y)
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

![tooltip format](images/tooltip/tooltip_format.png)

## Tooltip positioning

The tooltip can be made to display in the fixed location or at the pointer location itself using the [`tooltipPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/tooltipPosition.html) property. This defaults to [`TooltipPosition.auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipPosition.html).

{% tabs %}
{% highlight Dart %} 
    
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
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
            child: SfPyramidChart(
              tooltipBehavior: _tooltipBehavior,
              series: PyramidSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y)
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

![pointer tooltip](images/tooltip/tooltip_pointer.png)

## Tooltip template

You can customize the appearance of the tooltip with your own widget by using the [`builder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/builder.html) property of [`tooltipBehavior`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/tooltipBehavior.html).

{% tabs %}
{% highlight Dart %} 
    
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
        _tooltipBehavior = TooltipBehavior(
                enable: true,
                // Templating the tooltip
                builder: (dynamic data, dynamic point, dynamic series,
                int pointIndex, int seriesIndex) {
                  return Container(
                    child: Text(
                      'Point Y : ${point.y.toString()}'
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
            child: SfPyramidChart(
              tooltipBehavior: _tooltipBehavior,
              series: PyramidSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y)
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

![Tooltip template](images/tooltip/tooltip_template.png)

##	Activation mode

The [`activationMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/activationMode.html) property is used to restrict the visibility of tooltip based on the touch actions. The default value of this property is [`ActivationMode.singleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html).

The ActivationMode enum contains the following values:

* [`ActivationMode.longPress`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html) - activates tooltip only when performing the long press action.
* [`ActivationMode.singleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html) - activates tooltip only when performing single tap action.
* [`ActivationMode.doubleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html) - activates tooltip only when performing double tap action.
* [`ActivationMode.none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html) - hides the visibility of tooltip when setting activation mode to none.

{% tabs %}
{% highlight Dart %} 
    
    late TooltipBehavior _tooltipBehavior;
    
    @override
    void initState(){
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
            child: SfPyramidChart(
              tooltipBehavior: _tooltipBehavior,
              series: PyramidSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y)
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

Also refer [`tooltip event`](./callbacks#ontooltiprender) for customizing the tooltip further.