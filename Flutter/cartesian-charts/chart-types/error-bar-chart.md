---
layout: post
title: Error bar chart in Flutter Cartesian Charts widget | Syncfusion
description: Learn here all about error bar chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Error bar Chart in Flutter Cartesian Charts (SfCartesianChart)

Error bars are graphical representations of the variability of data and used on graphs to indicate the error or uncertainty in a reported measurement.

To render a Error bar chart, create an instance of [`ErrorBarSeries`], and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/XyDataSeries-class.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties can be used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the stroke width of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) - changes the stroke width of the line.
* [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) - render error bar with dashes.
* [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/pointColorMapper.html)- maps the individual colors to the data point.

* [`Marker`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/MarkerSettings.html), [`data label`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings-class.html), [`trendline`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/Trendline-class.html), [`Technical indicators`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicators-class.html), and other user interaction features are not applicable for error bar series. And events like [`onPointTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/onPointTap.html), [`onPointDoubleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/onPointDoubleTap.html) and [`onPointLongPress`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/onPointLongPress.html) are not applicable for this series.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final dynamic chartData = [
        ChartData(1, 24),
        ChartData(2, 20),
        ChartData(3, 35),
        ChartData(4, 27),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];

      return Scaffold(
        body: SfCartesianChart(
      series: <ChartSeries<ChartData, int>>[
        ErrorBarSeries<ChartData, int>(
          width: 3.0,
          opacity: 0.7,
          color: Color.fromRGBO(246, 114, 128, 1),
          dataSource: chartData,
          xValueMapper: (ChartData data, _) => data.x,
          yValueMapper: (ChartData data, _) => data.y,
        )
      ],
    ));
    }

    class ChartData {
      const ChartData(this.x, this.y);
      final int x;
      final int y;
    }

{% endhighlight %}

![Error Bar](cartesian-chart-types-images/error_bar_color.jpg)

## Type

The Type property is used to define the error bar type value in `Fixed`, `Custom`, `Percentage`, `StandardDeviation`, and `StandardError`. The default value of this property is `Fixed`.  

You can customize the error bar depending on the error value by setting the values for `HorizontalErrorValue` and `VerticalErrorValue` for all types except `Custom`.

* `HorizontalErrorValue` - It horizontally depicts the error value in positive and negative directions. The default value of `HorizontalErrorValue` is 1.
* `VerticalErrorValue` - It vertically depicts the error value in positive and negative directions. The default value of `VerticalErrorValue` is 3.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final dynamic chartData = [
        ChartData(1, 24),
        ChartData(2, 20),
        ChartData(3, 35),
        ChartData(4, 27),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];

      return Scaffold(
        body: SfCartesianChart(
      series: <ChartSeries<ChartData, int>>[
        ErrorBarSeries<ChartData, int>(
          dataSource: chartData,
          xValueMapper: (ChartData data, _) => data.x,
          yValueMapper: (ChartData data, _) => data.y,
          width: 1.5,
          type: ErrorBarType.standardError
        )
      ],
    ));
    }

    class ChartData {
      const ChartData(this.x, this.y);
      final int x;
      final int y;
    }

{% endhighlight %}

![Error Bar](cartesian-chart-types-images/error_bar_type.jpg)

### Custom type

For `Custom` type,You can customize the error bar depending on the error value by setting the values for `HorizontalPositiveErrorValue`, `HorizontalNegativeErrorValue`, `VerticalPositiveErrorValue` and `VerticalNegativeErrorValue`.

