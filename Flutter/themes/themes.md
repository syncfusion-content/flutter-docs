---
layout: post
title: Applying Themes for Syncfusion FLutter widgets
description: Learn how to apply theme across all the Syncfusion Flutter widgets with a common approach or to the individual widget.
platform: flutter
control: General
documentation: ug
---

# Theme for Syncfusion widgets

The Syncfusion theme widget allows you to apply colors, font-styles, etc in the application level across all the Syncfusion Flutter widgets with a uniform approach and provide a consistent look.

## Using SfTheme widget

The [`SfTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfTheme-class.html) widget is used to apply theme at one place to all of the applicable Syncfusion Flutter widgets. You can customize all our widgets with the [`SfThemeData`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfThemeData-class.html) and use this class to configure a [`SfTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfTheme-class.html) widget. The [`SfThemeData`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfThemeData-class.html) holds the color and typography values for light and dark themes. For more details, you can refer to the below links.

<table>
    <tr>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfBarcodeThemeData-class.html">SfBarcodeThemeData</a>
        </td>
        <td>
           <a href="https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/SfBarcodeGenerator-class.html">SfBarcodeGenerator</a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfCalendarThemeData-class.html">SfCalendarThemeData</a>
        </td>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar-class.html">SfCalendar</a>
        </td>
    </tr>
    <tr>
        <td>
         <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChartThemeData-class.html">SfChartThemeData</a>
        </td>
        <td>
             <a href="https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html">SfCartesianChart</a> <br/>
             <a href="https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html">SfCircularChart</a><br>
             <a href="https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart-class.html">SfPyramidChart</a><br>
             <a href="https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart-class.html">SfFunnelChart</a>
        </td>
    </tr>
	<tr>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDateRangePickerThemeData-class.html">SfDateRangePickerThemeData</a>
        </td>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker-class.html">SfDateRangePicker</a>
        </td>
    </tr>
    <tr>
       <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfGaugeThemeData-class.html">SfGaugeThemeData</a>
        </td>
        <td>
           <a href="https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge-class.html">SfRadialGauge</a>
        </td>
    </tr>
    <tr>
        <td>
          <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData-class.html">SfRangeSliderThemeData</a>
        </td>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider-class.html">SfRangeSlider</a><br>
            <a href="https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html">SfRangeSelector</a>
        </td>
  </tr>
</table>

The [`SfTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfTheme-class.html) widget is available in the [`syncfusion_flutter_core`](https://pub.dev/packages/syncfusion_flutter_core) package. Since all our widgets are core dependent, you don't need to include the core as a separate package. For example, here we have included the [`syncfusion_flutter_charts`](https://pub.dev/packages/syncfusion_flutter_charts) package in the pub spec file for the purpose of depicting the working model of the theme widget.

{% highlight dart %} 

    dependencies:

    syncfusion_flutter_charts: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter Chart`](https://pub.dev/packages/syncfusion_flutter_charts/versions) widget.

To use the theme widgets, import the following library in your Dart code.

{% highlight dart %} 

    import 'package:syncfusion_flutter_core/theme.dart';

{% endhighlight %}

Once the required package has been imported, initialize the [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html) as a child of  [`SfTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfTheme-class.html) widget. 


{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: SfTheme(
                    data: SfThemeData(
                            chartThemeData: SfChartThemeData(
                                plotAreaBackgroundColor: Colors.grey[400]
                            ) 
                    ),
                    child: SfCartesianChart()
                )
            )
        );
    }

{% endhighlight %}

![Chart theme](images/chart_light.png)

## Dark theme

Syncfusion Flutter widgets provide support for light and dark themes. As the name suggests, these themes will have colors with light and dark color contrasts, respectively. 

By default, the light theme will be applied. You can apply a dark theme using the [`brightness`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfThemeData/brightness.html) property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: SfTheme(
                    data: SfThemeData(
                        brightness: Brightness.dark
                    ),
                    child: SfCartesianChart())
            
        );
    }

{% endhighlight %}

![Dark theme](images/theme_chart.png)

## Specialized theme widget

Using the [`SfTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfTheme-class.html) widget you can apply theme across all the Syncfusion Flutter widgets at one place. If you wish to apply a specific theme to a specific widget alone, this can be achieved using the specialized theme widget. For example, [`SfChartTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChartTheme-class.html) widget in case of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html), [`SfCircularChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html), [`SfPyramidChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart-class.html), [`SfPyramidChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart-class.html) widgets. For more information, find the below links.

<table>
    <tr>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfBarcodeTheme-class.html">SfBarcodeTheme</a>
        </td>
        <td>
           <a href="https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/SfBarcodeGenerator-class.html">SfBarcodeGenerator</a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfCalendarTheme-class.html">SfCalendarTheme</a>
        </td>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar-class.html">SfCalendar</a>
        </td>
    </tr>
    <tr>
        <td>
         <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChartTheme-class.html">SfChartTheme</a>
        </td>
        <td>
             <a href="https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html">SfCartesianChart</a> <br/>
             <a href="https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html">SfCircularChart</a><br>
             <a href="https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart-class.html">SfPyramidChart</a><br>
             <a href="https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart-class.html">SfFunnelChart</a>
        </td>
    </tr>
	<tr>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDateRangePickerTheme-class.html">SfDateRangePickerTheme</a>
        </td>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker-class.html">SfDateRangePicker</a>
        </td>
    </tr>
    <tr>
       <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfGaugeTheme-class.html">SfGaugeTheme</a>
        </td>
        <td>
           <a href="https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge-class.html">SfRadialGauge</a>
        </td>
    </tr>
    <tr>
        <td>
          <a href="https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderTheme-class.html">SfRangeSliderTheme</a>
        </td>
        <td>
            <a href="https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider-class.html">SfRangeSlider</a><br>
            <a href="https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html">SfRangeSelector</a>
        </td>
  </tr>
</table>

In the below example, we have used [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html) widget.

{% highlight dart %} 

     @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: SfChartTheme(
                data: SfChartThemeData(
                    brightness: Brightness.dark, 
                    backgroundColor: Colors.blue[300]),
                child: SfCartesianChart()));
  }

{% endhighlight %}

Here, the [`SfChartThemeData`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfChartThemeData-class.html) includes the properties required to customize the [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html), [`SfCircularChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html), [`SfPyramidChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart-class.html), and [`SfFunnelChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart-class.html) widgets.

N> When dark or light theme is applied to the material app, and Syncfusion theme widgets are not initialized in your application, then based on the theme applied to the material app, the appropriate theme will be applied to Syncfusion widgets.