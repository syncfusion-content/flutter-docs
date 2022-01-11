---
layout: post
title: Callbacks in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about available Callbacks feature of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Callbacks in Flutter Cartesian Charts (SfCartesianChart)

The below Callbacks are for Cartesian chart.

## onTooltipRender

Triggers when the tooltip is rendering. Here, you can customize the text, header, x and y-positions. The [`onTooltipRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onTooltipRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/text.html) - specifies the content of the tooltip.
* [`header`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/header.html) - specifies the header content of the tooltip.
* [`locationX`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/locationX.html) - specifies the x position of tooltip.
* [`locationY`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/locationY.html) - specifies the y position of tooltip.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/seriesIndex.html) - specifies the current series index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/dataPoints.html) - holds the data point collection.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/pointIndex.html) - specifies the current point index.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/viewportPointIndex.html) - specifies the viewport index value of the tooltip.

 {% highlight dart %}

    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
      _tooltipBehavior =  TooltipBehavior(enable: true);
      super.initState(); 
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            tooltipBehavior: _tooltipBehavior,
            onTooltipRender: (TooltipArgs args) {
              args.text = 'Customized Text';
            }
          )
        )
      );
    }

{% endhighlight %}

## onActualRangeChanged

Triggers when the visible range of an axis is changed, i.e. value changes for minimum, maximum, and interval. Here, you can customize the visible range of an axis. The [`onActualRangeChanged`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onActualRangeChanged.html) Callback contains the following arguments.

* [`axisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActualRangeChangedArgs/axisName.html) - specifies the axis name.
* [`axis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActualRangeChangedArgs/axis.html) - holds the information about the current axis.
* [`actualMin`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActualRangeChangedArgs/actualMin.html) - specifies the actual minimum range of an axis.
* [`actualMax`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActualRangeChangedArgs/actualMax.html) - specifies the actual maximum range of an axis.
* [`actualInterval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActualRangeChangedArgs/actualInterval.html) - specifies the actual interval of an axis.
* [`visibleMin`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActualRangeChangedArgs/visibleMin.html) - specifies the visible minimum range of an axis.
* [`visibleMax`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActualRangeChangedArgs/visibleMax.html) - specifies the visible maximum range of an axis.
* [`visibleInterval`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActualRangeChangedArgs/visibleInterval.html) - specifies the visible interval of an axis. 
* [`orientation`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActualRangeChangedArgs/orientation.html) - specifies the current axis orientation.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            onActualRangeChanged: (ActualRangeChangedArgs args){
              if (args.axisName == 'primaryYAxis'){
                args.visibleMin = 10;
              }
            }
          )
        )
      );
    }

{% endhighlight %}

## onDataLabelRender

