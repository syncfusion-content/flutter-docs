---
layout: post
title: Builders in Flutter Date Range Picker | Date Picker | Syncfusion
description: Learn about Builders support in the Syncfusion Flutter Date range picker (SfDateRangePicker) widget and more details.
platform: Flutter
control: SfDateRangePicker
documentation: ug
---
# Builders in flutter date range picker
The date range picker allows you to create a responsive UI with conditions based on a widget’s details, to design and create your custom view to the month cells and year cells in the date range picker.

## Cell builder
The [DateRangePickerCellBuilder]() allows you to design your custom view and assign the view to the month and year view cells of the date range picker by returning an appropriate widget in the [cellBuilder]() of [SfDateRangePicker]().

[DateRangePickerCellDetails]() - returns the details of the cell.

`date` – The date associate with the cell.
`bound` – Returns the cell bounds.
`visibleDates` – The visible dates of the current view

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
              cellBuilder: (BuildContext context,
                  DateRangePickerCellDetails cellDetails) {
                if (_controller.view == DateRangePickerView.month) {
                  return Container(
                    width: cellDetails.bounds.width,
                    height: cellDetails.bounds.height,
                    alignment: Alignment.center,
                    child: Text(cellDetails.date.day.toString()),
                  );
                } else if (_controller.view == DateRangePickerView.year) {
                  return Container(
                    width: cellDetails.bounds.width,
                    height: cellDetails.bounds.height,
                    alignment: Alignment.center,
                    child: Text(cellDetails.date.month.toString()),
                  );
                } else if (_controller.view == DateRangePickerView.decade) {
                  return Container(
                    width: cellDetails.bounds.width,
                    height: cellDetails.bounds.height,
                    alignment: Alignment.center,
                    child: Text(cellDetails.date.year.toString()),
                  );
                } else {
                  final int yearValue = (cellDetails.date.year ~/ 10) * 10;
                  return Container(
                    width: cellDetails.bounds.width,
                    height: cellDetails.bounds.height,
                    alignment: Alignment.center,
                    child: Text(yearValue.toString() +
                        ' - ' +
                        (yearValue + 9).toString()),
                  );
                }
              })),
    );
  }
}

{% endhighlight %}
{% endtabs %}