* `HorizontalPositiveErrorValue` - It horizontally depicts the error value in positive direction. The default value of `HorizontalErrorValue` is 1.
* `HorizontalPositiveErrorValue` - It horizontally depicts the error value in positive direction. The default value of `HorizontalErrorValue` is 1.
* `VerticalPositiveErrorValue` - It vertically depicts the error value in positive direction. The default value of `VerticalErrorValue` is 3.
* `VerticalNegativeErrorValue` - It vertically depicts the error value in negative direction. The default value of `VerticalErrorValue` is 3.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final dynamic chartData = [
        ChartData(1, 24),
        ChartData(2, 20),
        ChartData(3, 35),
        ChartData(4, 27),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];

      return Scaffold(
        body: SfCartesianChart(
      series: <ChartSeries<ChartData, int>>[
        ErrorBarSeries<ChartData, int>(
          dataSource: chartData,
          xValueMapper: (ChartData data, _) => data.x,
          yValueMapper: (ChartData data, _) => data.y,
          width: 1.5,
          type: ErrorBarType.custom,
          mode: RenderingMode.both,
          verticalPositiveErrorValue: 5,
          verticalNegativeErrorValue: 2,
          horizontalPositiveErrorValue: 0.2,
          horizontalNegativeErrorValue: 0.5
        )
      ],
    ));
    }

    class ChartData {
      const ChartData(this.x, this.y);
      final int x;
      final int y;
    }

{% endhighlight %}

![Error Bar](cartesian-chart-types-images/error_bar_custom_type.jpg)

## Mode

The error bar mode specifies whether the error bar should be drawn horizontally, vertically, or both ways. Use the `mode` option to switch the error bar mode.The default value of the mode is `RenderingMode.vertical`.You can use the following properties to customize the `mode`,

* `RenderingMode.vertical` - It displays vertical error value only.
* `RenderingMode.horizontal` - It displays horizontal error value only.
* `RenderingMode.vertical`  - It displays both vertical and horizontal error values.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final dynamic chartData = [
        ChartData(1, 24),
        ChartData(2, 20),
        ChartData(3, 35),
        ChartData(4, 27),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];

      return Scaffold(
        body: SfCartesianChart(
      series: <ChartSeries<ChartData, int>>[
        ErrorBarSeries<ChartData, int>(
          dataSource: chartData,
          xValueMapper: (ChartData data, _) => data.x,
          yValueMapper: (ChartData data, _) => data.y,
          width: 1.5,
          mode:RenderingMode.both,
          verticalErrorValue:2,
          horizontalErrorValue:0.2
        )
      ],
    ));
    }

    class ChartData {
      const ChartData(this.x, this.y);
      final int x;
      final int y;
    }

{% endhighlight %}

![Error Bar](cartesian-chart-types-images/error_bar_mode.jpg)

## Direction

Using the `direction` option, you can alter the error bar direction to plus, minus, or both sides.  is The default value of the `direction` is `Direction.both`. .You can use the following properties to customize the `direction`,

* `Direction.both` - Used to set error value in positive and negative directions.
* `Direction.minus` - Used to set error value in a negative direction.
* `Direction.plus` - Used to set error value in a positive direction.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final dynamic chartData = [
        ChartData(1, 24),
        ChartData(2, 20),
        ChartData(3, 35),
        ChartData(4, 27),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];

      return Scaffold(
        body: SfCartesianChart(
      series: <ChartSeries<ChartData, int>>[
        ErrorBarSeries<ChartData, int>(
          dataSource: chartData,
          xValueMapper: (ChartData data, _) => data.x,
          yValueMapper: (ChartData data, _) => data.y,
          width: 1.5,
          direction: Direction.minus
        )
      ],
    ));
    }

    class ChartData {
      const ChartData(this.x, this.y);
      final int x;
      final int y;
    }

{% endhighlight %}

![Error Bar](cartesian-chart-types-images/error_bar_direction.jpg)

## CapLength

You can customize the ErrorBar with the following style properties,

* `capLength` – Used to customize the length of the error bar's cap. The default value of the `capLength` is 10.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final dynamic chartData = [
        ChartData(1, 24),
        ChartData(2, 20),
        ChartData(3, 35),
        ChartData(4, 27),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];

      return Scaffold(
        body: SfCartesianChart(
      series: <ChartSeries<ChartData, int>>[
        ErrorBarSeries<ChartData, int>(
          dataSource: chartData,
          xValueMapper: (ChartData data, _) => data.x,
          yValueMapper: (ChartData data, _) => data.y,
          width: 1.5,
          capLength: 20.0
        )
      ],
    ));
    }

    class ChartData {
      const ChartData(this.x, this.y);
      final int x;
      final int y;
    }

{% endhighlight %}

![Error Bar](cartesian-chart-types-images/error_bar_caplength.jpg)
