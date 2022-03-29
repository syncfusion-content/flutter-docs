---
layout: post
title: Selection in Flutter Circular Charts widget | Syncfusion 
description: Learn here all about Selection feature of Syncfusion Flutter Circular Charts (SfCircularChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Selection in Flutter Circular Charts (SfCircularChart)

The selection feature in chart let you to select a segment in a series or the series itself. This features allows you to select either individual or cluster of segments in the chart series.

{% tabs %}
{% highlight dart hl_lines="7" %} 
    
    late SelectionBehavior _selectionBehavior;

    @override
    void initState(){
        _selectionBehavior = SelectionBehavior(
            // Enables the selection
            enable: true);
        super.initState();
    }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            PieSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                selectionBehavior: _selectionBehavior
                            )
                        ]
                    )
                )
            )
        );  
    }

{% endhighlight %}
{% endtabs %}

![Selection](images/selection/default_selection.jpg)

## Customizing the segments

You can customize the segments using the below properties.

* [`selectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectedColor.html) - used to change the background color of selected segment.
* [`unselectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/unselectedColor.html) - used to change the background color of unselected segment.
* [`selectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectedBorderColor.html) - used to change the stroke color of the selected segment.
* [`selectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectedBorderWidth.html) - used to change the stroke width of the selected segment.
* [`unselectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/unselectedBorderColor.html) - used to change the stroke color of the unselected segment.
* [`unselectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/unselectedBorderWidth.html) - used to change the stroke width of the unselected segment.
* [`selectedOpacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectedOpacity.html) - used to control the transparency of the selected segment.
* [`unselectedOpacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/unselectedOpacity.html) - used to control the transparency of the unselected segment.
* [`selectionController`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectionController.html) - used to customize the minimum range of selected series or points.

{% tabs %}
{% highlight dart %} 
    
    late SelectionBehavior _selectionBehavior;

    @override
    void initState(){
        _selectionBehavior = SelectionBehavior(
             enable: true,
             selectedColor: Colors.red,
            unselectedColor: Colors.grey);
        super.initState();
    }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            PieSeries<ChartData, double>(
                                selectionBehavior: _selectionBehavior
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Customizing segments](images/selection/customizing_segments.jpg)

## Multi-selection

Multiple selection can be enabled using the [`enableMultiSelection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/enableMultiSelection.html) property of chart.

{% tabs %}
{% highlight dart hl_lines="8" %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        // Enables multiple selection
                        enableMultiSelection: true
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Multi selection](images/selection/multi_select.jpg)

## Toggle selection

You can decide, whether to deselect the selected data point/series or remain selected when interacted with it again by setting the [`toggleSelection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/toggleSelection.html) property `true` or `false`. If set to true, deselection will be performed else the point will not get deselected.
This works even while calling public methods, in various selection modes, with multi-selection, and also on dynamic changes.
Defaults to `true`.

{% tabs %}
{% highlight dart hl_lines="7" %} 

    late SelectionBehavior _selectionBehavior;

    @override
    void initState(){
      _selectionBehavior =  SelectionBehavior(
                          enable: true,
                          toggleSelection: false,
                        );
      super.initState(); 
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
            child: Container(
                child: SfCircularChart(
                    series: <CircularSeries<ChartData, String>>[
                       PieSeries<ChartData, String>(
                        dataSource: chartData1,
                        xValueMapper: (ChartData data, _) => data.x,
                        yValueMapper: (ChartData data, _) => data.y,
                        selectionBehavior: _selectionBehavior
                        )
                    ]
                )
            )
         )
      );
   }

{% endhighlight %}
{% endtabs %}

![Toggle selection](images/selection/deselection.gif)

Also refer [`selection event`](./events#onselectionchanged) for customizing the selection further.

#### See Also

* [Creating a clickable pie chart using selection in circular charts](https://www.syncfusion.com/kb/12346/how-to-create-clickable-pie-chart-in-flutter-using-circular-charts-widget-sfcircularchart).