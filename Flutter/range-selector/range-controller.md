---
layout: post
title: Controller in Syncfusion Flutter Range Selector | Syncfusion
description: This section explains about how to add the range controller to the range selector for Flutter platform
platform: Flutter
control: SfRangeSelector
documentation: ug
---

# Range controller in range selector

It coordinates the [`SfRangeSelector`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector-class.html) with charts. It automatically controls selection and zooming with charts using the `start` and `end` properties of the controller.

The `start` represents the currently selected start value of the range selector. The left thumb of the range selector was drawn corresponding to this value.

The `end` represents the currently selected end value of the range selector. The right thumb of the range selector was drawn corresponding to this value.

The `start` and `end` can be either `double` or `DateTime`.

I> No need to set the [`initialValues`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector/initialValues.html) property when using [`controller`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector/controller.html) property in the range selector.

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
                                selectionSettings: SelectionSettings(
                                    enable: true,
                                    selectionController: _rangeController),
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
