---
layout: post
title: Syncfusion Flutter Chart Public Methods
description: Learn what are all the public methods available in Flutter Chart.
platform: flutter
control: Chart
documentation: ug
---

# Cartesian chart methods

## Methods in tooltipBehavior

### Show method in tooltipBehavior

The [`show`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/show.html) method is used to activate the tooltip at the specified location.

{% highlight dart %} 

    SfCartesianChart chart;
    TooltipBehavior tooltip;

    @override
    Widget build(BuildContext context) {

    final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
        // Add the required data
    ];
    
    tooltip = TooltipBehavior (enable: true);

    chart = SfCartesianChart(
      tooltipBehavior: tooltip,
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
            FlatButton(
              child: Text('Show'),
              onPressed: show
            ),
            Container(child: chart)
          ]
        )
      )
    );
  }

    void show() {
        tooltip.show(121,164);
      }

    void hide(){
        tooltip.hide();
    }

  {% endhighlight %}

### showByIndex method in tooltipBehavior

The [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByIndex.html) method is used to Displays the tooltip at the specified series and point index.

The below mentioned arguments are given to the [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByIndex.html) method:

[`seriesIndex`]() - index of the series for which the pointIndex is specified.

[`pointIndex`]() - index of the point for which the tooltip should be shown.


{% highlight dart %} 

    SfCartesianChart chart;
    TooltipBehavior tooltip;

    @override
    Widget build(BuildContext context) {

    final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
        // Add the required data
    ];
    
    tooltip = TooltipBehavior (enable: true);

    chart = SfCartesianChart(
      tooltipBehavior: tooltip,
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
            FlatButton(
              child: Text('Show'),
              onPressed:(){
                   tooltip.showByIndex(0,1);
              }
            ),
            Container(child: chart)
          ]
        )
      )
    );
  }

    void hide(){
        tooltip.hide();
    }

  {% endhighlight %}

### showByPixel method in tooltipBehavior

