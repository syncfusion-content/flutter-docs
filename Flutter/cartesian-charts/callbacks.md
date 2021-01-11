---
layout: post
title: Syncfusion Flutter Chart Callbacks
description: Learn what are all the Callbacks available in Flutter Charts. Callbacks will be triggered on some specific actions in chart.
platform: flutter
control: Chart
documentation: ug
---

# Callbacks in Cartesian charts

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

     @override
     Widget build(BuildContext context) {
       return Scaffold(
         body: Center(
           child: SfCartesianChart(
             tooltipBehavior: TooltipBehavior(enable: true),
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

## onAxisLabelRender

Triggers while rendering the axis labels. Text and text styles such as color, font size, and font weight can be customized. The [`onAxisLabelRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onAxisLabelRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelRenderArgs/text.html) - specifies the axis label to be rendered.
* [`value`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelRenderArgs/value.html) - specifies the actual value of the current axis label.
* [`axisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelRenderArgs/axisName.html) - specifies the axis name.
* [`orientation`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelRenderArgs/orientation.html) - specifies the current axis orientation.
* [`axis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelRenderArgs/axis.html) - holds the information about the current axis.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AxisLabelRenderArgs/textStyle.html) - used to change the text color, size, font family, font style, and font weight.


{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            onAxisLabelRender: (AxisLabelRenderArgs args) {
              if(args.axisName == 'primaryXAxis'){
                args.text = 'Text';
                args.textStyle.color = Colors.red;
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
* [`seriesRenderer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/series.html) - specifies current series and the series type may vary based on the chart type.
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
            CartesianSeries<dynamic, dynamic> series = args.seriesRenderer;
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

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
          onTrackballPositionChanging: (TrackballArgs args) {
            args.chartPointInfo.label = 'Custom Text';
          },
          trackballBehavior: TrackballBehavior(
            enable: true
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

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
          onCrosshairPositionChanging: (CrosshairRenderArgs args){
            args.text = 'crosshair';
          },
          crosshairBehavior: CrosshairBehavior(
            enable: true
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

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
          zoomPanBehavior: ZoomPanBehavior(
            enableDoubleTapZooming: true,
            enablePanning: true,
            enablePinching: true,
            enableSelectionZooming: true
          ),
          onZooming: (ZoomPanArgs args){
              print(args.currentZoomFactor);
              print(args.currentZoomPosition);
          }
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

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
          zoomPanBehavior: ZoomPanBehavior(
            enableDoubleTapZooming: true,
            enablePanning: true,
            enablePinching: true,
            enableSelectionZooming: true
          ),
          onZoomStart: (ZoomPanArgs args){
              print(args.currentZoomFactor);
              print(args.currentZoomPosition);
          }
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

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
          zoomPanBehavior: ZoomPanBehavior(
            enableDoubleTapZooming: true,
            enablePanning: true,
            enablePinching: true,
            enableSelectionZooming: true
          ),
          onZoomEnd: (ZoomPanArgs args){
              print(args.currentZoomFactor);
              print(args.currentZoomPosition);
          }
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

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
          zoomPanBehavior: ZoomPanBehavior(
            enableDoubleTapZooming: true,
            enablePanning: true,
            enablePinching: true,
            enableSelectionZooming: true
          ),
          onZoomReset: (ZoomPanArgs args){
              print(args.currentZoomFactor);
              print(args.currentZoomPosition);
          }
       )
      );
    }

{% endhighlight %}

## onPointTapped

Triggers when tapping the series point. The [`onPointTapped`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onPointTapped.html) Callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PointTapArgs/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PointTapArgs/pointIndex.html) - specifies the current point index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PointTapArgs/dataPoints.html) - holds the data point collection.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PointTapArgs/viewportPointIndex.html) - specifies the viewport index value of the tapped data point.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
           onPointTapped: (PointTapArgs args){
            print(args.seriesIndex);
            print(args.pointIndex);
          }
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
      );
    }

{% endhighlight %}

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
    );
  }

{% endhighlight %}

## onSelectionChanged

Triggers while selection changes. Here you can customize the selectedColor, unselectedColor, selectedBorderColor, selectedBorderWidth, unselectedBorderColor, and unselectedBorderWidth properties. The [`onSelectionChanged`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/onSelectionChanged.html) Callback contains the following arguments.

* [`seriesRenderer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/series.html) - specifies current series.
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
              selectionBehavior: SelectionBehavior(
                enable: true,
              )
            )
          ]
        )
      );
    }

{% endhighlight %}

## onIndicatorRender
 
Triggers when indicator is rendering. Here you can customize the name, signal line color, signal line width,dash array and so on.
 
The [`onIndicatorRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderArgs-class.html) contains following arguments.

