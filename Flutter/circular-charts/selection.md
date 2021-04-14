---
layout: post
title: Syncfusion Flutter Circular Charts Data Point Selection
description: Learn how to select and customize the data point in SfCircular Charts and enable the multi selection in SfCircular Charts.
platform: flutter
control: Chart
documentation: ug
---

# Selection in Circular charts

The selection feature in chart let you to select a segment in a series or the series itself. This features allows you to select either individual or cluster of segments in the chart series.

{% highlight dart %} 
    
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

![Customizing segments](images/selection/customizing_segments.jpg)

## Multi-selection

Multiple selection can be enabled using the [`enableMultiSelection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/enableMultiSelection.html) property of chart.

{% highlight dart %} 

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

![Multi selection](images/selection/multi_select.jpg)

Also refer [selection event](./events#onselectionchanged) for customizing the selection further.

#### See Also

* [Creating a clickable pie chart using selection in circular charts](https://www.syncfusion.com/kb/12346/how-to-create-clickable-pie-chart-in-flutter-using-circular-charts-widget-sfcircularchart).