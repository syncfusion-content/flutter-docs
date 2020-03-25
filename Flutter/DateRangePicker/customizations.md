---
layout: post
title: Customizations Syncfusion Flutter Date Range Picker | Date Picker
description: Describe how to customize the Syncfusion SfDateRangePicker widget in Flutter | Date Picker | Customization
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Customizations in Flutter DateRangePicker (SfDateRangePicker)

## Month cell customization
You can customize the calendar month view by using the `monthCellStyle` of `SfDateRangePicker`.

•    **Current month dates** – You can customize the date range picker current month dates text style and background by using [textStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/textStyle.html) and [cellDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/cellDecoration.html).

•    **Today date** – You can customize the date range picker today date text style and background by using [todayTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/todayTextStyle.html) and [todayCellDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/todayCellDecoration.html).

•    **Leading dates** – You can hide the leading dates by using [showTrailingAndLeadingDates](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/showTrailingAndLeadingDates.html) property in [DateRangePickerMonthViewSettings](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings-class.html) class. You can also customize the date range picker leading month dates text style and background by using [leadingDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/leadingDatesTextStyle.html) and [leadingDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/leadingDatesDecoration.html).

•    **Trailing dates** - You can hide the trailing dates by using `showTrailingAndLeadingDates` dates property in `DateRangePickerMonthViewSettings` class. You can also customize the date range picker trailing month dates text style and background by using [trailingDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/trailingDatesTextStyle.html) and  [trailingDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/trailingDatesDecoration.html).

•    **Blackout Dates** - You can customize the date range picker blackout dates text style and background by using [blackoutDateTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/blackoutDateTextStyle.html) and [blackoutDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/blackoutDatesDecoration.html).

•    **Disabled dates** – Disable dates text style and background beyond the `minDate` and `maxDate` in range picker by using [disableDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/disabledDatesTextStyle.html) and  [disableDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/disabledDatesDecoration.html).

•    **Special Dates** – You can add special dates to date range picker by using [specialDates](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/specialDates.html) property, and you can also customize the special dates text style and background by using the [specialDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/specialDatesTextStyle.html) and [specialDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/specialDatesDecoration.html).

•    **Weekend Dates** – You can change weekend dates to date range picker by using [weekendDays](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/weekendDays.html) property, and you can also customize the weekend dates text style and background by using the [weekendDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/weekendTextStyle.html) and [weekendDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/weekendDatesDecoration.html).



{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.month,
       monthViewSettings:DateRangePickerMonthViewSettings(blackoutDates:List<DateTime>()
           ..add(DateTime(2020, 03, 26)),
      weekendDays: List<int>()
           ..add(7)..add(6),
      specialDates:List<DateTime>()
           ..add(DateTime(2020, 03, 20))..add(DateTime(2020, 03, 16))..add(DateTime(2020,03,17)),showTrailingAndLeadingDates: true),
      monthCellStyle: DateRangePickerMonthCellStyle(
         blackoutDatesDecoration: BoxDecoration(
               color: Colors.red,
               border: Border.all(color: const Color(0xFFF44436), width: 1),
               shape: BoxShape.circle),
        weekendDatesDecoration: BoxDecoration(
              color: const Color(0xFFDFDFDF),
              border: Border.all(color: const Color(0xFFB6B6B6), width: 1),
              shape: BoxShape.circle),
       specialDatesDecoration: BoxDecoration(
              color: Colors.green,
              border: Border.all(color: const Color(0xFF2B732F), width: 1),
              shape: BoxShape.circle),
       blackoutDateTextStyle: TextStyle(color: Colors.white, decoration: TextDecoration.lineThrough),
      specialDatesTextStyle: const TextStyle(color: Colors.white),
      ),
    )
  );
}

{% endhighlight %}
{% endtabs %}

![Customizations Date Range Picker](images/customizations/customizations.png)

## Month selection cell customization

You can also customize month view section by using the `monthCellStyle` of `SfDateRangePicker`.

•    **Selection date text style** – Selected date text style can be customized using [selectionTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/selectionTextStyle.html) property of `monthCellStyle` which is applicable for `selectionMode` is `single` and `multiple`, it’s also applicable for start and end of selected range text style in `single` and `multi-range` selection

•    **Selection color** – Selected date background color can be customized using [selectionColor](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/selectionColor.html) property of `monthCellStyle` which is applicable for `single` and `multiple` selection.

•    **Range selection text style** – Range selection date text style can be customized using [rangeTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/rangeTextStyle.html) property which is applicable when `selectionMode` is `range` or `multi-range`.

•    **Range selection color** - Range selection color text style can be customized using [startRangeSelectionColor](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/startRangeSelectionColor.html), [endRangeSelectionColor](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/endRangeSelectionColor.html) , [rangeSelectionColor](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/rangeSelectionColor.html)  properties which is applicable when `selectionMode` is `range` or `multi-range`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
      view: DateRangePickerView.month,
      selectionMode: DateRangePickerSelectionMode.range,
      monthCellStyle: DateRangePickerMonthCellStyle(
          selectionTextStyle: const TextStyle(color : Colors.white),
          selectionColor : Colors.blue,
          startRangeSelectionColor: Colors.purple,
         endRangeSelectionColor: Colors.purple,
         rangeSelectionColor: Colors.purpleAccent,
         rangeTextStyle: const TextStyle(color: Colors.white, fontSize: 20),
        ),
      )
   );
}

{% endhighlight %}
{% endtabs %}

## Year cell customization
You can customize the calendar `year`,`decade`,`century` view by using the `yearCellStyle` of `SfDateRangePicker`.

•   **Current year** – You can customize the date range picker current month dates text style and background by using [textStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/textStyle.html) and [cellDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/cellDecoration.html).

•   **Disabled dates** – Disable dates text style and background beyond the date range picker by using [disableDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/disabledDatesTextStyle.html) and  [disableDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/disabledDatesDecoration.html).

•   **Leading dates** –  You can also customize the date range picker leading month dates text style and background by using [leadingDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/leadingDatesTextStyle.html) and [leadingDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/leadingDatesDecoration.html).

•   **Today date** – You can customize the date range picker today date text style and background by using [todayTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/todayTextStyle.html) and [todayCellDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/todayCellDecoration.html).

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
        body: SfDateRangePicker(
        view: DateRangePickerView.month,
        selectionMode: DateRangePickerSelectionMode.range,
        yearCellStyle: DateRangePickerMonthCellStyle(
            disabledDatesDecoration:BoxDecoration(
                   color: const Color(0xFFDFDFDF),
                   border: Border.all(color: const Color(0xFFB6B6B6), width: 1),
                   shape: BoxShape.circle),
            disabledDatesTextStyle: const TextStyle(color: Colors.black),
            leadingDatesDecoration:BoxDecoration(
                   color: const Color(0xFFDFDFDF),
                   border: Border.all(color: const Color(0xFFB6B6B6), width: 1),
                   shape: BoxShape.circle),
            leadingDatesTextStyle: const TextStyle(color: Colors.black),
            textStyle: const TextStyle(color: Colors.blue),
            todayCellDecoration: BoxDecoration(
                   color: const Color(0xFFDFDFDF),
                   border: Border.all(color: const Color(0xFFB6B6B6), width: 1),
                   shape: BoxShape.circle),
           todayTextStyle: const TextStyle(color: Colors.purple),
           )
         ),
     )
}

{% endhighlight %}
{% endtabs %}
