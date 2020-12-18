---
layout: post
title: Builders in Flutter Date Range Picker | Date Picker | Syncfusion
description: Learn about the Builders support in the Syncfusion Flutter Date range picker (SfDateRangePicker) widget and more details.
platform: Flutter
control: SfDateRangePicker
documentation: ug
---
# Builders in flutter date range picker
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
  DateRangePickerController _controller;

  @override
  void initState() {
    _controller = DateRangePickerController();
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: SfDateRangePicker(
              controller: _controller,
			  cellBuilder:
                (BuildContext context, DateRangePickerCellDetails details) {
              final bool isToday = isSameDate(details.date, DateTime.now());
              final bool isBlackOut = isBlackedDate(details.date.day);
              final bool isSpecialDate = isSpecialDay(details.date.day);
              return Container(
                margin: EdgeInsets.all(2),
                padding: EdgeInsets.only(top: kIsWeb ? 5 : 10),
                decoration: BoxDecoration(
                    color: Colors.blueAccent,
                    border: isToday
                        ? Border.all(color: Colors.black, width: 2)
                        : null),
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
}

{% endhighlight %}
{% endtabs %}

![Cell builder](images/builders/cell-builder.png)