The [`showByPixel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByPixel.html) method is used to Displays the tooltip at the specified x and y-positions.

x & y - logical pixel values to position the tooltip.

{% highlight dart %} 

    SfCartesianChart chart;
    TooltipBehavior tooltip;

    @override
    Widget build(BuildContext context) {

    final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
        // Add the required data
    ];
    
    tooltip = TooltipBehavior (enable: true);

    chart = SfCartesianChart(
      tooltipBehavior: tooltip,
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
            FlatButton(
              child: Text('Show'),
              onPressed:(){
                tooltip.showByPixel(230.0,470.0);
              }
            ),
            Container(child: chart)
          ]
        )
      )
    );
   }

    void hide(){
        tooltip.hide();
    }

  {% endhighlight %}

### Hide method in tooltipBehavior

The [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/hide.html) method is used to hide the displaying tooltip programmatically.

{% highlight dart %} 

    SfCartesianChart chart;
    TooltipBehavior tooltip;

    @override
    Widget build(BuildContext context) {
    final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34)
    // Add the required data  
    ];
    
    tooltip = TooltipBehavior (enable: true);

    chart = SfCartesianChart(
      tooltipBehavior: tooltip,
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
            FlatButton(
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
        tooltip.hide();
    }

  {% endhighlight %}

## Methods in trackballBehavior

### Show method in trackballBehavior

The [`show`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/show.html) method is used to activate the trackball at the specified location.

{% highlight dart %} 

    SfCartesianChart chart;
    TrackballBehavior trackball;
  
    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34)
      // Add the required data
    ];
    
    trackball = TrackballBehavior(enable: true);
    
    chart = SfCartesianChart(
      trackballBehavior: trackball,
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
            FlatButton(
              child: Text('Show'),
              onPressed:() {
        trackball.show(121, 164);
            ),
            Container(child: chart)
          ]
        )
      )
    );
  }

  {% endhighlight %}

### showByIndex  method in trackballBehavior

The [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/showByIndex.html) method is used to activate the trackball at the specified point index.

[`pointIndex`]()- index of the point for which the trackball must be shown

{% highlight dart %} 

    SfCartesianChart chart;
    TrackballBehavior trackball;
  
    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34)
      // Add the required data
    ];
    
    trackball = TrackballBehavior(enable: true);
    
    chart = SfCartesianChart(
      trackballBehavior: trackball,
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
            FlatButton(
              child: Text('Show'),
              onPressed: (){
        trackball.showByIndex(3);
    },
            ),
            Container(child: chart)
          ]
        )
      )
    );
  }

  {% endhighlight %}

### Hide method in trackballBehavior

The [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/hide.html) method is used to hide the displaying trackball programmatically.

{% highlight dart %} 

    SfCartesianChart chart;
    TrackballBehavior trackball;
  
    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34),
      // Add the required data
    ];
    
    trackball = TrackballBehavior(enable: true);
    
    chart = SfCartesianChart(
      trackballBehavior: trackball,
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
            FlatButton(
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
        trackball.hide();
    }

  {% endhighlight %}

## Methods in crosshairBehavior

### Show method in crosshairBehavior

The [`show`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/show.html) method is used to activate the crosshair at the specified location.

{% highlight dart %} 

    SfCartesianChart chart;
    CrosshairBehavior crosshair;
    
    @override
    Widget build(BuildContext context) {
     // Add the required data 
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34),
    ];

    crosshair = CrosshairBehavior(enable: true);
    
    chart = SfCartesianChart(
      crosshairBehavior: crosshair,
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
            FlatButton(
              child: Text('Show'),
              onPressed: ()
              {
                crosshair.show(121, 164);
              }
            ),
            Container(child: chart)
          ]
        )
      )
    );
  }

  {% endhighlight %}

### showByIndex method in crosshairBehavior

The [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/showByIndex.html) method is used to activate the crosshair at the specified point index.

[`pointIndex`]() - index of point at which the crosshair needs to be shown.

{% highlight dart %} 

    SfCartesianChart chart;
    CrosshairBehavior crosshair;
    
    @override
    Widget build(BuildContext context) {
     // Add the required data 
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34),
    ];

    crosshair = CrosshairBehavior(enable: true);
    
    chart = SfCartesianChart(
      crosshairBehavior: crosshair,
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
            FlatButton(
              child: Text('Show'),
              onPressed: ()
              {
                 crosshair.showByIndex(2);
              }
            ),
            Container(child: chart)
          ]
        )
      )
    );
  }

  {% endhighlight %}


### Hide method in crosshairBehavior

The [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/hide.html) method is used to hide the displaying crosshair programmatically.

{% highlight dart %} 

    SfCartesianChart chart;
    CrosshairBehavior crosshair;
  
    @override
    Widget build(BuildContext context) {  
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34)
    // Add the required data  
    ];
    
    crosshair = CrosshairBehavior(enable: true);
    
    chart = SfCartesianChart(
      crosshairBehavior: crosshair,
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
            FlatButton(
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
        crosshair.hide();
    }

  {% endhighlight %}

## Methods in selectionSettings

### SelectionIndex method in selectionSettings

The [`selectionIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionSettings/selectionIndex.html) method is used to select the data point programmatically. The required arguments are listed below.

* pointIndex - specifies the point index value.
* seriesIndex - specifies the series index value.
* selectionType - specifies the [`SelectionType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionType-class.html) and this is an optional parameter. 
* multiSelect - bool property specifies the multiple selection and this is an optional parameter.

{% highlight dart %}

    SfCartesianChart chart;
    SelectionSettings selection;

    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      hartData(10, 17),
      ChartData(20, 34)
      // Add the required data
    ];

    selection = SelectionSettings(enable: true);
    
    chart = SfCartesianChart(
      series: <CartesianSeries>[
        ColumnSeries<ChartData, double>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y,
            selectionSettings: selection
        )
      ]
    );
    
    return Scaffold(
      body: Center(
        child: Column(
          children: <Widget>[
            FlatButton(
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
        selection.selectionIndex(1, 0);
    }

{% endhighlight %}

## Methods in zoomPanBehavior

### ZoomIn method in zoomPanBehavior

The [`zoomIn`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomIn.html) method is used to increases the magnification of the plot area.

{% highlight dart %}

    SfCartesianChart chart;
    ZoomPanBehavior zooming;

    @override
    Widget build(BuildContext context) {
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34)
      //add the required data
    ];
    
    zooming = ZoomPanBehavior(
      enableSelectionZooming: true,
      enableDoubleTapZooming: true,
      enablePinching: true,
      enablePanning: true
    );
    
    chart = SfCartesianChart(
      zoomPanBehavior: zooming,
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
            FlatButton(
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
        zooming.zoomIn();
    }

{% endhighlight %}

### ZoomOut method in zoomPanBehavior

The [`zoomOut`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomOut.html) method is used to decreases the magnification of the plot area.

{% highlight dart %}

    SfCartesianChart chart;
    ZoomPanBehavior zooming;

    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34)
      //add the required data
    ];
    
    zooming = ZoomPanBehavior(
        enableSelectionZooming: true,
        enableDoubleTapZooming: true,
        enablePinching: true,
        enablePanning: true
    );
    
    chart = SfCartesianChart(
      zoomPanBehavior: zooming,
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
            FlatButton(
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
        zooming.zoomOut();
    }

{% endhighlight %}

### zoomByFactor method in zoomPanBehavior

The [`zoomByFactor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomByFactor.html) method changes the zoom level using zoom factor. Here, you can pass the zoom factor of an axis to magnify the plot area. The value ranges from 0 to 1.

