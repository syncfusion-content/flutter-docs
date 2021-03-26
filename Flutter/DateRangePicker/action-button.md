---
layout: post 
title: Action buttons support in Syncfusion Flutter Date Range Picker
description: Learn about how to perform the confirm and cancel buttons to the Syncfusion SfDateRangePicker.
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Action buttons support

You can display action buttons at the bottom of the date range picker by using the [showDateRangePicker] () property of [SfDateRangePicker] (). It allows to confirm and cancel the selection values of SfDateRangePicker

{% tabs %}
{% highlight Dart %}

@override
  Widget build(BuildContext context) {
    return Scaffold(
         body: TextButton(
          child: Text('Show picker'),
          onPressed: () {
            showDialog<Widget>(
                context: context,
                builder: (BuildContext context) {
                  return SfDateRangePicker(
                    showActionButtons: true,
                    onSubmit: (Object value) {
                      Navigator.pop(context);
                    },
                    onCancel: () {
                     Navigator.pop(context);
                    },
                  );
                });
          },
        ));
  }       

{% endhighlight %}
{% endtabs %}

![onCancel and onSubmit]()