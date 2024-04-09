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

{% tabs %}
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
              ),
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
{% endtabs %}

### showByIndex method in tooltipBehavior

The [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByIndex.html) method is used to display the tooltip at the specified series and point index.

The below mentioned arguments are given to the [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByIndex.html) method:

* `seriesIndex` - index of the series for which the pointIndex is specified.

* `pointIndex` - index of the point for which the tooltip should be shown.


{% tabs %}
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
{% endtabs %}

### showByPixel method in tooltipBehavior

The [`showByPixel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByPixel.html) method is used to display the tooltip at the specified x and y-positions.

x & y - logical pixel values to position the tooltip.

{% tabs %}
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
{% endtabs %}

### Hide method in tooltipBehavior

The [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/hide.html) method is used to hide the displaying tooltip programmatically.

{% tabs %}
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
{% endtabs %}

## Methods in trackballBehavior

### Show method in trackballBehavior

The [`show`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/show.html) method is used to activate the trackball at the specified location.

{% tabs %}
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
{% endtabs %}

### showByIndex  method in trackballBehavior

The [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/showByIndex.html) method is used to activate the trackball at the specified point index.

The [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballDetails/pointIndex.html) specifies the index of the trackball point.

{% tabs %}
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
{% endtabs %}

### Hide method in trackballBehavior

The [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/hide.html) method is used to hide the displaying trackball programmatically.

{% tabs %}
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
{% endtabs %}

### Events in trackballBehavior

Provided the following methods for handling pointer and gesture events and allowing customizations for various pointer events such as long-press, tap, double-tap, pointer enter, and exit.

* [`handleEvent`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/handleEvent.html) - Specifies to customize the necessary pointer events.
* [`handleLongPressStart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/handleLongPressStart.html) - Specifies to customize the pointer event when a long-press begins.
* [`handleLongPressMoveUpdate`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/handleLongPressMoveUpdate.html) - Specifies to customize the pointer event during movement after a long-press.
* [`handleLongPressEnd`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/handleLongPressEnd.html) - Specifies to customize the pointer event when the pointer stops contacting the screen after a long-press.
* [`handleTapDown`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/handleTapDown.html) - Specifies to customize the pointer event when a tap has contacted the screen once.
* [`handleTapUp`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/handleTapUp.html) - Specifies to customize the pointer event when it has stopped contacting the screen after a tap.
* [`handleDoubleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/handleDoubleTap.html) - Specifies to customize the pointer event when a tap has contacted the screen twice.
* [`handlePointerEnter`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/handlePointerEnter.html) -Specifies to customize the pointer event when the mouse enter on the screen.
* [`handlePointerExit`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/handlePointerExit.html) - Specifies to customize the pointer event when the mouse exit on the screen.

This following code sample defines how to enable or disable specific pointer events and customize to show trackball in double tap and disabled trackball showing in pointer enter and exit.

{% tabs %}
{% highlight dart %} 

    SfCartesianChart(
      trackballBehavior: CustomTrackball(),
      // Add series.
    );
    
    class CustomTrackball extends TrackballBehavior {
      @override
      bool get enable => true;

      // Disable the behavior of pointer events(move, cancel, hover and up).
      @override
      void handleEvent(PointerEvent event, BoxHitTestEntry entry) {}

      // Disable the behavior of the pointer enter on the screen.
      @override
      void handlePointerEnter(PointerEnterEvent details) {}

      // Disable the behavior of the pointer exit on the screen.
      @override
      void handlePointerExit(PointerExitEvent details) {}

      @override
      void handleDoubleTap(Offset position) {
        if (activationMode == ActivationMode.doubleTap) {
          Offset localPosition = parentBox!.globalToLocal(position);
          show(localPosition.dx, localPosition.dy, 'pixel');
        }
      }
    }

{% endhighlight %}
{% endtabs %}

### onPaint in trackballBehavior

The [`onPaint`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TrackballBehavior/onPaint.html) method is used to customize the label, position, and style of trackball tooltip.

{% tabs %}
{% highlight dart %} 

    SfCartesianChart(
      trackballBehavior: CustomTrackball(),
      // Add series.
    );

    class CustomTrackball extends TrackballBehavior {
      @override
      bool get enable => true;

      @override
      ActivationMode get activationMode => ActivationMode.singleTap;

      Offset? customPosition;

      @override
      void show(x, double y, [String coordinateUnit = 'point']) {
        if (coordinateUnit == 'pixel') {
          customPosition = Offset(x.toDouble(), y);
        }
        super.show(x, y, 'pixel');
      }

      @override
      void onPaint(PaintingContext context, Offset offset,
      SfChartThemeData chartThemeData, ThemeData themeData) {
        _drawCustomTrackballLine(context, offset, chartThemeData, themeData);
        TextStyle style = TextStyle(
          color: Colors.white,
          fontSize: 12,
          fontWeight: FontWeight.bold,
          background: Paint()
            ..color = Colors.blueGrey
            ..strokeWidth = 17
            ..strokeJoin = StrokeJoin.round
            ..strokeCap = StrokeCap.round
            ..style = PaintingStyle.stroke,
          );

        if (chartPointInfo.isNotEmpty) {
          _drawText(
            context.canvas,
            chartPointInfo[0].label!,
            Offset(chartPointInfo[0].xPosition!, chartPointInfo[0].yPosition!),
            style);
        }
      }

      void _drawCustomTrackballLine(PaintingContext context, Offset offset, SfChartThemeData chartThemeData, ThemeData themeData) {
        if (chartPointInfo.isNotEmpty && lineType != TrackballLineType.none) {
          final Rect plotAreaBounds = parentBox!.paintBounds;
          final double x = chartPointInfo[0].xPosition!;
          final Offset start = Offset(x, chartPointInfo[0].yPosition!);
          final Offset end = Offset(x, plotAreaBounds.bottom);
          final Paint paint = Paint()
            ..isAntiAlias = true
            ..color = Colors.red
            ..strokeWidth = 2
            ..style = PaintingStyle.stroke
            ..shader = ui.Gradient.linear(
              start,
              end,
              <Color>[Colors.blueGrey, Colors.white],
              <double>[0.75, 1],
            );

          context.canvas.drawLine(end, start, paint);
          context.canvas.drawCircle(start, 5,
              Paint()
                ..color = Colors.blueGrey
                ..style = PaintingStyle.fill);
          context.canvas.drawCircle(start, 5,
              Paint()
                ..color = Colors.blueGrey
                ..strokeWidth = 2.0
                ..style = PaintingStyle.stroke
                ..isAntiAlias = true);
        }
      }

      void _drawText(Canvas canvas, String text, Offset point,  TextStyle style) {
        final TextPainter tp = TextPainter(
          text: TextSpan(text: text, style: style),
          textDirection: TextDirection.ltr,
          textAlign: TextAlign.center,
          maxLines: getMaxLinesContent(text),
        );

        tp.layout();
        canvas.save();
        canvas.translate(point.dx - tp.width / 2, point.dy - (tp.height * 2));
        Offset labelOffset = Offset.zero;
        tp.paint(canvas, labelOffset);
        canvas.restore();
      }
    }

{% endhighlight %}
{% endtabs %}

![Customized trackball](images\trackball-crosshair/customized_trackball.gif)

## Methods in crosshairBehavior

### Show method in crosshairBehavior

The [`show`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/show.html) method is used to activate the crosshair at the specified location.

{% tabs %}
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
{% endtabs %}

### showByIndex method in crosshairBehavior

The [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/showByIndex.html) method is used to activate the crosshair at the specified point index.

[`pointIndex`] - index of point at which the crosshair needs to be shown.

{% tabs %}
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
{% endtabs %}

### Hide method in crosshairBehavior

The [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/hide.html) method is used to hide the displaying crosshair programmatically.

{% tabs %}
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
{% endtabs %}

### Events in crosshairBehavior

Provided the following methods for handling pointer and gesture events and allowing customizations for various pointer events such as long-press, tap, double-tap, pointer enter, and exit.

* [`handleEvent`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/handleEvent.html) - Specifies to customize the necessary pointer events.
* [`handleLongPressStart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/handleLongPressStart.html) - Specifies to customize the pointer event when a long-press begins.
* [`handleLongPressMoveUpdate`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/handleLongPressMoveUpdate.html) - Specifies to customize the pointer event during movement after a long-press.
* [`handleLongPressEnd`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/handleLongPressEnd.html) - Specifies to customize the pointer event when the pointer stops contacting the screen after a long-press.
* [`handleTapDown`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/handleTapDown.html) - Specifies to customize the pointer event when a tap has contacted the screen once.
* [`handleTapUp`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/handleTapUp.html) - Specifies to customize the pointer event when it has stopped contacting the screen after a tap.
* [`handleDoubleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/handleDoubleTap.html) - Specifies to customize the pointer event when a tap has contacted the screen twice.
* [`handlePointerEnter`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/handlePointerEnter.html) -Specifies to customize the pointer event when the mouse enter on the screen.
* [`handlePointerExit`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/handlePointerExit.html) - Specifies to customize the pointer event when the mouse exit on the screen.

This following code sample defines how to enable or disable specific pointer events and customize to show crosshair in double tap and disabled crosshair showing in pointer enter and exit.

{% tabs %}
{% highlight dart %} 

    SfCartesianChart(
      crosshairBehavior: CustomCrosshair(),
      // Add series.
    );
    
    class CustomCrosshair extends crosshairBehavior {
      @override
      bool get enable => true;

      // Disable the behavior of pointer events(move, cancel, hover and up).
      @override
      void handleEvent(PointerEvent event, BoxHitTestEntry entry) {}

      // Disable the behavior of the pointer enter on the screen.
      @override
      void handlePointerEnter(PointerEnterEvent details) {}

      // Disable the behavior of the pointer exit on the screen.
      @override
      void handlePointerExit(PointerExitEvent details) {}

      @override
      void handleDoubleTap(Offset position) {
        if (activationMode == ActivationMode.doubleTap) {
          Offset localPosition = parentBox!.globalToLocal(position);
          show(localPosition.dx, localPosition.dy, 'pixel');
        }
      }
    }

{% endhighlight %}
{% endtabs %}

### DrawVerticalAxisLine method in crosshairBehavior

The [`drawVerticalAxisLine`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/drawVerticalAxisLine.html) method is used to customize the stroke drawing and styling of vertical crosshair line.

* `context` - Specifies the painting context.
* `offset` - Specifies the crosshair position.
* `dashArray` - Specifies the crosshair [`lineDashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/lineDashArray.html).
* `strokePaint` - Specifies the crosshair line stroke paint.

