---
layout: post  
title: Load more support in Syncfusion Flutter Calendar | Lazy loading events
description: Learn about lazily loading more appointments on-demand with an intuitive interface using Flutter Calendar.
platform: flutter
control: SfCalendar
documentation: ug
---

# Load more events in flutter calendar

Calendar provides the support to display an interactive view when the calendar view changed, or the schedule view reaches its start/end offset. You can use the [loadMoreViewBuilder](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/loadMoreWidgetBuilder.html) builder to display the view while loading appointments in the calendar.

You should use the `loadMoreWidgetBuilder` method to load more appointments and then notify the calendar about the changes. The `loadMoreWidgetBuilder` can be called to load more appointments from this builder by using the [loadMoreAppointments](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/LoadMoreWidgetBuilder.html) function which is passed as a parameter to `loadMoreViewBuilder`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SfCalendar(
            controller: _controller,
            loadMoreWidgetBuilder:
                (BuildContext context, CalendarLoadMoreCallback loadMoreAppointments) {
              return FutureBuilder<String>(
                initialData: 'loading',
                future: loadMoreAppointments(),
                builder: (context, snapShot) {
                    return Container(
                        height: _controller.view == CalendarView.schedule ? 50 : double.infinity,
                        width: double.infinity,
                        color: Colors.white38,
                        alignment: Alignment.center,
                        child: CircularProgressIndicator(
                            valueColor:
                                AlwaysStoppedAnimation(Colors.deepPurple)));
                },
              );
            },
            dataSource: _dataSource),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![loadMoreWidgetBuilder](images/load-more/loadmore.gif)

>**NOTE**
* This callback will be called after the `onViewChanged` callback.
* The widget returned from this builder will be removed from the SfCalendar when the `CalendarDataSource.notifyListeners` is called.
