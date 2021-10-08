---
layout: post
title: Methods in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about available Methods of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Methods in Flutter Cartesian Charts (SfCartesianChart)

## Methods in tooltipBehavior

### Show method in tooltipBehavior

The [`show`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/show.html) method is used to activate the tooltip at the specified x and y point values.

{% highlight dart %} 

    late SfCartesianChart chart;
    late TooltipBehavior _tooltipBehavior;
    @override
    void initState(){
      _tooltipBehavior = TooltipBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {

      final List<ChartData> chartData = [
          ChartData(10, 17),
          ChartData(20, 34),
          // Add the required data
      ];
      chart = SfCartesianChart(
        tooltipBehavior: _tooltipBehavior,
          series: <CartesianSeries>[
            ColumnSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
        ]
      );

      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Show'),
                onPressed: show
              ),s
              Container(child: chart)
            ]
          )
        )
      );
    }

    void show() {
        _tooltipBehavior.show(20, 34);
    }

    class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }

{% endhighlight %}

### showByIndex method in tooltipBehavior

The [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByIndex.html) method is used to display the tooltip at the specified series and point index.

The below mentioned arguments are given to the [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByIndex.html) method:

[`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipValue/seriesIndex.html) - index of the series for which the pointIndex is specified.

[`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipValue/pointIndex.html)  - index of the point for which the tooltip should be shown.


{% highlight dart %} 

    late SfCartesianChart chart;
    late TooltipBehavior _tooltipBehavior;
    
    @override
    void initState(){
      _tooltipBehavior = TooltipBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {

      final List<ChartData> chartData = [
          ChartData(10, 17),
          ChartData(20, 34),
          // Add the required data
      ];
      chart = SfCartesianChart(
        tooltipBehavior: _tooltipBehavior,
          series: <CartesianSeries>[
            ColumnSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
        ]
      );

      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Show'),
                onPressed:(){
                    _tooltipBehavior.showByIndex(0,1);
                }
              ),
              Container(child: chart)
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

### showByPixel method in tooltipBehavior

The [`showByPixel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByPixel.html) method is used to display the tooltip at the specified x and y-positions.

x & y - logical pixel values to position the tooltip.

{% highlight dart %} 

    late SfCartesianChart chart;
    late TooltipBehavior _tooltipBehavior;
    
    @override
    void initState(){
      _tooltipBehavior = TooltipBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {

      final List<ChartData> chartData = [
          ChartData(10, 17),
          ChartData(20, 34),
          // Add the required data
      ];
      chart = SfCartesianChart(
        tooltipBehavior: _tooltipBehavior,
          series: <CartesianSeries>[
            ColumnSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
        ]
      );

      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Show'),
                onPressed:(){
                  _tooltipBehavior.showByPixel(230.0,470.0);
                }
              ),
              Container(child: chart)
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

### Hide method in tooltipBehavior

The [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/hide.html) method is used to hide the displaying tooltip programmatically.

{% highlight dart %} 

    late SfCartesianChart chart;
    late TooltipBehavior _tooltipBehavior;
    
    @override
    void initState(){
      _tooltipBehavior = TooltipBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = [
          ChartData(10, 17),
          ChartData(20, 34)
      // Add the required data  
      ];
      chart = SfCartesianChart(
        tooltipBehavior: _tooltipBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
          ]
      );

      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Hide'),
                onPressed: hide
              ),
              Container(child: chart)
            ]
          )
        )
      );
    }

    void hide(){
      _tooltipBehavior.hide();
    }

     class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }

{% endhighlight %}

## Methods in trackballBehavior

### Show method in trackballBehavior

The [`show`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/show.html) method is used to activate the trackball at the specified location.

{% highlight dart %} 

  late SfCartesianChart chart;
  late TrackballBehavior _trackballBehavior;

  @override
  void initState() {
    _trackballBehavior = TrackballBehavior(enable: true);
    super.initState();
  }

  @override
  Widget build(BuildContext context) {

    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34)
      // Add the required data
    ];

    chart = SfCartesianChart(
        trackballBehavior: _trackballBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
        ]);

    return Scaffold(
      body: Center(
        child: Column(
          children: <Widget>[
             TextButton(
              child: Text('Show'),
              onPressed: () {
                      _trackballBehavior.show(10, 17);
              }
             ),
             Container(child: chart)
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

### showByIndex  method in trackballBehavior

The [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/showByIndex.html) method is used to activate the trackball at the specified point index.

[`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballDetails/pointIndex.html) - index of the point for which the trackball must be shown.

{% highlight dart %} 

    late SfCartesianChart chart;
    late TrackballBehavior _trackballBehavior;
    
    @override
    void initState(){
      _trackballBehavior = TrackballBehavior(enable: true);
      super.initState();
    }
  
    @override
    Widget build(BuildContext context) {
    
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34)
        // Add the required data
      ];
      
      chart = SfCartesianChart(
        trackballBehavior: _trackballBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
        ]
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Show'),
                onPressed: () {
                  _trackballBehavior.showByIndex(3);
                },
              ),
              Container(child: chart)
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

