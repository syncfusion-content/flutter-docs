---
layout: post
title: Callbacks in Flutter Funnel Chart widget | Syncfusion 
description: Learn here all about Callbacks feature of Syncfusion Flutter Funnel Chart (SfFunnelChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Callbacks in Flutter Funnel Chart (SfFunnelChart)

The below Callbacks are for Funnel chart.

## onLegendItemRender

Triggers when the legend item is rendering. Here, you can customize the legend’s text, and shape.  The [`onLegendItemRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/onLegendItemRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/text.html) - specifies the content of the legend.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/pointIndex.html) - specifies the current point index that is applicable for Funnel chart type alone.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/seriesIndex.html) - specifies the current series index.
* [`legendIconType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/legendIconType.html) - specifies the shape of the legend.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/color.html) - to get and set the color of the legend icon.

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfFunnelChart(
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
{% endtabs %}

## onTooltipRender

Triggers while tooltip is rendering. Here, you can customize the text, header, x and y-positions. The [`onTooltipRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/onTooltipRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/text.html) - specifies the content of the tooltip.
* [`header`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/header.html) - specifies the header content of the tooltip.
* [`locationX`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/locationX.html) - specifies the x position of tooltip.
* [`locationY`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/locationY.html) - specifies the y position of tooltip.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/seriesIndex.html) - specifies the current series index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/dataPoints.html) - holds the data point collection.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/pointIndex.html) - specifies the current point index.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/viewportPointIndex.html) - to get the viewport index value of the tapped data label.

{% tabs %}
{% highlight dart %}
    
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
        _tooltipBehavior = TooltipBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfFunnelChart(
            onTooltipRender: (TooltipArgs args){
              args.text = 'Custom Text';
            },
            tooltipBehavior: _tooltipBehavior,
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

## onDataLabelRender

Triggers when data label is rendering. Text and text styles such as color, font size, and font weight can be customized. The [`onDataLabelRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/onDataLabelRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/text.html) - specifies the content of the data label.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/textStyle.html) - used to change the text color, size, font family, font style, and font weight.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/pointIndex.html) - specifies the current point index.
* [`seriesRenderer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/seriesRenderer.html) - specifies current series.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/viewportPointIndex.html) - to get the viewport index value of the tapped data label.


{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfFunnelChart(
            onDataLabelRender:(DataLabelRenderArgs args){
              args.text = 'Data label';
            },
            series: FunnelSeries<ChartData, String>(
              dataLabelSettings: DataLabelSettings(
                  isVisible: true
              )
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

## onLegendTapped

Triggers when tapping the legend item. The [`onLegendTapped`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/onLegendTapped.html) Callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/pointIndex.html) - specifies the current point index that is applicable for Funnel series.
* [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/series.html) - specifies the current series.


{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfFunnelChart(
            onLegendTapped: (LegendTapArgs args) {
              print(args.seriesIndex);
            },
            legend: Legend(isVisible: true)
        )
      )
    );
  }

{% endhighlight %}
{% endtabs %}

## onSelectionChanged

Triggers while selection changes. Here you can customize the selectedColor, unselectedColor, selectedBorderColor, selectedBorderWidth, unselectedBorderColor, and unselectedBorderWidth properties. The [`onSelectionChanged`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/onSelectionChanged.html) Callback contains the following arguments.

* [`seriesRenderer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/seriesRenderer.html) - specifies current series.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/pointIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/pointIndex.html) - specifies the current point index.
* [`selectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedColor.html) - specifies color of the selected data points or series.
* [`unselectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedColor.html) - specifies color of the unselected data points or series.
* [`selectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedBorderColor.html) - specifies border color of the selected data points or series.
* [`selectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedBorderWidth.html) - specifies border width of the selected data points or series.
* [`unselectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedBorderColor.html) - specifies border color of the unselected data points or series.
* [`unselectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedBorderWidth.html) - specifies border width of the unselected data points or series.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/viewportPointIndex.html) - to get the overall point index.

{% tabs %}
{% highlight dart %}
    
    late SelectionBehavior _selectionBehavior;

    @override
    void initState(){
      _selectionBehavior = SelectionBehavior(
               enable: true);              
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfFunnelChart(
          onSelectionChanged: (SelectionArgs args){
              args.selectedColor = Colors.red;
              args.unselectedColor = Colors.lightGreen;
            },
            series: FunnelSeries<ChartData, String>(
                selectionBehavior: _selectionBehavior
            )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

## onDataLabelTapped

Triggers when tapping on the data label of the data point in the series. The [`onDataLabelTapped`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfFunnelChart/onDataLabelTapped.html) Callback contains the following arguments.

* [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/position.html) - specifies the position of the tapped data label in logical pixels.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/seriesIndex.html) - Specifies the series index of the tapped data label
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/pointIndex.html) - Specifies the point index of the tapped data label.
* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/text.html) - Specifies the content of the tapped data label.
* [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/dataLabelSettings.html) - to get the data label customization options specified in that particular series.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/viewportPointIndex.html) - to get the viewport index value of the tapped data label.

