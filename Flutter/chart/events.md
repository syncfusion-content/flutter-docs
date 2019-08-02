---
layout: post
title: Syncfusion Flutter Chart Events
description: What are the events in Essential Flutter Chart
platform: flutter
control: Chart
documentation: ug
---

# Events

## Cartesian events

### onTooltipRender

Occurs while tooltip is rendered. Here, you can customize the text, header, x and y-positions. The arguments of [`onTooltipRender`]() event contains the following information.

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
      ));
    }

{% endhighlight %}

### onActualRangeChanged

Occurs when the visible range of an axis is changed, i.e. value changes for minimum, maximum, and interval. Here, you can customize the visible range of an axis. The arguments of [`onActualRangeChanged`]() event contains the following information.

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
            if(args.axisName == 'primaryYAxis'){
              args.visibleMin = 10;
            }
          },
        ),
      ));
    }

{% endhighlight %}

### onAxisLabelRender

Occurs while rendering the axis labels. Text and text styles such as color, font size, and font weight can be customized. The arguments of [`onAxisLabelRender`]() event contains the following information.

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
          },
        ),
      ));
    }

{% endhighlight %}

### onDataLabelRender

Occurs when data label is rendering. Text and text styles such as color, font size, and font weight can be customized. The arguments of [`onDataLabelRender`]() event contains the following information.

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

Occurs when the legend item is rendered. Here, you can customize the legend’s text, and shape.  The arguments of [`onLegendItemRender`]() event contains the following information.

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

Occurs while the trackball position is changed. Here, you can customize the text of the trackball.The arguments of [`onTrackballPositionChanging`]() event contains the following information.

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

Occurs while the crosshair position is changed. Here, you can customize the text and line color of the crosshair.The arguments of [`onCrosshairPositionChanging`]() event contains the following information.

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

Occurs when the zooming action is in progress. The arguments of [`onZooming`]() event contains the following information.

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

Occurs when zooming action begins. The arguments of [`onZoomStart`]() event contains the following information.

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

Occurs when the zooming action is completed. The arguments of [`onZoomEnd`]() event contains the following information.

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

Occurs when zoomed state is reset. The arguments of [`onZoomReset`]() event contains the following information.

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

Occurs when tapping the series point. The arguments of [`onPointTapped`]() event contains the following information.

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

Occurs when tapping the axis label. The arguments of [`onPointTapped`]() event contains the following information.

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

Occurs when tapping the legend item. The arguments of [`onLegendTapped`]() event contains the following information.

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

Occurs while selection changes. Here you can customize the selectedColor, unselectedColor, selectedBorderColor, selectedBorderWidth, unselectedBorderColor, and unselectedBorderWidth properties. The arguments of [`onSelectionChanged`]() event contains the following information.

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

## Cirular events

### onLegendItemRender

Occurs when the legend item is rendered. Here, you can customize the legend’s text, and shape.  The arguments of [`onLegendItemRender`]() event contains the following information.

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

Occurs while tooltip is rendered. Here, you can customize the text, header, x and y-positions. The arguments of [`onTooltipRender`]() event contains the following information.

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

Occurs when data label is rendering. Text and text styles such as color, font size, and font weight can be customized. The arguments of [`onDataLabelRender`]() event contains the following information.

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

Occurs when tapping the series point. The arguments of [`onPointTapped`]() event contains the following information.

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

Occurs when tapping the legend item. The arguments of [`onLegendTapped`]() event contains the following information.

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

Occurs while selection changes. Here you can customize the selectedColor, unselectedColor, selectedBorderColor, selectedBorderWidth, unselectedBorderColor, and unselectedBorderWidth properties. The arguments of [`onSelectionChanged`]() event contains the following information.

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