### Hide method in trackballBehavior

The [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/hide.html) method is used to hide the displaying trackball programmatically.

{% highlight dart %} 

    late SfCartesianChart chart;
    late TrackballBehavior _trackballBehavior;
    
    @override
    void initState(){
      _trackballBehavior = TrackballBehavior(enable: true);
      super.initState();
    }
  
    @override
    Widget build(BuildContext context) {
    
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
        // Add the required data
      ];
      
      chart = SfCartesianChart(
        trackballBehavior: _trackballBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
        ],
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Hide'),
                onPressed: hide
              ),
              Container(child: chart)
            ]
          )
        )
      );
    }

    void hide() {
        _trackballBehavior.hide();
    }

     class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }
{% endhighlight %}

## Methods in crosshairBehavior

### Show method in crosshairBehavior

The [`show`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/show.html) method is used to activate the crosshair at the specified location.

{% highlight dart %} 

    late SfCartesianChart chart;
    late CrosshairBehavior _crosshairBehavior;

    @override
    void initState(){
      _crosshairBehavior = CrosshairBehavior(enable: true);
      super.initState();
    }
    
    @override
    Widget build(BuildContext context) {
      // Add the required data 
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
      ];

      chart = SfCartesianChart(
        crosshairBehavior: _crosshairBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y
            )
        ]
      );

      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Show'),
                onPressed: ()
                {
                  _crosshairBehavior.show(121, 164);
                }
              ),
              Container(child: chart)
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

### showByIndex method in crosshairBehavior

The [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/showByIndex.html) method is used to activate the crosshair at the specified point index.

[`pointIndex`] - index of point at which the crosshair needs to be shown.

{% highlight dart %} 

    late SfCartesianChart chart;
    late CrosshairBehavior _crosshairBehavior;

    @override
    void initState(){
      _crosshairBehavior = CrosshairBehavior(enable: true);
      super.initState();
    }
    
    @override
    Widget build(BuildContext context) {
      // Add the required data 
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
      ];
      chart = SfCartesianChart(
        crosshairBehavior: _crosshairBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y
            )
        ]
      );

      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Show'),
                onPressed: ()
                {
                  _crosshairBehavior.showByIndex(2);
                }
              ),
              Container(child: chart)
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

### Hide method in crosshairBehavior

The [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/hide.html) method is used to hide the displaying crosshair programmatically.

{% highlight dart %} 

    late SfCartesianChart chart;
    late CrosshairBehavior _crosshairBehavior;

    @override
    void initState(){
      _crosshairBehavior = CrosshairBehavior(enable: true);
      super.initState();
    }
  
    @override
    Widget build(BuildContext context) {  
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34)
      // Add the required data  
      ];
      chart = SfCartesianChart(
        crosshairBehavior: _crosshairBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
        ]
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Hide'),
                onPressed: hide
              ),
              Container(child: chart)
            ]
          )
        )
      );
    }

    void hide() {
        _crosshairBehavior.hide();
    }

     class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }


{% endhighlight %}

## Methods in selectionBehavior

### SelectDataPoints method in selectionBehavior

