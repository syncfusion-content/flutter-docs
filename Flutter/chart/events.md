---
layout: post
title: Syncfusion Flutter Chart Events
description: Learn what are all the events available in Flutter Charts.
platform: flutter
control: Chart
documentation: ug
---

# Events

## Cartesian chart events

### onTooltipRender

Triggers when the tooltip is rendering. Here, you can customize the text, header, x and y-positions. The [`onTooltipRender`]() event contains the following arguments.

* text - specifies the content of the tooltip.
* header - specifies the header content of the tooltip.
* locationX - specifies the x position of tooltip.
* locationY - specifies the y position of tooltip.
* seriesIndex - specifies the current series index.
* dataPoints - holds the data point collection.
* pointIndex - specifies the current point index.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            tooltipBehavior: TooltipBehavior(enable: true),
            onTooltipRender: (TooltipArgs args) {
              args.text = 'Customized Text';
            },
          ),
        )
      );
    }

{% endhighlight %}

### onActualRangeChanged

Triggers when the visible range of an axis is changed, i.e. value changes for minimum, maximum, and interval. Here, you can customize the visible range of an axis. The [`onActualRangeChanged`]() event contains the following arguments.

* axisName - specifies the axis name.
* axis - holds the information about the current axis.
* actualMin - specifies the actual minimum range of an axis.
* actualMax - specifies the actual maximum range of an axis.
* actualInterval - specifies the actual interval of an axis.
* visibleMin - specifies the visible minimum range of an axis.
* visibleMax - specifies the visible maximum range of an axis.
* visibleInterval - specifies the visible interval of an axis. 
* orientation - specifies the current axis orientation.

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

### onAxisLabelRender

Triggers while rendering the axis labels. Text and text styles such as color, font size, and font weight can be customized. The [`onAxisLabelRender`]() event contains the following arguments.

* text - specifies the axis label to be rendered.
* value - specifies the actual value of the current axis label.
* axisName - specifies the axis name.
* orientation - specifies the current axis orientation.
* axis - holds the information about the current axis.
* textStyle – used to change the text color, size, font family, font style, and font weight.

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
      ));
    }

{% endhighlight %}

### onDataLabelRender

Triggers when data label is rendering. Text and text styles such as color, font size, and font weight can be customized. The [`onDataLabelRender`]() event contains the following arguments.

* text - specifies the content of the data label.
* textStyle – used to change the text color, size, font family, font style, and font weight.
* pointIndex - specifies the current point index.
* series - specifies current series.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
          onDataLabelRender:(DataLabelRenderArgs args){
            args.text = 'Data label';
          },
          series: <CartesianSeries>[
            ColumnSeries<ChartData, double>(
              dataLabelSettings: DataLabelSettings(
                isVisible: true
              ),
            ),
          ],
        ),
      ));
    }

{% endhighlight %}

### onLegendItemRender

Triggers when the legend item is rendered. Here, you can customize the legend’s text, and shape.  The [`onLegendItemRender`]() event contains the following arguments.

* text - specifies the content of the legend.
* pointIndex - specifies the current point index that is applicable for circular chart type alone.
* seriesIndex - specifies the current series index.
* legendIconType - specifies the shape of the legend.

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
          },
        ),
      ));
    }

{% endhighlight %}

### onTrackballPositionChanging

Triggers while the trackball position is changed. Here, you can customize the text of the trackball.The [`onTrackballPositionChanging`]() event contains the following argument.

* chartPointInfo - holds the information about the current point.

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
          ),
      ));
    }

{% endhighlight %}

### onCrosshairPositionChanging

Triggers while the crosshair position is changed. Here, you can customize the text and line color of the crosshair.The [`onCrosshairPositionChanging`]() event contains the following arguments.

* text - specifies the crosshair content.
* value - specifies the actual value of the crosshair.
* axisName - specifies the axis name.
* orientation - specifies the current axis orientation.
* axis - holds the information about the current axis.
* lineColor - specifies the line color of the crosshair line.

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
          ),
      ));
    }

{% endhighlight %}

### onZooming

Triggers when the zooming action is in progress. The [`onZooming`]() event contains the following arguments.

* axis - holds the information about the current axis.
* currentZoomPosition - specifies the current zoom position of an axis.
* currentZoomFactor - specifies the current zoom factor of an axis.
* previousZoomPosition - specifies the previous zoom position of an axis.
* previousZoomFactor - specifies the previous zoom factor of an axis.

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
          },
      ));
    }

{% endhighlight %}

### onZoomStart

Triggers when zooming action begins. The [`onZoomStart`]() event contains the following arguments.

* axis - holds the information about the current axis.
* currentZoomPosition - specifies the current zoom position of an axis.
* currentZoomFactor - specifies the current zoom factor of an axis.
* previousZoomPosition - specifies the previous zoom position of an axis.
* previousZoomFactor - specifies the previous zoom factor of an axis.

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
          },
      ));
    }

{% endhighlight %}

### onZoomEnd

Triggers when the zooming action is completed. The [`onZoomEnd`]() event contains the following arguments.

* axis - holds the information about the current axis.
* currentZoomPosition - specifies the current zoom position of an axis.
* currentZoomFactor - specifies the current zoom factor of an axis.
* previousZoomPosition - specifies the previous zoom position of an axis.
* previousZoomFactor - specifies the previous zoom factor of an axis.

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
          },
      ));
    }

{% endhighlight %}

### onZoomReset

Triggers when zoomed state is reset. The  [`onZoomReset`]() event contains the following arguments.