{% highlight dart %}

    SfCartesianChart chart;
    ZoomPanBehavior zooming;

    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34),
      //add the required data
    ];
    
    zooming = ZoomPanBehavior(
        enableSelectionZooming: true,
        enableDoubleTapZooming: true,
        enablePinching: true,
        enablePanning: true
    );
    
    chart = SfCartesianChart(
      zoomPanBehavior: zooming,
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
            FlatButton(
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
        zooming.zoomByFactor(0.5);
    }

{% endhighlight %}

### ZoomByRect method in zoomPanBehavior

The [`zoomByRect`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomByRect.html) method zooms the chart for a given rectangle value. Here, you can pass the rectangle with the left, right, top, and bottom values, using which the selection zooming will be performed.

{% highlight dart %}

    SfCartesianChart chart;
    ZoomPanBehavior zooming;

    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34),
      //add the required data
    ];
    
    zooming = ZoomPanBehavior(
        enableSelectionZooming: true,
        enableDoubleTapZooming: true,
        enablePinching: true,
        enablePanning: true);
    
    chart = SfCartesianChart(
      zoomPanBehavior: zooming,
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
            FlatButton(
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
        zooming.zoomByRect(const Rect.fromLTRB(200, 300, 300, 400));
    }

{% endhighlight %}

### ZoomToSingleAxis method in zoomPanBehavior

The [`zoomToSingleAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomToSingleAxis.html) method changes the zoom level of an appropriate axis. Here, you need to pass axis, zoom factor, zoom position of the zoom level that needs to be modified.

{% highlight dart %}

    SfCartesianChart chart;
    ZoomPanBehavior zooming;
    NumericAxis xAxis;

    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34),
      //add required data
    ];
    zooming = ZoomPanBehavior(
      enableSelectionZooming: true,
      enableDoubleTapZooming: true,
      enablePinching: true,
      enablePanning: true
    );

    xAxis = NumericAxis();
    chart = SfCartesianChart(
      zoomPanBehavior: zooming,
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
            FlatButton(
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
        zooming.zoomToSingleAxis(xAxis,zoomPosition,zoomFactor);
    }

{% endhighlight %}

### PanToDirection method in zoomPanBehavior

The [`panToDirection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/panToDirection.html) method pans the plot area for given left, right, top, and bottom directions. To perform this action, the plot area needs to be in zoomed state.

{% highlight dart %}

    SfCartesianChart chart;
    ZoomPanBehavior zooming;
    NumericAxis xAxis;

    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34),
      //add required data
    ];
    zooming = ZoomPanBehavior(
        enableSelectionZooming: true,
        enableDoubleTapZooming: true,
        enablePinching: true,
        enablePanning: true
    );

    xAxis = NumericAxis();
    chart = SfCartesianChart(
      zoomPanBehavior: zooming,
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
            FlatButton(
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
        zooming.panToDirection('top'); 
    }

{% endhighlight %}

### Reset method in zoomPanBehavior

The [`reset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/reset.html) method returns the plot area back to its original position after zooming..

{% highlight dart %}

    SfCartesianChart chart;
    ZoomPanBehavior zooming;

    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34)
      //add the required data
    ];
    
    zooming = ZoomPanBehavior(
      enableSelectionZooming: true,
      enableDoubleTapZooming: true,
      enablePinching: true,
      enablePanning: true
    );
    
    chart = SfCartesianChart(
      zoomPanBehavior: zooming,
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
            FlatButton(
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
      zooming.reset();
       }

{% endhighlight %}