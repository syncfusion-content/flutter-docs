---
layout: post
title: Builders in Flutter Date Range Picker | Syncfusion
description: Step-by-step guide to use builders in Syncfusion Flutter Date Range Picker (SfDateRangePicker)—custom cell builders, view customization, and sample usage.
platform: flutter
control: SfDateRangePicker
documentation: ug
---
# Flutter Date Range Picker Builders (SfDateRangePicker)

The date range picker allows you to design custom views for month and year cells based on cell details.

## Cell builder

The [DateRangePickerCellBuilder](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerCellBuilder.html) allows you to design your custom view and assign the view to the month and year view cells of the date range picker by returning an appropriate widget in the [cellBuilder](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/cellBuilder.html) of [SfDateRangePicker](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker-class.html).

[DateRangePickerCellDetails](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerCellDetails-class.html): Returns the details of the cell.

* `date`: The date associated with the cell.
* `bound`: Returns the cell bounds.
* `visibleDates`: The visible dates of the current view.

{% tabs %}
{% highlight dart hl_lines="11 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65" %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_datepicker/datepicker.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: const PickerCellBuilder(),
    );
  }
}

class PickerCellBuilder extends StatefulWidget {
  const PickerCellBuilder({super.key});

  @override
  State<PickerCellBuilder> createState() => _PickerCellBuilderState();
}

class _PickerCellBuilderState extends State<PickerCellBuilder> {
  final DateRangePickerController _controller = DateRangePickerController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: SfDateRangePicker(
          controller: _controller,
          cellBuilder: (
            BuildContext context,
            DateRangePickerCellDetails details,
          ) {
            final bool isToday = isSameDate(details.date, DateTime.now());
            final bool isBlackOut = isBlackoutDate(details.date);
            final bool isSpecialDate = isSpecialDay(details.date);
            return Container(
              margin: const EdgeInsets.all(2),
              padding: const EdgeInsets.only(top: 10),
              decoration: BoxDecoration(
                color: Colors.blueAccent,
                border:
                    isToday
                        ? Border.all(color: Colors.black, width: 2)
                        : null,
              ),
              child: Column(
                mainAxisSize: MainAxisSize.max,
                mainAxisAlignment: MainAxisAlignment.spaceAround,
                children: <Widget>[
                  Text(
                    details.date.day.toString(),
                    style: const TextStyle(
                      fontSize: 13,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  isBlackOut
                      ? const Icon(Icons.block_sharp, size: 13)
                      : isSpecialDate
                      ? const Row(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          Icon(Icons.cake, size: 13),
                          Icon(Icons.celebration, size: 13),
                          Icon(Icons.audiotrack, size: 13),
                        ],
                      )
                      : Container(),
                ],
              ),
            );
          },
        ),
      ),
    );
  }

  bool isSpecialDay(DateTime date) {
    if (date.day == 20 || date.day == 21 || date.day == 24 || date.day == 25) {
      return true;
    }
    return false;
  }

  bool isSameDate(DateTime date, DateTime dateTime) {
    if (date.year == dateTime.year &&
        date.month == dateTime.month &&
        date.day == dateTime.day) {
      return true;
    }

    return false;
  }

  bool isBlackoutDate(DateTime date) {
    if (date.day == 17 || date.day == 18) {
      return true;
    }
    return false;
  }
}

{% endhighlight %}
{% endtabs %}

![Cell builder](images/builders/cell-builder.jpg)

>**NOTE**
* Use [HijriDateRangePickerCellDetails](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/HijriDateRangePickerCellDetails-class.html) for the [SfHijriDateRangePicker](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfHijriDateRangePicker-class.html).


## See also

* [How to customize the date range picker cells using builder in the Flutter (SfDateRangePicker)](https://support.syncfusion.com/kb/article/10711/how-to-customize-the-date-range-picker-cells-using-builder-in-the-flutter-sfdaterangepicker)
* [How to create timeline Date Picker in Flutter](https://support.syncfusion.com/kb/article/10992/how-to-create-timeline-date-picker-in-flutter)
* [How to customize the special dates using builder in the Flutter Date Range Picker](https://support.syncfusion.com/kb/article/10750/how-to-customize-the-special-dates-using-builder-in-the-flutter-date-range-picker)
