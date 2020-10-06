---
layout: post
title: Syncfusion Flutter Circular Chart Public Methods
description: Learn what are all the public methods available in Syncfusion Flutter Circular Charts along with their properties.
platform: flutter
control: Chart
documentation: ug
---

# Methods in Circular charts

## Methods in tooltipBehavior

### Show method in tooltipBehavior

The [`show`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/show.html) method is used to activate the tooltip at the specified x and y point values.

{% highlight dart %} 

    SfCircularChart chart;
    TooltipBehavior tooltip;

    @override
    Widget build(BuildContext context) {

    final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
        // Add the required data
    ];
    
    tooltip = TooltipBehavior (enable: true);

    chart = SfCircularChart(
      tooltipBehavior: tooltip,
        series: <CircularSeries>[
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
      tooltip.show(10, 17);
    }
  
  {% endhighlight %}

### showByIndex method in tooltipBehavior

The [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByIndex.html) method is used to Displays the tooltip at the specified series and point index.

The below mentioned arguments are given to the [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByIndex.html) method:

[`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/seriesIndex.html) - index of the series for which the pointIndex is specified.

[`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/pointIndex.html)  - index of the point for which the tooltip should be shown.


{% highlight dart %} 

    SfCircularChart chart;
    TooltipBehavior tooltip;

    @override
    Widget build(BuildContext context) {

    final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
        // Add the required data
    ];
    
    tooltip = TooltipBehavior (enable: true);

    chart = SfCircularChart(
      tooltipBehavior: tooltip,
        series: <CircularSeries>[
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

  {% endhighlight %}

### showByPixel method in tooltipBehavior

The [`showByPixel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByPixel.html) method is used to Displays the tooltip at the specified x and y-positions.

x & y - logical pixel values to position the tooltip.

{% highlight dart %} 

    SfCircularChart chart;
    TooltipBehavior tooltip;

    @override
    Widget build(BuildContext context) {

    final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34),
        // Add the required data
    ];
    
    tooltip = TooltipBehavior (enable: true);

    chart = SfCircularChart(
      tooltipBehavior: tooltip,
        series: <CircularSeries>[
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
  {% endhighlight %}

### Hide method in tooltipBehavior

The [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/hide.html) method is used to hide the displaying tooltip programmatically.

{% highlight dart %} 

    SfCircularChart chart;
    TooltipBehavior tooltip;

    @override
    Widget build(BuildContext context) {
    final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34)
    // Add the required data  
    ];
    
    tooltip = TooltipBehavior (enable: true);

    chart = SfCircularChart(
      tooltipBehavior: tooltip,
      series: <CircularSeries>[
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

## Methods in selectionBehavior

### SelectDataPoints method in selectionBehavior

The [`selectDataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectDataPoints.html) method is used to select the data point programmatically. The required arguments are listed below.

* `pointIndex` - index of the point which needs to be selected.
* `seriesIndex` - index of the series for which the pointIndex is specified and this is an optional parameter. By default it will be considered as 0.

N> The [`enableMultiSelection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/enableMultiSelection.html) is also applicable for this but, it is based on the API values specified in the chart.

{% highlight dart %}

    SfCircularChart chart;
    SelectionBehavior selection;

    @override
    Widget build(BuildContext context) {
    
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34)
      // Add the required data
    ];

    selection = SelectionBehavior(enable: true);
    
    chart = SfCircularChart(
      series: <CircularSeries>[
        PieSeries<ChartData, double>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y,
            selectionBehavior: selection
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
        selection.selectDataPoints(1, 0);
    }

{% endhighlight %}