Triggers when data label is rendering. Text and text styles such as color, font size, and font weight can be customized. The [`onDataLabelRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onDataLabelRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/text.html) - used to get and set the content of the data label.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/textStyle.html) - used to change the text color, size, font family, font style, and font weight.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/pointIndex.html) - specifies the current point index.
* [`seriesRenderer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/seriesRenderer.html) - specifies current series and the series type may vary based on the chart type.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/dataPoints.html) - used to get the data points of the series.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/viewportPointIndex.html) - to get the viewport index value of the tapped data label.
* [`offset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/offset.html) - used to get and set the horizontal/vertical position of the data label. The first argument sets the horizontal component to x, while the second argument sets the vertical component to y.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/color.html) - used to get and set the background color of a data label.
 
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            onDataLabelRender:(DataLabelRenderArgs args){
              args.text = 'Data label';
              CartesianSeries<ChartData, double> series = args.seriesRenderer;
              //Changed the background color of the data label based on the series type
              if (series.name == 'Product A') {
                args.color = Colors.blue;
              } else if(series.name == 'Product B'){
                args.color = Colors.red;
              }
            },
            series: <CartesianSeries>[
              ColumnSeries<ChartData, double>(
                dataLabelSettings: DataLabelSettings(
                  isVisible: true
                )
              )
            ]
          )
        )
      );
    }

    class ChartData {
      ChartData(this.x, this.y);
      final double x;
      final double? y;
    }

{% endhighlight %}

## onLegendItemRender

Triggers when the legend item is rendering. Here, you can customize the legend’s text, and shape.  The [`onLegendItemRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onLegendItemRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/text.html) - specifies the content of the legend.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/pointIndex.html) - specifies the current point index that is applicable for circular chart type alone.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/seriesIndex.html) - specifies the current series index.
* [`legendIconType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/legendIconType.html) - specifies the shape of the legend.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/color.html) - used to get and set the color of the legend icon.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
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

## onTrackballPositionChanging

Triggers while the trackball position is changing. Here, you can customize the text of the trackball.The [`onTrackballPositionChanging`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onTrackballPositionChanging.html) Callback contains the following argument.

* [`chartPointInfo`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballArgs/chartPointInfo.html) - holds the information about the current point.

{% highlight dart %}

  late TrackballBehavior _trackballBehavior;

    @override
    void initState(){
      _trackballBehavior =  TrackballBehavior(enable: true);
      super.initState(); 
    }

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center( 
          child: SfCartesianChart(
              onTrackballPositionChanging: (TrackballArgs args) {
                args.chartPointInfo.label = 'Custom Text';
              },
              trackballBehavior: _trackballBehavior
            )
          )
      );
    }

{% endhighlight %}

## onCrosshairPositionChanging

Triggers while the crosshair position is changing. Here, you can customize the text and line color of the crosshair.The [`onCrosshairPositionChanging`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onCrosshairPositionChanging.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairRenderArgs/text.html) - used to get and set the crosshair tooltip content.
* [`value`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairRenderArgs/value.html) - specifies the actual value of the crosshair.
* [`axisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairRenderArgs/axisName.html) - specifies the axis name.
* [`orientation`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairRenderArgs/orientation.html) - specifies the current axis orientation.
* [`axis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairRenderArgs/axis.html) - holds the information about the current axis.
* [`lineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairRenderArgs/lineColor.html) - used to get and set the color of the crosshair line.

{% highlight dart %}
    
    late CrosshairBehavior _crosshairBehavior;

    @override
    void initState(){
      _crosshairBehavior = CrosshairBehavior(
            enable: true
          );
      super.initState(); 
    }

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            onCrosshairPositionChanging: (CrosshairRenderArgs args){
              args.text = 'crosshair';
            },
            crosshairBehavior: _crosshairBehavior
          )
        )
      );
    }

{% endhighlight %}

## onZooming

Triggers when the zooming action is in progress. The [`onZooming`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onZooming.html) Callback contains the following arguments.

* [`axis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/axis.html) - holds the information about the current axis.
* [`currentZoomPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/currentZoomPosition.html) - used to get and set the current zoom position of an axis.
* [`currentZoomFactor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/currentZoomFactor.html) - used to get and set the current zoom factor of an axis.
* [`previousZoomPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/previousZoomPosition.html) - specifies the previous zoom position of an axis.
* [`previousZoomFactor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/previousZoomFactor.html) - specifies the previous zoom factor of an axis.

{% highlight dart %}
    
    late ZoomPanBehavior _zoomPanBehavior;

    @override
    void initState(){
      _zoomPanBehavior = ZoomPanBehavior(
            enableDoubleTapZooming: true,
            enablePanning: true,
            enablePinching: true,
            enableSelectionZooming: true
          );
      super.initState(); 
    }

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
          body: Center(
            child: SfCartesianChart(
              zoomPanBehavior: _zoomPanBehavior,
              onZooming: (ZoomPanArgs args){
                  print(args.currentZoomFactor);
                  print(args.currentZoomPosition);
              }
            )
          )
      );
    }

{% endhighlight %}

## onZoomStart

Triggers when zooming action begins. The [`onZoomStart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onZoomStart.html) Callback contains the following arguments.