The [`selectDataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectDataPoints.html) method is used to select the data point programmatically. The required arguments are listed below.

* `pointIndex` - index of the point which needs to be selected.
* `seriesIndex` - index of the series for which the pointIndex is specified and this is an optional argument. By default it will be considered as 0.

>**NOTE**:The [`enableMultiSelection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/enableMultiSelection.html) and [`selectionType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/selectionType.html) are also applicable for this but, it is based on their API values specified in the chart.

{% highlight dart %}

    late SfCartesianChart chart;
    late SelectionBehavior _selectionBehavior;

    @override
    void initState(){
      _selectionBehavior = SelectionBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
    
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34)
        // Add the required data
      ];

      chart = SfCartesianChart(
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
              selectionBehavior: _selectionBehavior
          )
        ]
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Select'),
                onPressed: select
              ),
              Container(child: chart)
            ]
          )
        )
      );
    }

    void select() {
        _selectionBehavior.selectDataPoints(1, 0);
    }

     class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }


{% endhighlight %}

## Methods in zoomPanBehavior

### ZoomIn method in zoomPanBehavior

The [`zoomIn`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomIn.html) method is used to increase the magnification of the plot area.

{% highlight dart %}

    late SfCartesianChart chart;
    late ZoomPanBehavior _zoomPanBehavior;

    @override
    void initState(){
      _zoomPanBehavior =  ZoomPanBehavior(
        enableSelectionZooming: true,
        enableDoubleTapZooming: true,
        enablePinching: true,
        enablePanning: true
      );
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34)
        //add the required data
      ];
      
      chart = SfCartesianChart(
        zoomPanBehavior: _zoomPanBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y
          )
        ]
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Zoom'),
                onPressed: zoom
              ),
              Container(child: chart)
            ]
          )
        )
      );
    }

    void zoom() {
        _zoomPanBehavior.zoomIn();
    }

     class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }


{% endhighlight %}

### ZoomOut method in zoomPanBehavior

The [`zoomOut`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomOut.html) method is used to decrease the magnification of the plot area.

{% highlight dart %}

    late SfCartesianChart chart;
    late ZoomPanBehavior _zoomPanBehavior;

    @override
    void initState(){
      _zoomPanBehavior =  ZoomPanBehavior(
        enableSelectionZooming: true,
        enableDoubleTapZooming: true,
        enablePinching: true,
        enablePanning: true
      );
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
    
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34)
        //add the required data
      ];
      
      chart = SfCartesianChart(
        zoomPanBehavior: _zoomPanBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y
          )
        ]
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Zoom'),
                onPressed: zoom
              ),
              Container(child: chart)
            ]
          )
        )
      );
    }

    void zoom() {
        _zoomPanBehavior.zoomOut();
    }

     class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }


{% endhighlight %}

### zoomByFactor method in zoomPanBehavior

The [`zoomByFactor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomByFactor.html) method changes the zoom level using zoom factor. Here, you can pass the zoom factor of an axis to magnify the plot area. The value ranges from 0 to 1.

{% highlight dart %}

    late SfCartesianChart chart;
    late ZoomPanBehavior _zoomPanBehavior;

    @override
    void initState(){
      _zoomPanBehavior =  ZoomPanBehavior(
        enableSelectionZooming: true,
        enableDoubleTapZooming: true,
        enablePinching: true,
        enablePanning: true
      );
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
    
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
        //add the required data
      ];
      chart = SfCartesianChart(
        zoomPanBehavior: _zoomPanBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y
          )
        ]
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Zoom'),
                onPressed: zoom
              ),
              Container(child: chart)
            ]
          )
        )
      );
    }

    void zoom() {
        _zoomPanBehavior.zoomByFactor(0.5);
    }

     class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }


{% endhighlight %}

### ZoomByRect method in zoomPanBehavior

The [`zoomByRect`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomByRect.html) method zooms the chart for a given rectangle value. Here, you can pass the rectangle with the left, right, top, and bottom values, using which the selection zooming will be performed.

{% highlight dart %}

    late SfCartesianChart chart;
    late ZoomPanBehavior _zoomPanBehavior;

    @override
    void initState(){
      _zoomPanBehavior =  ZoomPanBehavior(
        enableSelectionZooming: true,
        enableDoubleTapZooming: true,
        enablePinching: true,
        enablePanning: true
      );
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
    
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
        //add the required data
      ];
      
      chart = SfCartesianChart(
        zoomPanBehavior: _zoomPanBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y
          )
        ]
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Zoom'),
                onPressed: zoom
              ),
              Container(child: chart)
            ]
          )
        )
      );
    }

    void zoom() {
        _zoomPanBehavior.zoomByRect(const Rect.fromLTRB(200, 300, 300, 400));
    }

     class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }


{% endhighlight %}

