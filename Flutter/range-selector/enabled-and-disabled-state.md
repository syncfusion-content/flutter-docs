---
layout: post
title: Disabled state in Syncfusion Flutter Range Selector | Syncfusion
description: This section helps to learn about how to change disabled state in the range selector for Flutter platform
platform: Flutter
control: SfRangeSelector
documentation: ug
---

# Disabled state in range selector

This section helps to learn about how to change disabled state in the range selector.

## Disabled state

It controls the range selector’s state whether it is disabled or enabled. The default value of [`enabled`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSelector/enabled.html) property is `true`.

{% tabs %}
{% highlight Dart %}

final double _min = 2.0;
final double _max = 10.0;
SfRangeValues _initialValues = SfRangeValues(5.0, 8.0);

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
          body: Center(
              child: SfRangeSelector(
                    min: _min,
                    max: _max,
                    enabled: false,
                    initialValues: _initialValues,
                    child: Container(
                    height: 130,
                    child: SfCartesianChart(
                        margin: const EdgeInsets.all(0),
                        primaryXAxis: NumericAxis(minimum: _min,
                            maximum: _max,
                            isVisible: false,),
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

![Range selector disabled state](images/disabled-state/selector_disabled_state.png)

## Disabled color

You can change the disable state color of the active and inactive track using the [`disabledActiveTrackColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledActiveTrackColor.html) and [`disabledInactiveTrackColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledInactiveTrackColor.html) properties, color of the disabled active and inactive major ticks using the [`disabledActiveTickColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledActiveTickColor.html) and [`disabledInactiveTickColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledInactiveTickColor.html) properties, color of the disabled active and inactive minor ticks using the [`disabledActiveMinorTickColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledActiveMinorTickColor.html) and [`disabledInactiveMinorTickColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledInactiveMinorTickColor.html) properties, color of the active and inactive divisors using the [`disabledActiveDivisorColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledActiveDivisorColor.html) and [`disabledInactiveDivisorColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledInactiveDivisorColor.html) properties, color of the disabled thumb color using the [`disabledThumbColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSliderThemeData/disabledThumbColor.html) property.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfRangeSelectorTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfRangeSelectorTheme-class.html).

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
            body: Center(
              child: SfRangeSelectorTheme(
                data: SfRangeSliderThemeData(
                  disabledActiveTrackColor: Colors.orange,
                  disabledInactiveTrackColor: Colors.orange[200],
                  disabledActiveTickColor: Colors.orange,
                  disabledInactiveTickColor: Colors.orange[200],
                  disabledActiveMinorTickColor: Colors.orange,
                  disabledInactiveMinorTickColor: Colors.orange[200],
                  disabledActiveDivisorColor: Colors.purple,
                  disabledInactiveDivisorColor: Colors.purple[200],
                  disabledThumbColor: Colors.orange,
                ),
                child:  SfRangeSelector(
                  min: _min,
                  max: _max,
                  interval: 1,
                  showLabels: true,
                  enabled: false,
                  showTicks: true,
                  showDivisors: true,
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

![Disabled color support](images/enabled-and-disabled/selector-disabled-color.png)
