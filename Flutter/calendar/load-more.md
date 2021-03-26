---
layout: post 
title: Load More in Syncfusion Flutter Calendar
description: Learn about how to load more appointments to the Syncfusion Flutter Calendar.
platform: flutter
control: SfCalendar
documentation: ug
---

# Load more

SfCalendar provides support to display an interactive view when the calendar view changed, or schedule view reaches its start/end offset. You can use [loadMoreViewBuilder] () builder to display the view while load appointments in calendar.

You should use the [loadMoreWidgetBuilder] () method to load more appointments and then notify the calendar about the changes. The loadMoreWidgetBuilder can be called to load more appointments from this builder by using the loadMoreAppointments function which is passed as a parameter to loadMoreViewBuilder

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

![loadMoreWidgetBuilder]()

>**NOTE**
* This callback will be called after the onViewChanged callback.
* The widget returned from this builder will be removed from SfCalendar when the CalendarDataSource.notifyListeners is called.