### ZoomToSingleAxis method in zoomPanBehavior

The [`zoomToSingleAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomToSingleAxis.html) method changes the zoom level of an appropriate axis. Here, you need to pass axis, zoom factor, zoom position of the zoom level that needs to be modified.

{% highlight dart %}

    late SfCartesianChart chart;
    late ZoomPanBehavior _zoomPanBehavior;

    @override
    void initState(){
      _zoomPanBehavior =  ZoomPanBehavior(
        enableSelectionZooming: true,
        enableDoubleTapZooming: true,
        enablePinching: true,
        enablePanning: true
      );
      super.initState();
    }

    late NumericAxis xAxis;

    @override
    Widget build(BuildContext context) {
    
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
        //add required data
      ];
      xAxis = NumericAxis();
      chart = SfCartesianChart(
        zoomPanBehavior: _zoomPanBehavior,
        primaryXAxis: xAxis,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y
          )
        ]
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Zoom'),
                onPressed: zoom
              ),
              Container(child: chart)
            ]
          )
        )
      );
    }

    void zoom() {
        final double zoomPosition = 0.5;
        final double zoomFactor = 0.4;
        _zoomPanBehavior.zoomToSingleAxis(xAxis,zoomPosition,zoomFactor);
    }

     class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }


{% endhighlight %}

### PanToDirection method in zoomPanBehavior

The [`panToDirection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/panToDirection.html) method pans the plot area for given left, right, top, and bottom directions. To perform this action, the plot area needs to be in zoomed state.

{% highlight dart %}

    late SfCartesianChart chart;
    late NumericAxis xAxis;
    late ZoomPanBehavior _zoomPanBehavior;

    @override
    void initState(){
      _zoomPanBehavior =  ZoomPanBehavior(
        enableSelectionZooming: true,
        enableDoubleTapZooming: true,
        enablePinching: true,
        enablePanning: true
      );
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
    
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
        //add required data
      ];

      xAxis = NumericAxis();
      chart = SfCartesianChart(
        zoomPanBehavior: _zoomPanBehavior,
        primaryXAxis: xAxis,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y
          )
        ]
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Pan'),
                onPressed: pan
              ),
              Container(child: chart)
            ]
          )
        )
      );
    }

    void pan() {
        //In similar way, specify other directions like bottom, left and right
        _zoomPanBehavior.panToDirection('top'); 
    }

     class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }

{% endhighlight %}

### Reset method in zoomPanBehavior

