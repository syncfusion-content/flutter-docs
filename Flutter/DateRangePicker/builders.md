---
layout: post
title: Builders in Flutter Date Range Picker widget | Syncfusion
description: Learn here all about Bulders feature of Syncfusion Flutter Date Range Picker (SfDateRangePicker) widget and more.
platform: Flutter
control: SfDateRangePicker
documentation: ug
---
# Builders in Flutter Date Range Picker (SfDateRangePicker)
The date range picker allows you to create a responsive UI with the conditions based on a widget’s details, and to design and create your custom view to the month cells and year cells in the date range picker.

## Cell builder
The [DateRangePickerCellBuilder](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerCellBuilder.html) allows you to design your custom view and assign the view to the month and year view cells of the date range picker by returning an appropriate widget in the [cellBuilder](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/cellBuilder.html) of [SfDateRangePicker](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker-class.html).

[DateRangePickerCellDetails](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerCellDetails-class.html): Returns the details of the cell.

`date`: The date associate with the cell.
`bound`: Returns the cell bounds.
`visibleDates`: The visible dates of the current view.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp> {
  final DateRangePickerController _controller = DateRangePickerController();
  
  @override
  Widget build(BuildContext context) {
   return MaterialApp(
    home: Scaffold(
        body: SfDateRangePicker(
      controller: _controller,
      cellBuilder:
          (BuildContext context, DateRangePickerCellDetails details) {
        final bool isToday = isSameDate(details.date, DateTime.now());
        final bool isBlackOut = isBlackedDate(details.date);
        final bool isSpecialDate = isSpecialDay(details.date);
        return Container(
          margin: EdgeInsets.all(2),
          padding: EdgeInsets.only(top: kIsWeb ? 5 : 10),
          decoration: BoxDecoration(
              color: Colors.blueAccent,
              border:
                  isToday ? Border.all(color: Colors.black, width: 2) : null),
          child: Column(
            mainAxisSize: MainAxisSize.max,
            mainAxisAlignment: MainAxisAlignment.spaceAround,
            children: <Widget>[
              Text(
                details.date.day.toString(),
                style: TextStyle(
                  fontSize: kIsWeb ? 11 : 15,
                  fontWeight: FontWeight.bold,
                ),
              ),
              isBlackOut
                  ? Icon(
                      Icons.block_sharp,
                      size: 13,
                    )
                  : isSpecialDate
                      ? Row(
                          mainAxisAlignment: MainAxisAlignment.center,
                          children: [
                            Icon(
                              Icons.cake,
                              size: 13,
                            ),
                            Icon(
                              Icons.celebration,
                              size: 13,
                            ),
                            Icon(
                              Icons.audiotrack,
                              size: 13,
                            )
                          ],
                        )
                      : Container()
            ],
          ),
        );
      },
    )),
  );
}

bool isSpecialDay(DateTime date) {
  /// Check the condition for special date here.
}

bool isSameDate(DateTime date, DateTime dateTime) {
  /// Check condition for today date.
}

bool isBlackedDate(DateTime date) {
  /// Check condition for blackout date here.
}

{% endhighlight %}
{% endtabs %}

![Cell builder](images/builders/cell-builder.png)

>**NOTE** 
* Use [HijriDateRangePickerCellDetails]() for the [SfHijriDateRangePicker](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfHijriDateRangePicker-class.html).


## See also

* [How to customize the date range picker cells using builder in the Flutter (SfDateRangePicker)](https://www.syncfusion.com/kb/12208/how-to-customize-the-date-range-picker-cells-using-builder-in-the-flutter-sfdaterangepicker)
* [How to create timeline Date Picker in Flutter](https://www.syncfusion.com/kb/12474/how-to-create-timeline-date-picker-in-flutter)
* [How to customize the special dates using builder in the Flutter Date Range Picker](https://www.syncfusion.com/kb/12374/how-to-customize-the-special-dates-using-builder-in-the-flutter-date-range-picker)