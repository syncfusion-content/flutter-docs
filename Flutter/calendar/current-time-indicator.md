---
layout: post 
title: Current time indicator
description: Learn about time indicator
platform: flutter
control: SfCalendar
documentation: ug
---

# Current time indicator

You can display the current time indicator in all timeslot views of SfCalendar by using the [showCurrentTimeIndicator] () property and you can also customize the color of current time indicator by using the [todayHighlightColor] () property. 

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Container(
      child: SfCalendar(
        view: CalendarView.day,
        showCurrentTimeIndicator: true,
              ),
  );
  }

{% endhighlight %}
{% endtabs %}

![showCurrentTimeIndicator]()