* [`indicatorName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderArgs/indicatorName.html) - used to get and set the indicator name.
* [`indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderArgs/indicator.html) - used to get the technical indicator information.
* [`signalLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderArgs/signalLineColor.html) - used to change the color of the signal line.
* [`signalLineWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderArgs/signalLineWidth.html) - used to change the width of the signal line.
* [`lineDashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderArgs/lineDashArray.html) - used to change the dash array size.
* [`seriesName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderArgs/seriesName.html) - Specifies the series name.
* [`index`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderArgs/index.html) - Specifies the current series index
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderArgs/dataPoints.html) - Specifies the current datapoints.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body:Center(
            child: SfCartesianChart(
              onIndicatorRender: (IndicatorRenderArgs args)
              {
                if(args.index==0) 
                {
                  args.indicatorname='changed1';
                  args.signalLineColor=Colors.green;
                  args.signalLineWidth=6.0;
                }
              }
            )
        )
      );
    }
    
{% endhighlight %}

## onTrendlineRender

Triggers when the trendline gets rendered. Trendline properties like color,opacity can be customized using trendlineRender Callbacks. The [`onTrendlineRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrendlineRenderArgs-class.html) Callback contains the following arguments.

* [`trendlineIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrendlineRenderArgs/trendlineIndex.html) - Specifies the  index of the trendlines.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrendlineRenderArgs/opacity.html) - Specifies the opacity of the trendlines.
* [`seriesName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrendlineRenderArgs/seriesName.html) - Specifies the series name of the trendline.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrendlineRenderArgs/color.html) - Specifies the color of the trendline.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrendlineRenderArgs/seriesIndex.html) - Specifies the seriesIndex.
* [`data`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrendlineRenderArgs/data.html) - Specifies the data points of the series.
* [`trendlineName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrendlineRenderArgs/trendlineName.html) - Specifies the name of the trendline.
* [`intercept`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrendlineRenderArgs/intercept.html) - Specifies the intercept value of the trendline.
* [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrendlineRenderArgs/dashArray.html) - Specifies and set the dashArray for trendlines.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
          onTrendlineRender: (TrendlineRenderArgs args) {
            args.color = Colors.greenAccent;
            args.opacity = 0.18;
            args.dashArray = <double>[5, 3];
           }
        )
      )
    );
  }

{% endhighlight %}

## onRendererCreated

Triggers when the series renderer is created. Using this callback, able to get the `ChartSeriesController` instance, which is used to access the public methods in the series.

{% highlight dart %}

  Widget build(BuildContext context) {

    //Initialize the series controller
    ChartSeriesController _chartSeriesController;

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
        child: RaisedButton(
          onPressed: () {
            //Removed a point from data source
            chartData.removeAt(0);
            //Added a point to the data source
            chartData.add(ChartData(3,23));
            //Here accessed the public method of the series.
            _chartSeriesController.updateDataSource(
              addedDataIndexes: <int>[chartData.length -1],
              removedDataIndexes: <int>[0],
            );
          }
        )
      )
    ]
  );
 }

{% endhighlight %}

## onChartTouchInteractionDown

Triggers when touched or clicked on the chart area. You can get the position of the touched region using this callback.

The callback contains the following argument:

* [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) - used to get the position of the touch interaction.

{% highlight dart %}

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

Triggers when tapped or clicked on the chart area. You can get the position of the taped region using this callback.

The callback contains the following argument:

* [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) - used to get the position of the touch interaction.

{% highlight dart %}

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

Triggers when touched or clicked and moved on the chart area. You can get the position of the moving region using this callback.

The callback contains the following argument:

* [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) - used to get the position of the touch interaction.

{% highlight dart %}

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
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/seriesIndex.html) - Specifies the series index of the tapped data label
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/pointIndex.html) - Specifies the point index of the tapped data label.
* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/text.html) - Specifies the content of the tapped data label.
* [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/dataLabelSettings.html) - to get the data label customization options specified in that particular series.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/viewportPointIndex.html) - to get the viewport index value of the tapped data label.


N> This callback will not be called, when the builder is specified for data label (data label template). For this case, custom widget specified in the [`DataLabelSettings.builder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/builder.html) property can be wrapped using the [`GestureDetector`](https://api.flutter.dev/flutter/widgets/GestureDetector-class.html) and this functionality can be achieved in the application level.

{% highlight dart %}

    Widget build(BuildContext context) {
      return Container(
          child: SfCartesianChart(
              onDatalabelTapped: (DataLabelTapArgs args) {
                print(args.seriesIndex);                 
              },
              series: <ChartSeries<Sample, DateTime>>[
                  LineSeries<Sample, DateTime>(
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



## See Also

* [Customize the tooltip using its callback event](https://www.syncfusion.com/kb/11507/how-to-customize-the-tooltip-using-callback-events-sfcartesianchart).
* [Customize the axis labels using its callback event](https://www.syncfusion.com/kb/11678/how-to-customize-the-axis-labels-using-callback-events-sfcartesianchart).
* [Customize the data labels using its callback event](https://www.syncfusion.com/kb/11679/how-to-customize-data-labels-using-callback-events-sfcartesianchart).
* [Disabling trackball tooltip for particular series using its callback event](https://www.syncfusion.com/kb/11638/how-to-disable-trackball-tooltip-for-particular-series-in-cartesian-charts-sfcartesianchart).
* [To Synchronize panning in multiple charts](https://www.syncfusion.com/kb/11533/how-to-synchronize-panning-in-multiple-charts-sfcartesianchart).