The [`reset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/reset.html) method returns the plot area back to its original position after zooming..

{% highlight dart %}

    late SfCartesianChart chart;
    late ZoomPanBehavior _zoomPanBehavior;

    @override
    void initState(){
      _zoomPanBehavior =  ZoomPanBehavior(
        enableSelectionZooming: true,
        enableDoubleTapZooming: true,
        enablePinching: true,
        enablePanning: true
      );
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
    
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34)
        //add the required data
      ];
      
      chart = SfCartesianChart(
        zoomPanBehavior: _zoomPanBehavior,
        series: <CartesianSeries>[
          ColumnSeries<ChartData, double>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y
          )
        ]
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              TextButton(
                child: Text('Zoom'),
                onPressed: zoom
              ),
              Container(child: chart)
            ]
          )
        )
      );
    }

    void zoom() {
      _zoomPanBehavior.reset();
    }

     class ChartData {
        ChartData(this.x, this.y);
        final double x;
        final double? y;
      }


{% endhighlight %}

## UpdateDataSource

Used to process only the newly added, updated, and removed data points in a series, instead of processing all the data points.

To re-render the chart with modified data points, setState() will be called. This will render the chart from scratch and thus, the app’s performance will be degraded on continuous updates.

To overcome this problem, the [`updateDataSource`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeriesController/updateDataSource.html) method can be called by passing updated data points indexes. The chart widget will process only that point and skip various steps like bounds calculation,
old data points processing, etc. Thus, this will improve the app’s performance.

The following are the arguments of this method.
* `addedDataIndexes` - `List<int>` type - Indexes of newly added data points in the existing series.
* `removedDataIndexes` - `List<int>` type - Indexes of removed data points in the existing series.
 * `updatedDataIndexes` - `List<int>` type - Indexes of updated data points in the existing series.
 * `addedDataIndex` - `int` type - Index of newly added data point in the existing series.
 * `removedDataIndex` - `int` type - Index of removed data point in the existing series.
* `updatedDataIndex` - `int` type - Index of updated data point in the existing series.


{% highlight dart %}

Widget build(BuildContext context) {

    //Initialize the series controller
    ChartSeriesController? _chartSeriesController;

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
                //Passed the necessary arguments to the updateDataSource method. Here passed the added and removed data point indexes.
                _chartSeriesController?.updateDataSource(
                  addedDataIndexes: <int>[chartData.length - 1],
                  removedDataIndexes: <int>[0],
                );
              }, child: Text('Add a point'),
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

#### See Also

*[Rendering real time live charts using updateDataSource method](https://www.syncfusion.com/kb/12316/how-to-create-flutter-real-time-charts-using-the-cartesian-charts-widget-sfcartesianchart).

## PixelToPoint 

Converts logical pixel value to the data point value.
  
The [`pixelToPoint`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeriesController/pixelToPoint.html) method takes logical pixel value as input and returns a chart data point.
  
Since this method is in the series controller, x and y-axis associated with this particular series will be considering for conversion value.

{% highlight dart %}

        //Initialize the series controller
    ChartSeriesController? seriesController;

    @override
    Widget build(BuildContext context) {
      return Container(
            child: SfCartesianChart(
             series: <CartesianSeries<ChartSampleData, num>>[
               LineSeries<ChartSampleData, num>(
                 onRendererCreated: (ChartSeriesController controller) {
                   seriesController = controller;
                 },
               )
             ],
             onChartTouchInteractionUp: (ChartTouchInteractionArgs args) {
               final Offset value = Offset(args.position.dx, args.position.dy);
               CartesianChartPoint<dynamic> chartpoint =
                 seriesController!.pixelToPoint(value);
               print('X point: ${chartpoint.x}');
               print('Y point: ${chartpoint.y}');
           }
         )
       );
    }

     class ChartSampleData{
        ChartSampleData(this.x, this.y);
        final num x;
        final double? y;
      }


{% endhighlight %}

## PointToPixel 
Converts chart data point value to logical pixel value.
  
The [`pointToPixel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeriesController/pointToPixel.html) method takes chart data point value as input and returns logical pixel value.
  
Since this method is in the series controller, x and y-axis associated with this particular series will be considering for conversion value.
  
>**NOTE**:This method is only applicable for Cartesian chart, not for the circular, pyramid,
and funnel charts.
  
{% highlight dart %}


    //Initialize the series controller
    ChartSeriesController? seriesController;

    @override 
    Widget build(BuildContext context) {
      return Container(
          child: SfCartesianChart(
              series: <CartesianSeries<ChartSampleData, num>>[
                ColumnSeries<ChartSampleData, num>(
                  onRendererCreated: (ChartSeriesController controller) {
                    seriesController = controller;
                  },
                )
              ],
              onPointTapped: (PointTapArgs args) {
                  CartesianChartPoint<dynamic> chartPoint =
                      CartesianChartPoint<dynamic>(data[args.pointIndex].x,
                          data[args.pointIndex].y);
                  Offset pointLocation = seriesController!.pointToPixel(chartPoint);
                  print('X location: ${pointLocation.x}');
                  print('Y location: ${pointLocation.y}');
              },
            )
      );
    }

    class ChartSampleData{
        ChartSampleData(this.x, this.y);
        final num x;
        final double? y;
      }

{% endhighlight %}

## See Also

* [Show or hide tooltip dynamically in Cartesian chart](https://www.syncfusion.com/kb/11490/how-to-show-or-hide-the-tooltip-dynamically-in-cartesian-charts-sfcartesianchart).
* [Show or hide trackball dynamically in Cartesian chart](https://www.syncfusion.com/kb/11489/how-to-show-or-hide-trackball-dynamically-in-cartesian-charts-sfcartesianchart).
* [Show or hide crosshair dynamically in Cartesian chart](https://www.syncfusion.com/kb/11488/how-to-show-or-hide-crosshair-dynamically-in-cartesian-charts-sfcartesianchart).

>**NOTE**:`chartData` in the above code snippets is a class type list and holds the data for binding to the chart series. Refer [Bind data source](https://help.syncfusion.com/flutter/cartesian-charts/getting-started#bind-data-source) topic for more details.