* [`axis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/axis.html) - holds the information about the current axis.
* [`currentZoomPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/currentZoomPosition.html) - used to get and set the current zoom position of an axis.
* [`currentZoomFactor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/currentZoomFactor.html) - used to get and set the current zoom factor of an axis.
* [`previousZoomPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/previousZoomPosition.html) - specifies the previous zoom position of an axis.
* [`previousZoomFactor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/previousZoomFactor.html) - specifies the previous zoom factor of an axis.

{% highlight dart %}
    
    late ZoomPanBehavior _zoomPanBehavior;

    @override
    void initState(){
      _zoomPanBehavior = ZoomPanBehavior(
            enableDoubleTapZooming: true,
            enablePanning: true,
            enablePinching: true,
            enableSelectionZooming: true
          );
      super.initState(); 
    }

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            zoomPanBehavior: _zoomPanBehavior,
            onZoomStart: (ZoomPanArgs args){
                print(args.currentZoomFactor);
                print(args.currentZoomPosition);
            }
          )
        )
      );
    }

{% endhighlight %}

## onZoomEnd

Triggers when the zooming action is completed. The [`onZoomEnd`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onZoomEnd.html) Callback contains the following arguments.

* [`axis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/axis.html) - holds the information about the current axis.
* [`currentZoomPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/currentZoomPosition.html) - used to get and set the current zoom position of an axis.
* [`currentZoomFactor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/currentZoomFactor.html) - used to get and set the current zoom factor of an axis.
* [`previousZoomPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/previousZoomPosition.html) - specifies the previous zoom position of an axis.
* [`previousZoomFactor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/previousZoomFactor.html) - specifies the previous zoom factor of an axis.

{% highlight dart %}
    
    late ZoomPanBehavior _zoomPanBehavior;

    @override
    void initState(){
      _zoomPanBehavior = ZoomPanBehavior(
            enableDoubleTapZooming: true,
            enablePanning: true,
            enablePinching: true,
            enableSelectionZooming: true
          );
      super.initState(); 
    }

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            zoomPanBehavior: _zoomPanBehavior,
            onZoomEnd: (ZoomPanArgs args){
                print(args.currentZoomFactor);
                print(args.currentZoomPosition);
            }
          )
        )
      );
    }

{% endhighlight %}

## onZoomReset

Triggers when zoomed state is reset. The  [`onZoomReset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onZoomReset.html) Callback contains the following arguments.

* [`axis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/axis.html) - holds the information about the current axis.
* [`currentZoomPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/currentZoomPosition.html) - used to get and set the current zoom position of an axis.
* [`currentZoomFactor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/currentZoomFactor.html) - used to get and set the current zoom factor of an axis.
* [`previousZoomPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/previousZoomPosition.html) - specifies the previous zoom position of an axis.
* [`previousZoomFactor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanArgs/previousZoomFactor.html) - specifies the previous zoom factor of an axis.

{% highlight dart %}
    
    late ZoomPanBehavior _zoomPanBehavior;

    @override
    void initState(){
      _zoomPanBehavior = ZoomPanBehavior(
            enableDoubleTapZooming: true,
            enablePanning: true,
            enablePinching: true,
            enableSelectionZooming: true
          );
      super.initState(); 
    }

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            zoomPanBehavior: _zoomPanBehavior,
            onZoomReset: (ZoomPanArgs args){
                print(args.currentZoomFactor);
                print(args.currentZoomPosition);
            }
          )
        )
      );
    }

{% endhighlight %}

## onPointTap

Triggers when tapping on the series point. The [`onPointTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/onPointTap.html) callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/pointIndex.html) - specifies the current point index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/dataPoints.html) - holds the data point collection.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/viewportPointIndex.html) - specifies the viewport index value of the tapped data point.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            series: <ChartSeries<ChartData,num>>[
              ColumnSeries(
                onPointTap: (ChartPointDetails details) {
                  print(details.pointIndex);
                  print(details.seriesIndex);
                }
              )
            ],
          )
        )
      );
    }

{% endhighlight %}

## onPointDoubleTap

Triggers when double-tap the series point. The [`onPointDoubleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/onPointDoubleTap.html) callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/pointIndex.html) - specifies the current point index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/dataPoints.html) - holds the data point collection.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/viewportPointIndex.html) - specifies the viewport index value of the double-tapped data point.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            series: <ChartSeries<ChartData,num>>[
              ColumnSeries(
                onPointDoubleTap: (ChartPointDetails details) {
                  print(details.pointIndex);
                  print(details.seriesIndex);
                }
              )
            ],
          )
        )
      );
    }

{% endhighlight %}

## onPointLongPress

Triggers when long press on the series point. The [`onPointLongPress`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/onPointLongPress.html) callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/pointIndex.html) - specifies the current point index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/dataPoints.html) - holds the data point collection.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/viewportPointIndex.html) - specifies the viewport index value of the long pressed data point.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            series: <ChartSeries<ChartData,num>>[
              ColumnSeries(
                onPointLongPress: (ChartPointDetails details) {
                  print(details.pointIndex);
                  print(details.seriesIndex);
                }
              )
            ],
          )
        )
      );
    }
{% endhighlight %}