* axis - holds the information about the current axis.
* currentZoomPosition - specifies the current zoom position of an axis.
* currentZoomFactor - specifies the current zoom factor of an axis.
* previousZoomPosition - specifies the previous zoom position of an axis.
* previousZoomFactor - specifies the previous zoom factor of an axis.

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
          },
      ));
    }

{% endhighlight %}

### onPointTapped

Triggers when tapping the series point. The [`onPointTapped`]() event contains the following arguments.

* seriesIndex - specifies the current series index.
* pointIndex - specifies the current point index.
* dataPoints - holds the data point collection.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
           onPointTapped: (PointTapArgs args){
            print(args.seriesIndex);
            print(args.pointIndex);
          },
      ));
    }

{% endhighlight %}

### onAxisLabelTapped

Triggers when tapping the axis label. The  [`onPointTapped`]() event contains the following arguments.

* axis - holds the information about the current axis.
* text - specifies the content of the axis label.
* value - specifies the actual value of the current axis label.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
           onAxisLabelTapped: (AxisLabelTapArgs args) {
            print(args.text);
           },
      ));
    }

{% endhighlight %}

### onLegendTapped

Triggers when tapping the legend item. The  [`onLegendTapped`]() event contains the following arguments.

* seriesIndex - specifies the current series index.
* pointIndex - specifies the current point index that is applicable for circular series.
* series - specifies the current series.


{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCartesianChart(
          onLegendTapped: (LegendTapArgs args) {
            print(args.seriesIndex);
          },
          legend: Legend(isVisible: true),
      ));
    }

{% endhighlight %}

### onSelectionChanged

Triggers while selection changes. Here you can customize the selectedColor, unselectedColor, selectedBorderColor, selectedBorderWidth, unselectedBorderColor, and unselectedBorderWidth properties. The [`onSelectionChanged`]() event contains the following arguments.

* series - specifies current series.
* seriesIndex - specifies the current series index.
* pointIndex - specifies the current point index.
* selectedColor - specifies color of the selected data points or series.
* unselectedColor - specifies color of the unselected data points or series.
* selectedBorderColor - specifies border color of the selected data points or series.
* selectedBorderWidth - specifies border width of the selected data points or series.
* unselectedBorderColor - specifies border color of the unselected data points or series.
* unselectedBorderWidth - specifies border width of the unselected data points or series.

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
              selectionSettings: SelectionSettings(
                enable: true,
              ),
            ),
          ],
      ));
    }

{% endhighlight %}

## Cirular chart events

### onLegendItemRender

Triggers when the legend item is rendered. Here, you can customize the legend’s text, and shape.  The [`onLegendItemRender`]() event contains the following arguments.

* text - specifies the content of the legend.
* pointIndex - specifies the current point index that is applicable for circular chart type alone.
* seriesIndex - specifies the current series index.
* legendIconType - specifies the shape of the legend.

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
          },
        ),
      ));
    }

{% endhighlight %}

### onTooltipRender

Triggers while tooltip is rendered. Here, you can customize the text, header, x and y-positions. The [`onTooltipRender`]() event contains the following arguments.

* text - specifies the content of the tooltip.
* header - specifies the header content of the tooltip.
* locationX - specifies the x position of tooltip.
* locationY - specifies the y position of tooltip.
* seriesIndex - specifies the current series index.
* dataPoints - holds the data point collection.
* pointIndex - specifies the current point index.

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
        ),
      ));
    }

{% endhighlight %}

### onDataLabelRender

Triggers when data label is rendering. Text and text styles such as color, font size, and font weight can be customized. The [`onDataLabelRender`]() event contains the following arguments.

* text - specifies the content of the data label.
* textStyle – used to change the text color, size, font family, font style, and font weight.
* pointIndex - specifies the current point index.
* series - specifies current series.

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
             ),
            ),
          ],
        ),
      ));
    }

{% endhighlight %}

### onPointTapped

Triggers when tapping the series point. The [`onPointTapped`]() event contains the following arguments.

* seriesIndex - specifies the current series index.
* pointIndex - specifies the current point index.
* dataPoints - holds the data point collection.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCircularChart(
           onPointTapped: (PointTapArgs args){
            print(args.seriesIndex);
            print(args.pointIndex);
          },
      ));
    }

{% endhighlight %}

### onLegendTapped

Triggers when tapping the legend item. The [`onLegendTapped`]() event contains the following arguments.

* seriesIndex - specifies the current series index.
* pointIndex - specifies the current point index that is applicable for circular series.
* series - specifies the current series.


{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
    return Scaffold(
      body: Center(
        child: SfCircularChart(
          onLegendTapped: (LegendTapArgs args) {
            print(args.seriesIndex);
          },
          legend: Legend(isVisible: true),
      ));
    }

{% endhighlight %}

### onSelectionChanged

Triggers while selection changes. Here you can customize the selectedColor, unselectedColor, selectedBorderColor, selectedBorderWidth, unselectedBorderColor, and unselectedBorderWidth properties. The [`onSelectionChanged`]() event contains the following arguments.

* series - specifies current series.
* seriesIndex - specifies the current series index.
* pointIndex - specifies the current point index.
* selectedColor - specifies color of the selected data points or series.
* unselectedColor - specifies color of the unselected data points or series.
* selectedBorderColor - specifies border color of the selected data points or series.
* selectedBorderWidth - specifies border width of the selected data points or series.
* unselectedBorderColor - specifies border color of the unselected data points or series.
* unselectedBorderWidth - specifies border width of the unselected data points or series.

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
              selectionSettings: SelectionSettings(
                enable: true,
              ),
            ),
          ],
      ));
    }

{% endhighlight %}