{% tabs %}
{% highlight dart %} 

    class CustomCrosshair extends CrosshairBehavior {
      @override
      void drawVerticalAxisLine(PaintingContext context, Offset offset,
        List<double>? dashArray, Paint strokePaint) {
        strokePaint
          ..isAntiAlias = true
          ..color = Colors.green
          ..strokeWidth = 1;
        dashArray = [5, 10, 5];
        super.drawVerticalAxisLine(context, offset, dashArray, strokePaint);
      }
    }

{% endhighlight %}
{% endtabs %}

### DrawHorizontalAxisLine method in crosshairBehavior

The [`drawHorizontalAxisLine`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/drawHorizontalAxisLine.html) method is used to customize the stroke drawing and styling of horizontal crosshair line.

{% tabs %}
{% highlight dart %} 

    class CustomCrosshair extends CrosshairBehavior {
      @override
      void drawHorizontalAxisLine(PaintingContext context, Offset offset, List<double>? dashArray, Paint strokePaint) {
        strokePaint
          ..isAntiAlias = true
          ..strokeCap = StrokeCap.round
          ..color = Colors.red
          ..strokeWidth = 2;
        dashArray = [10, 15, 10];
        super.drawHorizontalAxisLine(context, offset, dashArray, strokePaint);
      }
    }