## onAxisLabelTapped

Triggers when tapping the axis label. The  [`onAxisLabelTapped`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onAxisLabelTapped.html) Callback contains the following arguments.

* [`axis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelTapArgs/axis.html) - holds the information about the current axis.
* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelTapArgs/text.html) - specifies the content of the axis label.
* [`value`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelTapArgs/value.html) - specifies the actual value of the current axis label.
* [`axisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelTapArgs/axisName.html) - used to get the axis name.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            onAxisLabelTapped: (AxisLabelTapArgs args) {
              print(args.text);
            }
          )
        )
      );
    }

{% endhighlight %}

#### See Also

* [Navigating to an hyperlink on axis label tap](https://www.syncfusion.com/kb/12202/how-to-navigate-to-a-hyperlink-when-clicked-on-chart-axis-label-sfcartesianchart).

## onLegendTapped

Triggers when tapping the legend item. The  [`onLegendTapped`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onLegendTapped.html) Callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/pointIndex.html) - specifies the current point index that is applicable for circular series.
* [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/series.html) - specifies the current series and the series type may vary based on the chart type.


{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            onLegendTapped: (LegendTapArgs args) {
              print(args.seriesIndex);
            },
            legend: Legend(isVisible: true)
          )
        )
      );
    }

{% endhighlight %}

## onSelectionChanged

Triggers while selection changes. Here you can customize the selectedColor, unselectedColor, selectedBorderColor, selectedBorderWidth, unselectedBorderColor, and unselectedBorderWidth properties. The [`onSelectionChanged`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onSelectionChanged.html) Callback contains the following arguments.

