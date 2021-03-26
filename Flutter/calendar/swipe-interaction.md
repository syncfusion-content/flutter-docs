---
layout: post 
title: Enable or disable swipe interaction in Syncfusion Flutter Calendar
description: Learn about how to swipe the interaction to the Syncfusion Flutter Calendar.
platform: flutter
control: SfCalendar
documentation: ug
---

# Enable or disable swipe interaction

You can customize the swipe interaction of SfCalendar by using the [viewNavigationMode] (). You can allow or restrict to switching to previous or next views through the swipe interaction of SfCalendar. By default , the [viewNavigationMode] () is set as snap.

{% tabs %}
{% highlight Dart %}

@override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfCalendar(
         view: CalendarView.day,
        viewNavigationMode: ViewNavigationMode.snap,
    ),);
  }

{% endhighlight %}
{% endtabs %}

>**NOTE**
* Not applicable when the view set as schedule. 
* It will not impact scrolling timeslot views, CalendarController.forward(), CalendarController.backward() and showNavigationArrow
