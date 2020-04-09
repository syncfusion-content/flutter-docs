---
layout: post
title: RTL feature in Syncfusion Flutter Range Selector | Syncfusion
description: This section helps to learn about how to change the layout direction in the right to left direction in range selector for Flutter platform
platform: Flutter
control: SfRangeSelector
documentation: ug
---

# Right to Left (RTL) in range selector

The SfRangeSelector supports changing the layout direction of the widget in the right-to-left direction by using the [`textDirection`](https://api.flutter.dev/flutter/widgets/Directionality/textDirection.html) property to `rtl` in the [`Directionality`](https://api.flutter.dev/flutter/widgets/Directionality-class.html) widget.

You can also change the right to left direction by specifying locale, that supports RTL language such as (Arabic ,Persian ,Hebrew, Pashto and Urdu) by specifying the MaterialApp properties and adding the flutter_localizations package to your application.

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _initialValues = SfRangeValues(4.0, 8.0);

final List<Data> _chartData = <Data>[
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
          backgroundColor: Colors.white,
          body: Directionality(
            textDirection: TextDirection.rtl,
            child: Center(
              child: SfRangeSelector(
                min: _min,
                max: _max,
                interval: 1,
                showLabels: true,
                showTicks: true,
                initialValues: _initialValues,
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
                          dataSource: _chartData,
                          xValueMapper: (Data sales, _) => sales.x,
                          yValueMapper: (Data sales, _) => sales.y)
                    ],
                  ),
                ),
              ),
            )
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

![RTL support](images/right-to-left/right-to-left-support.png)