* [`seriesRenderer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/seriesRenderer.html) - specifies current series.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/pointIndex.html) - specifies the current point index.
* [`selectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedColor.html) - used to get and set the color of the selected data points or series.
* [`unselectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedColor.html) - used to get and set the color of the unselected data points or series.
* [`selectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedBorderColor.html) - used to get and set the border color of the selected data points or series.
* [`selectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedBorderWidth.html) - used to get and set the border width of the selected data points or series.
* [`unselectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedBorderColor.html) - used to get and set the border color of the unselected data points or series.
* [`unselectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedBorderWidth.html) - used to get and set the border width of the unselected data points or series.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/viewportPointIndex.html) - used to get the viewport index value of the selected data points.

{% highlight dart %}
    
    late SelectionBehavior _selectionBehavior;

    @override
    void initState(){
      _selectionBehavior =  SelectionBehavior(enable: true);
      super.initState(); 
    }

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
          body: Center(
            child: SfCartesianChart(
              onSelectionChanged: (SelectionArgs args){
                args.selectedColor = Colors.red;
                args.unselectedColor = Colors.lightGreen;
              },
              series: <CartesianSeries>[
                ColumnSeries<ChartData, double>(
                  selectionBehavior: _selectionBehavior
                )
              ]
            )
          )
      );
    }

    class ChartData {
      ChartData(this.x, this.y);
      final double x;
      final double? y;
    }

{% endhighlight %}

## onRenderDetailsUpdate (TechnicalIndicators)
 
Triggers when the indicator is rendering. Here you can customize the name, calculated data points, signal line color, signal line width, signal line dash array, and so on.
 
The [`onRenderDetailsUpdate`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicators/onRenderDetailsUpdate.html) contains following arguments.

* [`name`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderParams/name.html) - used to get and set the indicator name.
* [`calculatedDataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderParams/calculatedDataPoints.html) - used to get the calculated indicator data points details.
* [`signalLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicatorRenderDetails/signalLineColor.html) - used to change the color of the signal line.
* [`signalLineWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicatorRenderDetails/signalLineWidth.html) - used to change the width of the signal line.
* [`signalLineDashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicatorRenderDetails/signalLineDashArray.html) - used to change the dash array size of the signal line.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      List<double> signalLineDashArray = <double>[5,5];
      double signalLineWidth = 3.0;
      Color signalLineColor = Colors.cyan;
      return Scaffold(
        body:Center(
          child: SfCartesianChart(
            indicators: <TechnicalIndicators<dynamic, dynamic>>[
              SmaIndicator<dynamic, dynamic>(
                onRenderDetailsUpdate: (IndicatorRenderParams params) {
                  return TechnicalIndicatorRenderDetails(signalLineColor, signalLineWidth, signalLineDashArray);
                },
            )],
          )
        )
      );
    }
    
{% endhighlight %}

## onRenderDetailsUpdate (Trendline)

Triggers when the trendline gets rendered. The `onRenderDetailsUpdate` callback contains the following arguments.

* `seriesName` - specifies the series name of the trendline.
* `calculatedDataPoints` - specifies the calculated data points of the trendline.
* `trendlineName` - specifies the name of the trendline.
* `intercept` - specifies the intercept value of the trendline.
* `rSquaredValue` - specifies the r-squared value of the trendline.
* `slope` - specifies the slope value of the trendline.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            series: <LineSeries<ChartData, String>>[
              LineSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
                trendlines: <Trendline>[
                  Trendline(onRenderDetailsUpdate: (TrendlineRenderParams args) {
                    print('Slope value: ' + args.slope![0].toString());
                    print('rSquare value: ' + args.rSquaredValue.toString());
                    print('Intercept value (x): ' + args.intercept.toString());
                  })
              ])
          ],
      )));
    }

{% endhighlight %}

>**NOTE**
* The slope values of the polynomial trendline type will depend on the polynomial order. The intercept, slope, and rSquaredValue are not applicable for moving average trendline type.

## onRendererCreated

Triggers when the series renderer is created. This callback can be used to obtain the [`ChartSeriesController`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeriesController-class.html) instance, which is used to access the the public methods in the series.

{% highlight dart %}

    //Initialize the series controller
    ChartSeriesController? _chartSeriesController;
    
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

      return Column(
        children: <Widget>[
          Container(
          child: SfCartesianChart(
                series: <LineSeries<SalesData, num>>[
                    LineSeries<SalesData, num>(
                      dataSource: chartData,
                      //Initialize the onRendererCreated event and store the controller for the respective series
                      onRendererCreated: (ChartSeriesController controller) {
                          _chartSeriesController = controller;
                      },
                    ),
                  ],
            )
          ),
          Container(
            child: ElevatedButton(
              onPressed: () {
                //Removed a point from data source
                chartData.removeAt(0);
                //Added a point to the data source
                chartData.add(ChartData(3,23));
                //Here accessed the public method of the series.
                _chartSeriesController?.updateDataSource(
                  addedDataIndexes: <int>[chartData.length -1],
                  removedDataIndexes: <int>[0],
                );
              },
              child: Container(child: Text('Add a point'),)
            )
          )
        ]
      );
    }

    class SalesData {
      SalesData(this.x, this.y);
      final num x;
      final double? y;
    }

{% endhighlight %}

## onChartTouchInteractionDown

Triggers when touched or clicked on the chart area. You can get the tapped region using the [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) argument.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Container(
          child: SfCartesianChart(
                onChartTouchInteractionDown: (ChartTouchInteractionArgs args){
                  print(args.position.dx.toString());
                  print(args.position.dy.toString());
                }
            )
        );
    }

{% endhighlight %}

## onChartTouchInteractionUp

Triggers when tapped or clicked on the chart area. You can get the tapped region using the [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) argument.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
     return Container(
        child: SfCartesianChart(
            onChartTouchInteractionUp: (ChartTouchInteractionArgs args){
                print(args.position.dx.toString());
                print(args.position.dy.toString());
              }
        )
    );
  }

{% endhighlight %}

## onChartTouchInteractionMove

Triggers when touched or clicked and moved on the chart area. You can get the tapped region using the [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) argument.

{% highlight dart %}

  @override
  Widget build(BuildContext context) {
      return Container(
        child: SfCartesianChart(
            onChartTouchInteractionMove: (ChartTouchInteractionArgs args){
                print(args.position.dx.toString());
                print(args.position.dy.toString());
              }
        )
    );
  }

{% endhighlight %}

## onMarkerRender

Triggers when the marker is being rendered. Here, you can customize the following arguments.

* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerRenderArgs/pointIndex.html) - to get the point index of the marker.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerRenderArgs/seriesIndex.html) - to get the series index of the marker.
* [`shape`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerRenderArgs/shape.html) - to get and set the shape of the marker.
* [`markerHeight`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerRenderArgs/markerHeight.html) - to get and set the height of the marker.
* [`markerWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerRenderArgs/markerWidth.html) - to get and set the width of the marker.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerRenderArgs/color.html) - to get and set the color of the marker.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerRenderArgs/borderWidth.html) - to get and set the border width of the marker.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerRenderArgs/borderColor.html) - to get and set the border color of the marker.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerRenderArgs/viewportPointIndex.html) - to get the viewport index value of the tapped data label.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Container(
            child: SfCartesianChart(
                onMarkerRender: (MarkerRenderArgs args) {
                  if (args.pointIndex == 1) {
                    args.color = Colors.red;
                    args.markerHeight = 20;
                    args.markerWidth = 20;
                    args.shape = DataMarkerType.diamond;
                    args.borderColor = Colors.green;
                    args.borderWidth = 2;
                  }
                },
            )
        );
    }