>**Note**: This callback will not be called, when the builder is specified for data label (data label template). For this case, custom widget specified in the [`DataLabelSettings.builder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/builder.html) property can be wrapped using the [`GestureDetector`](https://api.flutter.dev/flutter/widgets/GestureDetector-class.html) and this functionality can be achieved in the application level.

{% tabs %}
{% highlight dart %}

    Widget build(BuildContext context) {
      return Container(
        child: SfFunnelChart(
          onDataLabelTapped: (DataLabelTapDetails args) {
            print(args.seriesIndex);                 
          },
          series: FunnelSeries<Sample, DateTime>(
              dataSource: sample,
              xValueMapper: (Sample data, _) => data.x,
              yValueMapper: (Sample data, _) => data.y,
              dataLabelSettings: DataLabelSettings(
                isVisible: true),
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

## onPointTap

Triggers when tapping on the series point. The [`onPointTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/onPointTap.html) callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/pointIndex.html) - specifies the current point index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/dataPoints.html) - holds the data point collection.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/viewportPointIndex.html) - specifies the viewport index value of the tapped data point.

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfFunnelChart(
            series: FunnelSeries<Sample, DateTime>(
                onPointTap: (ChartPointDetails details) {
                  print(details.pointIndex);
                  print(details.seriesIndex);
                }
              )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

## onPointDoubleTap

Triggers when double-tap the series point. The [`onPointDoubleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/onPointDoubleTap.html) callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/pointIndex.html) - specifies the current point index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/dataPoints.html) - holds the data point collection.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/viewportPointIndex.html) - specifies the viewport index value of the double-tapped data point.

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfFunnelChart(
              series: FunnelSeries<Sample, DateTime>(
                onPointDoubleTap: (ChartPointDetails details) {
                  print(details.pointIndex);
                  print(details.seriesIndex);
                }
              )
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

## onPointLongPress

Triggers when long press on the series point. The [`onPointLongPress`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/onPointLongPress.html) callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/pointIndex.html) - specifies the current point index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/dataPoints.html) - holds the data point collection.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/viewportPointIndex.html) - specifies the viewport index value of the long pressed data point.

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfFunnelChart(
              series: FunnelSeries<Sample, DateTime>(
                onPointLongPress: (ChartPointDetails details) {
                  print(details.pointIndex);
                  print(details.seriesIndex);
                }
              )
          )
        )
      );
    }
{% endhighlight %}
{% endtabs %}

## onChartTouchInteractionUp

Triggers when tapped or clicked on the chart area. You can get the tapped region using the [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) argument.

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Container(
            child: SfFunnelChart(
                onChartTouchInteractionUp: (ChartTouchInteractionArgs args){
                  print(args.position.dx.toString());
                  print(args.position.dy.toString());
                }
            )
        );
    }

{% endhighlight %}
{% endtabs %}

## onChartTouchInteractionMove

Triggers when touched or clicked and moved on the chart area. You can get the tapped region using the [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) argument.

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Container(
            child: SfFunnelChart(
                onChartTouchInteractionMove: (ChartTouchInteractionArgs args){
                  print(args.position.dx.toString());
                  print(args.position.dy.toString());
                }
            )
        );
    }

{% endhighlight %}
{% endtabs %}

## onChartTouchInteractionDown

Triggers when touched or clicked on the chart area. You can get the tapped region using the [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) argument.

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Container(
          child: SfFunnelChart(
                onChartTouchInteractionDown: (ChartTouchInteractionArgs args){
                  print(args.position.dx.toString());
                  print(args.position.dy.toString());
                }
            )
        );
    }

{% endhighlight %}
{% endtabs %}

## onRendererCreated

Triggers when the series renderer is created. This callback can be used to obtain the [`FunnelSeriesController`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeriesController-class.html) instance, which is used to access the the public methods in the series.

{% tabs %}
{% highlight dart %}

    //Initialize the series controller
    FunnelSeriesController? funnelSeriesController;
    
    final List<ChartData> chartData = <ChartData>[
      ChartData(1, 24),
      ChartData(2, 20),
      ChartData(3, 23),
      ChartData(4, 57),
      ChartData(5, 30),
      ChartData(6, 41),
    ];

    @override
    Widget build(BuildContext context) {
      return Column(children: <Widget>[
        Container(
          child: SfFunnelChart(
            series: FunnelSeries<ChartData, dynamic>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y,
            onRendererCreated: (FunnelSeriesController controller) {
              funnelSeriesController = controller;
            },
          ),
        ), 
      ),
      Container(
          child: ElevatedButton(
              onPressed: () {
                //Removed a point from data source
                chartData.removeAt(0);
                //Added a point to the data source
                chartData.add(ChartData(3, 23));
                //Here accessed the public method of the series.
                funnelSeriesController!.updateDataSource(
                  addedDataIndexes: <int>[chartData.length - 1],
                  removedDataIndexes: <int>[0],
                );
              },
              child: Container(
                child: Text('Add a point'),
                )
              )
            )
          ]
        );
      }

    class ChartData {
      ChartData(this.x, this.y);
      final num x;
      final double? y;
    }

{% endhighlight %}
{% endtabs %}
