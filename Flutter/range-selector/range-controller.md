---
layout: post
title: Controller in Syncfusion Flutter Range Selector | Syncfusion
description: This section explains about how to use the range controller in the range selector.
platform: Flutter
control: SfRangeSelector
documentation: ug
---

# Range controller in range selector

You can use [`RangeController`](https://pub.dev/documentation/syncfusion_flutter_core/latest/core/RangeController-class.html) for setting and getting current selected values of range selector.

The `start` represents the currently selected start value of the range selector. The left thumb of the range selector was drawn corresponding to this value.

The `end` represents the currently selected end value of the range selector. The right thumb of the range selector was drawn corresponding to this value.

You can get previous values using `previousStart` and `previousEnd` properties.

The `start`, `end`, `previousStart`, `previousEnd` properties can be either `double` or `DateTime` based on whether it is date type [`SfRangeSelector`](https://help.syncfusion.com/flutter/range-selector/getting-started#set-date-range) or numeric [`SfRangeSelector`](https://help.syncfusion.com/flutter/range-selector/getting-started#set-numeric-range).

I> You need not to set the [`initialValues`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector/initialValues.html) property when using [`controller`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector/controller.html) property in the range selector.

N> You must import the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) to use the range controller in the range selector.

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _values = SfRangeValues(4.0, 6.0);
RangeController _rangeController;

@override
void initState() {
   super.initState();
     _rangeController = RangeController(
     start: _values.start,
     end: _values.end);
}

@override
void dispose() {
   _rangeController.dispose();
   super.dispose();
}

final List<Data> chartData = <Data>[
    Data(x:2.0, y: 2.2),
    Data(x:3.0, y: 3.4),
    Data(x:4.0, y: 2.8),
    Data(x:5.0, y: 1.6),
    Data(x:6.0, y: 2.3),
    Data(x:7.0, y: 2.5),
    Data(x:8.0, y: 2.9),
    Data(x:9.0, y: 3.8),
    Data(x:10.0, y: 3.7),
];

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: SfRangeSelector(
                    min: _min,
                    max: _max,
                    interval: 1,
                    showTicks: true,
                    showLabels: true,
                    controller: _rangeController,
                    child: Container(
                    height: 130,
                    child: SfCartesianChart(
                        margin: const EdgeInsets.all(0),
                        primaryXAxis: NumericAxis(minimum: _min,
                            maximum: _max,
                            isVisible: false),
                        primaryYAxis: NumericAxis(isVisible: false),
                        plotAreaBorderWidth: 0,
                        series: <SplineAreaSeries<Data, double>>[
                            SplineAreaSeries<Data, double>(
                                color: Color.fromARGB(255, 126, 184, 253),
                                dataSource: chartData,
                                    xValueMapper: (Data sales, _) => sales.x,
                                    yValueMapper: (Data sales, _) => sales.y)
                            ],
                        ),
                   ),
              ),
          )
      )
  );
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight Dart %}

class Data {
  Data({this.x, this.y});
  final double x;
  final double y;
}

{% endhighlight %}
{% endtabs %}

![Range selector controller](images/range-controller/range-controller.png)

## Selection with SfChart

We have provided built-in support for selecting the chart segments based on the selected range in range selector.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2010, 03, 01), DateTime(2010, 06, 01));
RangeController _rangeController;
List<int> selectedItems;

@override
void initState() {
  super.initState();
    _rangeController = RangeController(
       start: _values.start,
       end: _values.end);
}

@override
void dispose() {
   _rangeController.dispose();
   super.dispose();
}

final List<Data> chartData = <Data>[
    Data(x: DateTime(2010, 01, 01), y: 2.2),
    Data(x: DateTime(2010, 02, 01), y: 3.4),
    Data(x: DateTime(2010, 03, 01), y: 2.8),
    Data(x: DateTime(2010, 04, 01), y: 1.6),
    Data(x: DateTime(2010, 05, 01), y: 2.3),
    Data(x: DateTime(2010, 06, 01), y: 2.5),
    Data(x: DateTime(2010, 07, 01), y: 2.9),
    Data(x: DateTime(2010, 08, 01), y: 3.8),
    Data(x: DateTime(2010, 09, 01), y: 3.7),
];