{% endhighlight %}

## onDataLabelTapped
Triggers when tapping on the data label of the data point in the series. The [`onDataLabelTapped`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onDataLabelTapped.html) Callback contains the following arguments.

* [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/position.html) - specifies the position of the tapped data label in logical pixels.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/seriesIndex.html) - specifies the series index of the tapped data label
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/pointIndex.html) - specifies the point index of the tapped data label.
* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/text.html) - specifies the content of the tapped data label.
* [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/dataLabelSettings.html) - to get the data label customization options specified in that particular series.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/viewportPointIndex.html) - to get the viewport index value of the tapped data label.


>**NOTE**: This callback will not be called, when the builder is specified for data label (data label template). For this case, custom widget specified in the [`DataLabelSettings.builder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/builder.html) property can be wrapped using the [`GestureDetector`](https://api.flutter.dev/flutter/widgets/GestureDetector-class.html) and this functionality can be achieved in the application level.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Container(
          child: SfCartesianChart(
              onDatalabelTapped: (DataLabelTapArgs args) {
                print(args.seriesIndex);                 
              },
              series: <ChartSeries<Sample, DateTime>>[
                  LineSeries<Sample, DateTime>(
                    dataSource: chartData,
                    xValueMapper: (Sample sales, _) => sales.x,
                    yValueMapper: (Sample sales, _) => sales.y,
                    dataLabelSettings: DataLabelSettings(
                        isVisible: true),
                  )
              ]
          )
      );
    }

    class Sample{
      Sample(this.x, this,y);
      final DateTime x;
      final double? y;
    }

{% endhighlight %}

## onPlotAreaSwipe

Triggers while swiping on the plot area. Whenever the swiping happens on the plot area (the series rendering area), [`onPlotAreaSwipe`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onPlotAreaSwipe.html) callback will be called. It provides options to get the direction of swiping. If the chart is swiped from left to right direction, the direction is [`ChartSwipeDirection.start`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSwipeDirection.html) and if the swipe happens from right to left direction, the direction is [`ChartSwipeDirection.end`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSwipeDirection.html). Using this callback, the user will be able to achieve pagination functionality (i.e., on swiping over chart area, next set of data points can be loaded to the chart).

{% highlight dart %}

    //Initialize the series controller
    ChartSeriesController? SeriesController;
    
    @override
    Widget build(BuildContext context) {
      return Container(
         child: SfCartesianChart(
            onPlotAreaSwipe:
              (ChartSwipeDirection direction) =>
                  performSwipe(direction),
            series: <ChartSeries<SalesData, num>>[
                 AreaSeries<SalesData, num>(
                     dataSource: chartData,
                 ),
            ],
         )
      );
    }

    Widget performSwipe(ChartSwipeDirection direction) {
        if (direction == ChartSwipeDirection.end) {
            chartData.add(ChartSampleData(
                x: chartData[chartData.length - 1].x + 1,
                y: 10));
            seriesController?.updateDataSource(addedDataIndex: chartData.length - 1);
      }
    }

    class SalesData {
      SalesData(this.x, this.y);
      final num x;
      final double? y;
    }

{% endhighlight %}

## onRenderDetailsUpdate (ErrorBarSeries)

Triggers when the error bar is being rendered. In this `onRenderDetailsUpdate` callback, you can get the following arguments.

* `pointIndex` - To obtain the point index of the error bar.
* `viewPortPointIndex` - To obtain the viewport index value of the error bar.
* `calculatedErrorBarValues` - This contains the calculated error bar values such as `horizontalPositiveErrorValue`,`horizontalNegativeErrorValue`,`verticalPositiveErrorValue` and `verticalNegativeErrorValue`.

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
          onRenderDetailsUpdate: (ErrorBarRenderDetails args) {
            print(args.pointIndex);
            print(args.viewPortPointIndex);
            print(
                args.calculatedErrorBarValues!.horizontalPositiveErrorValue);
            print(
                args.calculatedErrorBarValues!.horizontalNegativeErrorValue);
            print(args.calculatedErrorBarValues!.verticalPositiveErrorValue);
            print(args.calculatedErrorBarValues!.verticalNegativeErrorValue);
          })
      ],
    )
    );
    }

    class ChartData {
      ChartData(this.x, this.y);
      final int x;
      final int y;
    }

{% endhighlight %}

## onCreateRenderer

Used to create the renderer for custom series. This is applicable only when the custom series is defined in the sample and for built-in series types, it is not applicable.

Renderer created in this will hold the series state and this should be created for each series. [`onCreateRenderer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/onCreateRenderer.html) callback function should return the renderer class and should not return null.

