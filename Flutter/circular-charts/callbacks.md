---
layout: post
title: Syncfusion Flutter Chart Callbacks
description: Learn what are all the Callbacks available in Flutter Charts. Callbacks will be triggered on some specific actions in SfCircular chart.
platform: flutter
control: Chart
documentation: ug
---

# Callbacks in Circular charts

The below Callbacks are for Circular chart.

## onLegendItemRender

Triggers when the legend item is rendering. Here, you can customize the legend’s text, and shape.  The [`onLegendItemRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onLegendItemRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/text.html) - specifies the content of the legend.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/pointIndex.html) - specifies the current point index that is applicable for circular chart type alone.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/seriesIndex.html) - specifies the current series index.
* [`legendIconType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/legendIconType.html) - specifies the shape of the legend.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCircularChart(
          legend: Legend(isVisible: true),
          onLegendItemRender: (LegendRenderArgs args){
            args.text = 'Legend Text';
            args.legendIconType = LegendIconType.diamond;
          }
        )
      )
    );
  }

{% endhighlight %}

## onTooltipRender

Triggers while tooltip is rendering. Here, you can customize the text, header, x and y-positions. The [`onTooltipRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onTooltipRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/text.html) - specifies the content of the tooltip.
* [`header`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/header.html) - specifies the header content of the tooltip.
* [`locationX`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/locationX.html) - specifies the x position of tooltip.
* [`locationY`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/locationY.html) - specifies the y position of tooltip.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/seriesIndex.html) - specifies the current series index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/dataPoints.html) - holds the data point collection.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/pointIndex.html) - specifies the current point index.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCircularChart(
          onTooltipRender: (TooltipArgs args){
            args.text = 'Custom Text';
          },
          tooltipBehavior: TooltipBehavior(enable: true),
        )
      )
    );
  }

{% endhighlight %}

## onDataLabelRender

Triggers when data label is rendering. Text and text styles such as color, font size, and font weight can be customized. The [`onDataLabelRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onDataLabelRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/text.html) - specifies the content of the data label.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/textStyle.html) – used to change the text color, size, font family, font style, and font weight.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/pointIndex.html) - specifies the current point index.
* [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/series.html) - specifies current series.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCircularChart(
          onDataLabelRender:(DataLabelRenderArgs args){
            args.text = 'Data label';
          },
          series: <CircularSeries>[
            PieSeries<ChartData, String>(
             dataLabelSettings: DataLabelSettings(
                isVisible: true
             )
            )
          ]
        )
      )
    );
  }

{% endhighlight %}

## onPointTapped

Triggers when tapping the series point. The [`onPointTapped`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onPointTapped.html) Callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PointTapArgs/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PointTapArgs/pointIndex.html) - specifies the current point index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PointTapArgs/dataPoints.html) - holds the data point collection.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCircularChart(
           onPointTapped: (PointTapArgs args){
            print(args.seriesIndex);
            print(args.pointIndex);
          }
        )
      );
    }

{% endhighlight %}

## onLegendTapped

Triggers when tapping the legend item. The [`onLegendTapped`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onLegendTapped.html) Callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/pointIndex.html) - specifies the current point index that is applicable for circular series.
* [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/series.html) - specifies the current series.


{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCircularChart(
          onLegendTapped: (LegendTapArgs args) {
            print(args.seriesIndex);
          },
          legend: Legend(isVisible: true)
      )
    );
  }

{% endhighlight %}

## onSelectionChanged

Triggers while selection changes. Here you can customize the selectedColor, unselectedColor, selectedBorderColor, selectedBorderWidth, unselectedBorderColor, and unselectedBorderWidth properties. The [`onSelectionChanged`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onSelectionChanged.html) Callback contains the following arguments.

* [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/series.html) - specifies current series.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/pointIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/pointIndex.html) - specifies the current point index.
* [`selectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedColor.html) - specifies color of the selected data points or series.
* [`unselectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedColor.html) - specifies color of the unselected data points or series.
* [`selectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedBorderColor.html) - specifies border color of the selected data points or series.
* [`selectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedBorderWidth.html) - specifies border width of the selected data points or series.
* [`unselectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedBorderColor.html) - specifies border color of the unselected data points or series.
* [`unselectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedBorderWidth.html) - specifies border width of the unselected data points or series.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCircularChart(
         onSelectionChanged: (SelectionArgs args){
            args.selectedColor = Colors.red;
            args.unselectedColor = Colors.lightGreen;
          },
          series: <CircularSeries>[
            PieSeries<ChartData, String>(
              selectionBehavior: SelectionBehavior(
                enable: true
              )
            )
          ]
       )
      );
    }

{% endhighlight %}

## onDataLabelTapped

Triggers when tapping on the data label of the data point in the series. The [`onDataLabelTapped`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onDataLabelTapped.html) Callback contains the following arguments.

* [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/position.html) - specifies the position of the tapped data label in logical pixels.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/seriesIndex.html) - Specifies the series index of the tapped data label
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/pointIndex.html) - Specifies the point index of the tapped data label.
* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/text.html) - Specifies the content of the tapped data label.

N> This callback will not be called, when the builder is specified for data label (data label template). For this case, custom widget specified in the [`DataLabelSettings.builder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/builder.html) property can be wrapped using the [`GestureDetector`](https://api.flutter.dev/flutter/widgets/GestureDetector-class.html) and this functionality can be achieved in the application level.

{% highlight dart %}

    Widget build(BuildContext context) {
      return Container(
        child: SfCartesianChart(
          onDatalabelTapped: (DataLabelTapArgs args) {
            print(args.seriesIndex);                 
          },
          series: <CircularSeries<Sample, DateTime>>[
            PieSeries<Sample, DateTime>(
                dataSource: sample,
                xValueMapper: (Sample sales, _) => sales.x,
                yValueMapper: (Sample sales, _) => sales.y,
                dataLabelSettings: DataLabelSettings(
                  isVisible: true),
            )
          ]
        )
      );
    }

{% endhighlight %}