@override
Widget build(BuildContext context) {
   selectedItems = <int>[];
   for (int i = 0; i < chartData.length; i++) {
      if (chartData[i].x.millisecondsSinceEpoch >=
          _rangeController.start.millisecondsSinceEpoch &&
          chartData[i].x.millisecondsSinceEpoch <=
              _rangeController.end.millisecondsSinceEpoch) {
        selectedItems.add(chartData.indexOf(chartData[i]));
      }
   }

    return Scaffold(
        body: Center(
          child: SfRangeSelector(
            min: DateTime(2010, 01, 01),
            max: DateTime(2010, 09, 01),
            interval: 2,
            dateIntervalType: DateIntervalType.months,
            dateFormat: DateFormat.yM(),
            showTicks: true,
            showLabels: true,
            controller: _rangeController,
            child: Container(
              height: 130,
              child: SfCartesianChart(
                margin: const EdgeInsets.all(0),
                primaryXAxis: DateTimeAxis(minimum: DateTime(2010, 01, 01),
                    maximum: DateTime(2010, 09, 01),
                    isVisible: false),
                primaryYAxis: NumericAxis(isVisible: false),
                plotAreaBorderWidth: 0,
                plotAreaBackgroundColor: Colors.transparent,
                series: <ColumnSeries<Data, DateTime>>[
                  ColumnSeries<Data, DateTime>(
                      initialSelectedDataIndexes: selectedItems,
                      selectionSettings: SelectionSettings(
                          enable: true,
                          unselectedOpacity: 0,
                          selectedBorderColor: const Color.fromRGBO(
                              0, 178, 206, 1),
                          selectedColor: const Color.fromRGBO(0, 178, 206, 1),
                          unselectedColor: Colors.transparent,
                          selectionController: _rangeController),
                      color: const Color.fromRGBO(255, 255, 255, 0),
                      dashArray: <double>[5, 4],
                      borderColor: const Color.fromRGBO(194, 194, 194, 1),
                      animationDuration: 0,
                      borderWidth: 1,
                      dataSource: chartData,
                      xValueMapper: (Data sales, _) => sales.x,
                      yValueMapper: (Data sales, _) => sales.y)
                ],
              ),
            ),
          ),
        )
    );
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight Dart %}

class Data {
   Data({this.x, this.y});
   final DateTime x;
   final double y;
}

{% endhighlight %}
{% endtabs %}

![Selection support](images/range-controller/selection-controller-with-sfchart.gif)

## Zooming with SfChart

We have provided built-in support for updating the visible range of the chart based on the selected range in range selector.

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 19.0;
SfRangeValues _values = SfRangeValues(8.0, 16.0);
RangeController _rangeController;
SfCartesianChart splineChart;

@override
void initState() {
    super.initState();
    _rangeController = RangeController(start: _values.start, end: _values.end);
}

@override
void dispose() {
    _rangeController.dispose();
    super.dispose();
}

final List<Data> chartData = <Data>[
    Data(x: 2.0, y: 2.2),
    Data(x: 3.0, y: 3.4),
    Data(x: 4.0, y: 2.8),
    Data(x: 5.0, y: 1.6),
    Data(x: 6.0, y: 2.3),
    Data(x: 7.0, y: 2.5),
    Data(x: 8.0, y: 2.9),
    Data(x: 9.0, y: 3.8),
    Data(x: 10.0, y: 3.7),
    Data(x: 11.0, y: 2.2),
    Data(x: 12.0, y: 3.4),
    Data(x: 13.0, y: 2.8),
    Data(x: 14.0, y: 1.6),
    Data(x: 15.0, y: 2.3),
    Data(x: 16.0, y: 2.5),
    Data(x: 17.0, y: 2.9),
    Data(x: 18.0, y: 3.8),
    Data(x: 19.0, y: 3.7),
];

@override
Widget build(BuildContext context) {
    splineChart = SfCartesianChart(
      margin: const EdgeInsets.only(left: 10, right: 10, bottom: 20),
      primaryXAxis: NumericAxis(
          minimum: _min,
          maximum: _max,
          isVisible: true,
          rangeController: _rangeController),
      primaryYAxis: NumericAxis(isVisible: true),
      plotAreaBorderWidth: 0,
      series: <SplineSeries<Data, double>>[
        SplineSeries<Data, double>(
            color: Color.fromARGB(255, 126, 184, 253),
            dataSource: chartData,
            animationDuration: 0,
            xValueMapper: (Data sales, _) => sales.x,
            yValueMapper: (Data sales, _) => sales.y)
      ],
    );

    return Scaffold(
        body: Center(
          child: Padding(
            padding: EdgeInsets.only(left: 10, right: 10, top: 80),
            child: Column(
              children: <Widget>[
                Container(
                  child: splineChart,
                ),
                SfRangeSelector(
                  min: _min,
                  max: _max,
                  interval: 2,
                  showTicks: true,
                  showLabels: true,
                  controller: _rangeController,
                  child: Container(
                    height: 130,
                    child: SfCartesianChart(
                      margin: const EdgeInsets.all(0),
                      primaryXAxis: NumericAxis(
                          minimum: _min,
                          maximum: _max,
                          isVisible: false),
                      primaryYAxis: NumericAxis(isVisible: false),
                      plotAreaBorderWidth: 0,
                      series: <SplineSeries<Data, double>>[
                        SplineSeries<Data, double>(
                            color: Color.fromARGB(255, 126, 184, 253),
                            dataSource: chartData,
                            xValueMapper: (Data sales, _) => sales.x,
                            yValueMapper: (Data sales, _) => sales.y)
                      ],
                    ),
                  ),
                ),
              ],
            ),
          ),
       )
    );
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight Dart %}

class Data {
  Data({this.x, this.y});
  final double x;
  final double y;
}

{% endhighlight %}
{% endtabs %}

![Zooming support](images/range-controller/zooming-controller-with-sfchart.gif)