Series state will be created only once per series and will not be created again when we update the series.

Defaults to `null`.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = <ChartData>[
        ChartData(1, 24),
        ChartData(2, 20),
        ChartData(3, 35),
        ChartData(4, 27),
        ChartData(5, 30),
        ChartData(6, 41),
        ChartData(7, 26)
      ];
      return Container(
        child: SfCartesianChart(
          series: <ColumnSeries<ChartData, int>>[
            ColumnSeries<ChartData, int>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
              onCreateRenderer: (ChartSeries<ChartData, int> series) {
                return _CustomColumnSeriesRenderer(series as ColumnSeries<ChartData, int>);
              }
            ),
          ],
        )
      );
    }

    class _CustomColumnSeriesRenderer extends ColumnSeriesRenderer {
      _CustomColumnSeriesRenderer(this.series);

      final ColumnSeries<ChartData, int> series;
      @override
      ChartSegment createSegment() {
        return _ColumnCustomPainter(series);
      }
    }

    class _ColumnCustomPainter extends ColumnSegment {
      _ColumnCustomPainter(this.series);

      final ColumnSeries<ChartData, int> series;
      @override
      int get currentSegmentIndex => super.currentSegmentIndex!;

      @override
      Paint getFillPaint() {
        final Paint customerFillPaint = Paint();
        customerFillPaint.color = series.dataSource[currentSegmentIndex].y > 30
          ? Colors.red
          : Colors.green;
        customerFillPaint.style = PaintingStyle.fill;
        return customerFillPaint;
      }

      @override
      void onPaint(Canvas canvas) {
        super.onPaint(canvas);
      }
    }
 
    class ChartData {
      ChartData(this.x, this.y);
      final int x;
      final int y;
    }
  
{% endhighlight %}

## onCreateShader

The [`onCreateShader`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/onCreateShader.html)  provides options to get the outer rect, inner rect, and render type (either series or legend) using [`ChartShaderDetails`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartShaderDetails-class.html)  class.

The onCreateShader callback is called once while rendering
the data points and legend. For further reference on this callback, Check the [`Gradient fill`](https://help.syncfusion.com/flutter/cartesian-charts/series-customization#gradient-fill) section.

{% highlight dart %}

    /// Package import
    import 'dart:ui' as ui;

    Widget build(BuildContext context) {
    final List<ChartData> chartData = <ChartData>[
      ChartData('IND', 24),
      ChartData('AUS', 20),
      ChartData('USA', 27),
      ChartData('DEU', 57),
      ChartData('ITA', 30),
      ChartData('UK', 41),
    ];
    final List<Color> colors = <Color>[
      const Color.fromRGBO(75, 135, 185, 1),
      const Color.fromRGBO(192, 108, 132, 1),
      const Color.fromRGBO(246, 114, 128, 1),
      const Color.fromRGBO(248, 177, 149, 1),
      const Color.fromRGBO(116, 180, 155, 1)
    ];
    final List<double> stops = <double>[
      0.2,
      0.4,
      0.6,
      0.8,
      1,
    ];

    return Scaffold(
        appBar: AppBar(),
        body: Center(
            child: Container(
          child: SfCartesianChart(
            primaryXAxis: CategoryAxis(),
            series: <CartesianSeries<ChartData, String>>[
            AreaSeries<ChartData, String>(
              dataSource: chartData,
              onCreateShader: (ShaderDetails chartShaderDetails) {
                return ui.Gradient.linear(chartShaderDetails.rect.topRight,
                    chartShaderDetails.rect.centerLeft, colors, stops);
              },
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y),
                ]
              ),
            )
          )
        );
      }
    }

    class ChartData {
      ChartData(this.x, this.y);
      final num x;
      final double? y;
  }