{% endhighlight %}
{% endtabs %}

### DrawHorizontalAxisTooltip method in crosshairBehavior

The [`drawHorizontalAxisTooltip`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/drawHorizontalAxisTooltip.html) method is used to customize the tooltip label, position, and style for horizontal axis tooltip.

* `context` - Specifies the painting context.
* `position` - Specifies the position of the tooltip label.
* `text` - Specifies the tooltip label.
* `style` - Specifies the style of the tooltip text.
* `path` - Specifies path reference of the tooltip rectangle.
* `fillPaint` - Specifies the fill paint applied to the default tooltip rectangle.
* `strokePaint` - Specifies the stroke paint applied to the default tooltip rectangle.

{% tabs %}
{% highlight dart %} 

    class CustomCrosshair extends CrosshairBehavior {
      Offset? customPosition;

      @override
      void show(x, double y, [String coordinateUnit = 'point']) {
        if (coordinateUnit == 'pixel') {
          customPosition = Offset(x.toDouble(), y);
        }
        super.show(x, y, 'pixel');
      }

      @override
      void drawHorizontalAxisTooltip(PaintingContext context, Offset position, String text, TextStyle style, [Path? path, Paint? fillPaint, Paint? strokePaint]) {
        TextStyle style = TextStyle(
        color: Colors.white,
        fontSize: 12,
        background: Paint()
          ..color = Colors.blueGrey
          ..strokeWidth = 16
          ..strokeJoin = StrokeJoin.round
          ..style = dart_ui.PaintingStyle.stroke,
        );

        if (parentBox != null) {
        final Rect bounds = parentBox!.paintBounds;
        final String finalText = 'Y : ${verticalValue.toStringAsFixed(2)}';
        final Offset horizontalPosition =
            Offset(bounds.right, customPosition!.dy).translate(-50, -20);
        _drawText(context.canvas, finalText, horizontalPosition, style);
      }
    }

      void _drawText(Canvas canvas, String text, Offset point, TextStyle style) {
        final TextPainter textPainter = TextPainter(
          text: TextSpan(
            text: text,
            style: style.copyWith(fontWeight: dart_ui.FontWeight.bold)),
        textDirection: dart_ui.TextDirection.ltr,
        textAlign: TextAlign.center,
        maxLines: getMaxLinesContent(text),
        );
        
        textPainter
        ..layout()
        ..paint(canvas, point);
      }
    }