{% endhighlight %}

## axisLabelFormatter

Called while rendering each axis label in the chart. Provides label text, axis name, orientation of the axis, trimmed text and text styles such as color, font size, and font weight to the user using the `AxisLabelRenderDetails` class.

You can customize the text and text style using the `ChartAxisLabel` class and can return it.

Defaults to `null`.

{% highlight dart %}

    Widget build(BuildContext context) {
      return Container(
        child: SfCartesianChart(
            primarXAxis: CategoryAxis(
               axisLabelFormatter: (AxisLabelRenderDetails details) => axis(details),
            ),
        ));
    }

    ChartAxisLabel axis(AxisLabelRenderDetails details) {
      return ChartAxisLabel('Label', details.textStyle);
    }
{% endhighlight %}

## multiLevelLabelFormatter

Triggers while rendering the multi-level labels. Text and text styles such as color, font size, font-weight, etc can be customized by using [`ChartAxisLabel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxisLabel-class.html) class. The [`MultiLevelLabelRenderDetails`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelLabelRenderDetails-class.html) contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelLabelRenderDetails/text.html) - specifies the multi-level label to be rendered.
* [`actualLevel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelLabelRenderDetails/actualLevel.html) - specifies the re-ordered level value of the current multi-level label.
* [`axisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelLabelRenderDetails/axisName.html) - specifies the axis name.
* [`index`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelLabelRenderDetails/index.html) - specifies the index of the multi-level label. and the index will be in the same order as specified in [`multiLevelLabels`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAxis/multiLevelLabels.html) property.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MultiLevelLabelRenderDetails/textStyle.html) - used to change the text color, size, font family, font style, etc.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = <ChartData>[
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
          primaryXAxis: NumericAxis(
            multiLevelLabelFormatter: (MultiLevelLabelRenderDetails details) {
              return ChartAxisLabel(
                details.index == 2 ? 'Callback' : details.text,
                details.textStyle);
            },
            multiLevelLabels: const <NumericMultiLevelLabel>[
              NumericMultiLevelLabel(
                start: 1, 
                end: 4, 
                text: 'First'
              ),
              NumericMultiLevelLabel(
                start: 4, 
                end: 7, 
                text: 'Second'
              ),
              NumericMultiLevelLabel(
                start: 1, 
                end: 4, 
                text: 'Third', 
                level: 1
              ),
              NumericMultiLevelLabel(
                start: 4, 
                end: 7, 
                text: 'Fourth', 
                level: 1
              ),
            ]
          ),
          series: <ChartSeries<ChartData, int>>[
            LineSeries<ChartData, int>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
            )
          ]
        )
      );
    }

    class ChartData {
      ChartData(this.x, this.y);
        final int x;
        final int y;
    }

{% endhighlight %}

## See Also

* [Customize the tooltip using its callback event](https://www.syncfusion.com/kb/11507/how-to-customize-the-tooltip-using-callback-events-sfcartesianchart).
* [Customize the axis labels using its callback event](https://www.syncfusion.com/kb/11678/how-to-customize-the-axis-labels-using-callback-events-sfcartesianchart).
* [Customize the data labels using its callback event](https://www.syncfusion.com/kb/11679/how-to-customize-data-labels-using-callback-events-sfcartesianchart).
* [Disabling trackball tooltip for particular series using its callback event](https://www.syncfusion.com/kb/11638/how-to-disable-trackball-tooltip-for-particular-series-in-cartesian-charts-sfcartesianchart).
* [To Synchronize panning in multiple charts](https://www.syncfusion.com/kb/11533/how-to-synchronize-panning-in-multiple-charts-sfcartesianchart).

>**NOTE**:`chartData` in the above code snippets is a class type list and holds the data for binding to the chart series. Refer [Bind data source](https://help.syncfusion.com/flutter/cartesian-charts/getting-started#bind-data-source) topic for more details.