{% endhighlight %}
{% endtabs %}

![Crosshair Horizonatl Axis Tooltip](images\trackball-crosshair/custom_crosshair_horizontal_tooltip.png)

### DrawVerticalAxisTooltip method in crosshairBehavior

The [`drawVerticalAxisTooltip`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/drawVerticalAxisTooltip.html) method is used to customize the tooltip label, position, and style for vertical axis tooltip.

For further reference, please consult the [`drawHorizontalAxisTooltip`](https://help.syncfusion.com/flutter/cartesian-charts/methods#drawhorizontalaxistooltip-method-in-crosshairbehavior) code sample.

![Crosshair Vertical Axis Tooltip](images\trackball-crosshair/custom_crosshair_vertical_tooltip.png)

### onPaint in crosshairBehavior

The [`onPaint`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CrosshairBehavior/onPaint.html) method is used to customize the label, position, and style of crosshair tooltip.

{% tabs %}
{% highlight dart %} 

    dynamic verticalValue;
    late String horizontalText;

    @override
    void initState() {
      verticalValue = null;
      horizontalText = '';
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      final List<_SalesData> dateTimeData = [
        _SalesData(DateTime(2015, 2, 0), 31),
        _SalesData(DateTime(2015, 2, 1), 21),
        // Add data points.
      ];
      return Scaffold(
        body: SfCartesianChart(
          crosshairBehavior: CustomCrosshair(),
          onCrosshairPositionChanging: (CrosshairRenderArgs args) {
            if (args.orientation != null) {
              if (args.orientation == AxisOrientation.horizontal) {
                horizontalText = args.text;
              }
              if (args.orientation == AxisOrientation.vertical) {
                verticalValue = args.value;
              }
            }
          },
          series: <CartesianSeries<_SalesData, DateTime>>[
            SplineSeries(
              dataSource: dateTimeData,
              xValueMapper: (_SalesData sales, _) => sales.x,
              yValueMapper: (_SalesData sales, _) => sales.y,
              markerSettings: MarkerSettings(isVisible: true),
            ),
          ],
        ),
      );
    }
    

    class _SalesData {
      _SalesData(this.x, this.y);
      final dynamic x;
      final double y;
    }

    class CustomCrosshair extends CrosshairBehavior {
      @override
      bool get enable => true;

      Offset? customPosition;

      @override
      void show(x, double y, [String coordinateUnit = 'point']) {
        if (coordinateUnit == 'pixel') {
          customPosition = Offset(x.toDouble(), y);
        }
        super.show(x, y, 'pixel');
      }

      @override
      void drawHorizontalAxisLine(PaintingContext context, Offset offset, List<double>? dashArray, Paint strokePaint) {
        strokePaint
          ..isAntiAlias = true
          ..strokeCap = StrokeCap.round
          ..color = Colors.red
          ..strokeWidth = 2;
        dashArray = [10, 15, 10];
        super.drawHorizontalAxisLine(context, offset, dashArray, strokePaint);
      }

      @override
      void drawVerticalAxisLine(PaintingContext context, Offset offset, List<double>? dashArray, Paint strokePaint) {
        strokePaint
          ..isAntiAlias = true
          ..strokeCap = StrokeCap.round
          ..color = Colors.green
          ..strokeWidth = 2;
        dashArray = [5, 10, 5];
        super.drawVerticalAxisLine(context, offset, dashArray, strokePaint);
      }

      @override
      void drawVerticalAxisTooltip(
      PaintingContext context, Offset position, String text, TextStyle style, [Path? path, Paint? fillPaint, Paint? strokePaint]) {
        // Don't invoke default tooltip.
      }

      @override
      void drawHorizontalAxisTooltip(
      PaintingContext context, Offset position, String text, TextStyle style, [Path? path, Paint? fillPaint, Paint? strokePaint]) {
        // Don't invoke default tooltip.
      }

      @override
      void onPaint(PaintingContext context, Offset offset, SfChartThemeData chartThemeData, ThemeData themeData) {
        super.onPaint(context, offset, chartThemeData, themeData);
        // Custom tooltip.
        TextStyle style = TextStyle(
          color: Colors.white,
          fontSize: 12,
          background: Paint()
            ..color = Colors.blueGrey
            ..strokeWidth = 16
            ..strokeJoin = StrokeJoin.round
            ..style = dart_ui.PaintingStyle.stroke,
        );

        if (customPosition != null && horizontalText != '' && verticalValue != null) {
          final String finalText = 'X : ${horizontalText}  Y : ${verticalValue.toStringAsFixed(2)}';
          _drawText( context.canvas, finalText, customPosition!.translate(20, 20), style);
        }
      }

      void _drawText(Canvas canvas, String text, Offset point, TextStyle style) {
        final TextPainter textPainter = TextPainter(
          text: TextSpan(
            text: text,
            style: style.copyWith(fontWeight: dart_ui.FontWeight.bold)),
          textAlign: TextAlign.center,
          textDirection: dart_ui.TextDirection.ltr,
        );
        textPainter
          ..layout()
          ..paint(canvas, point);
      }

      @override
      void hide() {
        customPosition = null;
        horizontalText = '';
        verticalValue = null;
        super.hide();
      }
    }

{% endhighlight %}
{% endtabs %}

![Customized crosshair](images\trackball-crosshair/customized_crosshair.gif)

## Methods in selectionBehavior

### SelectDataPoints method in selectionBehavior

The [`selectDataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectDataPoints.html) method is used to select the data point programmatically. The required arguments are listed below.

* `pointIndex` - index of the point which needs to be selected.
* `seriesIndex` - index of the series for which the pointIndex is specified and this is an optional argument. By default it will be considered as 0.

>**Note**: The [`enableMultiSelection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/enableMultiSelection.html) and [`selectionType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/selectionType.html) are also applicable for this but, it is based on their API values specified in the chart.

{% tabs %}
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
{% endtabs %}

## Methods in zoomPanBehavior

### ZoomIn method in zoomPanBehavior

The [`zoomIn`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomIn.html) method is used to increase the magnification of the plot area.

{% tabs %}
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
{% endtabs %}

### ZoomOut method in zoomPanBehavior

The [`zoomOut`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomOut.html) method is used to decrease the magnification of the plot area.

{% tabs %}
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
{% endtabs %}

### zoomByFactor method in zoomPanBehavior

The [`zoomByFactor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomByFactor.html) method changes the zoom level using zoom factor. Here, you can pass the zoom factor of an axis to magnify the plot area. The value ranges from 0 to 1.

{% tabs %}
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
{% endtabs %}

### ZoomByRect method in zoomPanBehavior

The [`zoomByRect`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomByRect.html) method zooms the chart for a given rectangle value. Here, you can pass the rectangle with the left, right, top, and bottom values, using which the selection zooming will be performed.

{% tabs %}
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
{% endtabs %}

### ZoomToSingleAxis method in zoomPanBehavior

The [`zoomToSingleAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/zoomToSingleAxis.html) method changes the zoom level of an appropriate axis. Here, you need to pass axis, zoom factor, zoom position of the zoom level that needs to be modified.

{% tabs %}
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
{% endtabs %}

### PanToDirection method in zoomPanBehavior

The [`panToDirection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/panToDirection.html) method pans the plot area for given left, right, top, and bottom directions. To perform this action, the plot area needs to be in zoomed state.

{% tabs %}
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
{% endtabs %}

### Reset method in zoomPanBehavior

The [`reset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ZoomPanBehavior/reset.html) method returns the plot area back to its original position after zooming..

{% tabs %}
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
{% endtabs %}

### Events in zoomPanBehavior

Provided the following methods for handling pointer and gesture events and allowing customizations for various pointer events such as double-tap, scale and long-press.

* `handleEvent` - Specifies to customize the necessary pointer events.
* `handleDoubleTap` - Specifies to customize the pointer event when a tap has contacted the screen twice.
* `handleScaleStart` - Specifies to customize the pointer event when the pointers begins to move.
* `handleScaleUpdate` - Specifies to customize the pointer event when the pointers in the moving state.
* `handleScaleEnd` - Specifies to customize the pointer event when the pointers stops moving and contacting on the screen.
* `handleLongPressStart` - Specifies to customize the pointer event when a long-press begins.
* `handleLongPressMoveUpdate` - Specifies to customize the pointer event during movement after a long-press.
* `handleLongPressEnd` - Specifies to customize the pointer event when the pointer stops contacting the screen after a long-press.

This following code sample defines how to perform zoom in and out behavior in double tap zooming.

{% endhighlight %}
{% endtabs %}

    CategoryAxis xAxis = CategoryAxis();
    NumericAxis yAxis = NumericAxis();

    SfCartesianChart(
      primaryXAxis: xAxis,
      primaryYAxis: yAxis,
      zoomPanBehavior: CustomDoubleTapZoomPanBehavior(xAxis, yAxis),
      // Add series here.
      series: series: [
        LineSeries(),
      ]
    );

    class CustomDoubleTapZoomPanBehavior extends ZoomPanBehavior {
      CustomDoubleTapZoomPanBehavior(this.xAxis, this.yAxis);

      CategoryAxis xAxis;
      NumericAxis yAxis;

      @override
      bool get enableDoubleTapZooming => true;

      bool _isZoomIn = true;

      @override
      void handleDoubleTap(Offset position) {
        if (parentBox == null && !enableDoubleTapZooming) {
          return;
        }
        const double origin = 0.5;
        final double cumulativeZoomLevel = _isZoomIn ? 1.4 : 1.0;
        double zoomFactor = 1 / cumulativeZoomLevel;
        double zoomPosition = (1 - zoomFactor) * origin;

        _isZoomIn = !_isZoomIn;
        zoomToSingleAxis(xAxis, zoomPosition, zoomFactor);
        zoomToSingleAxis(yAxis, zoomPosition, zoomFactor);
      }
    }

{% endhighlight %}
{% endtabs %}

![Customized double tap](images\zooming-panning\custom_double_tap_zoom.gif)

### onPaint in ZoomPanBehavior

To customize the tooltip label, position, and selection rect of the zooming.

This following code sample defines how to perform selection zooming and customize the selection zooming rect in single tap using scale methods.

{% endhighlight %}
{% endtabs %}

    SfCartesianChart(
      zoomPanBehavior: CustomScaleZoomPanBehavior(),
      // Add series here.
      series: series: [
        LineSeries(),
      ]
    );

    class CustomScaleZoomPanBehavior extends ZoomPanBehavior {
      @override
      bool get enableSelectionZooming => true;

      RRect? _customRect;
      Rect? _zoomRect;
      Offset? _customRectStartPosition;
      Offset? _textPosition;

      @override
      void handleScaleStart(ScaleStartDetails details) {
        _customRectStartPosition = parentBox!.globalToLocal(details.focalPoint);
      }

      @override
      void handleScaleUpdate(ScaleUpdateDetails details) {
        if (details.pointerCount != 1 || !enableSelectionZooming) {
          return;
        }
        _calculateCustomRect(parentBox!.globalToLocal(details.focalPoint));
        parentBox!.markNeedsPaint();
      }

      @override
      void handleScaleEnd(ScaleEndDetails details) {
        _customRectStartPosition = null;
        _textPosition = null;
        zoomByRect(_zoomRect!);
        _customRect = RRect.zero;
        _zoomRect = Rect.zero;
        parentBox?.markNeedsPaint();
      }

      // Disable the long Press selection zooming behavior
      @override
      void handleLongPressStart(LongPressStartDetails details) {}

      // Disable the long Press selection zooming behavior
      @override
      void handleLongPressMoveUpdate(LongPressMoveUpdateDetails details) {}

      // Disable the long Press selection zooming behavior
      @override
      void handleLongPressEnd(LongPressEndDetails details) {}

      @override
      void onPaint(PaintingContext context, Offset offset,
          SfChartThemeData chartThemeData, ThemeData themeData) {
        if (_zoomRect == null || _textPosition == null) {
          return;
        }
        _drawCustomRect(context, chartThemeData, themeData);
        _drawText(context.canvas);
      }

      void _calculateCustomRect(Offset position) {
        if (parentBox == null) {
          return;
        }
        if (_customRectStartPosition != null) {
          final Rect clipRect = parentBox!.paintBounds;
          final Offset startPosition = Offset(
            max(_customRectStartPosition!.dx, clipRect.left),
            max(_customRectStartPosition!.dy, clipRect.top),
          );
          Offset currentPosition = position;
          final double currentX =
              _minMax(currentPosition.dx, clipRect.left, clipRect.right);
          final double currentY =
              _minMax(currentPosition.dy, clipRect.top, clipRect.bottom);
          currentPosition = Offset(currentX, currentY);
          double left = startPosition.dx > currentPosition.dx
              ? currentPosition.dx
              : startPosition.dx;
          double top = startPosition.dy > currentPosition.dy
              ? currentPosition.dy
              : startPosition.dy;
          double right = startPosition.dx < currentPosition.dx
              ? currentPosition.dx
              : startPosition.dx;
          double bottom = startPosition.dy < currentPosition.dy
              ? currentPosition.dy
              : startPosition.dy;
          _zoomRect = Rect.fromLTRB(left, top, right, bottom);
          _customRect = RRect.fromRectAndRadius(_zoomRect!, Radius.circular(20));
          _textPosition = currentPosition;
        }
      }

      void _drawCustomRect(PaintingContext context, SfChartThemeData chartThemeData,
          ThemeData themeData) {
        final Paint customRectPaint = Paint()..color = Colors.teal.withOpacity(0.1);
        final Paint customStrokeRectPaint = Paint()
          ..color = Colors.teal.withOpacity(0.7)
          ..style = PaintingStyle.stroke
          ..strokeWidth = 2;
        context.canvas.drawRRect(_customRect!, customRectPaint);
        context.canvas.drawRRect(_customRect!, customStrokeRectPaint);
      }

      double _minMax(double value, double min, double max) {
        return value > max ? max : (value < min ? min : value);
      }

      void _drawText(Canvas canvas) {
        String left = _zoomRect!.left.toStringAsFixed(2);
        String top = _zoomRect!.top.toStringAsFixed(2);
        String right = _zoomRect!.right.toStringAsFixed(2);
        String bottom = _zoomRect!.bottom.toStringAsFixed(2);
        String text =
            'left: $left \n top: $top \n right: $right \n bottom: $bottom';
        final TextSpan span = TextSpan(
            text: text, style: TextStyle(fontSize: 10, color: Colors.black));
        final TextPainter textPainter = TextPainter(
          text: span,
          textAlign: TextAlign.center,
          textDirection: TextDirection.ltr,
        );
        textPainter.layout();
        if (_zoomRect!.width < textPainter.width ||
            _zoomRect!.height < textPainter.height) {
          return;
        }
        double leftX = 0;
        double topY = 0;
        if (_zoomRect!.left == _textPosition!.dx) {
          leftX = 80;
        } else {
          leftX = -10;
        }
        if (_zoomRect!.top == _textPosition!.dy) {
          topY = 60;
        } else {
          topY = -10;
        }
        canvas.save();
        canvas.translate(_textPosition!.dx, _textPosition!.dy);
        final Offset labelOffset =
            Offset(-textPainter.width + leftX, -textPainter.height + topY);
        textPainter.paint(canvas, labelOffset);
        canvas.restore();
      }
    }

{% endhighlight %}
{% endtabs %}

![Customized selection zooming](images\zooming-panning\custom_selection_zooming.png)

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


{% tabs %}
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
                series: <LineSeries<ChartData, num>>[
                    LineSeries<ChartData, num>(
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
  }

     class ChartData {
        ChartData(this.x, this.y);
        final num x;
        final double? y;
      }


{% endhighlight %}
{% endtabs %}

#### See Also

* [Rendering real time live charts using updateDataSource method](https://support.syncfusion.com/kb/article/10783/how-to-create-flutter-real-time-charts-using-the-cartesian-charts-widget-sfcartesianchart).

## PixelToPoint 

Converts logical pixel value to the data point value.
  
The [`pixelToPoint`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeriesController/pixelToPoint.html) method takes logical pixel value as input and returns a chart data point.
  
Since this method is in the series controller, x and y-axis associated with this particular series will be considering for conversion value.

{% tabs %}
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
{% endtabs %}

## PointToPixel 
Converts chart data point value to logical pixel value.
  
The [`pointToPixel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeriesController/pointToPixel.html) method takes chart data point value as input and returns logical pixel value.
  
Since this method is in the series controller, x and y-axis associated with this particular series will be considering for conversion value.
  
>**Note**: This method is only applicable for Cartesian chart, not for the circular, pyramid,
and funnel charts.
  
{% tabs %}
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
{% endtabs %}

#### See Also

* [Show or hide tooltip dynamically in Cartesian chart](https://support.syncfusion.com/kb/article/9957/how-to-show-or-hide-the-tooltip-dynamically-in-flutter-cartesian-charts-sfcartesianchart).
* [Show or hide trackball dynamically in Cartesian chart](https://support.syncfusion.com/kb/article/9960/how-to-show-or-hide-trackball-dynamically-in-flutter-cartesian-charts-sfcartesianchart).
* [Show or hide crosshair dynamically in Cartesian chart](https://support.syncfusion.com/kb/article/9911/how-to-show-or-hide-crosshair-dynamically-in-flutter-cartesian-charts-sfcartesianchart).

>**Note**: `chartData` in the above code snippets is a class type list and holds the data for binding to the chart series. Refer [Bind data source](https://help.syncfusion.com/flutter/cartesian-charts/getting-started#bind-data-source) topic for more details.
