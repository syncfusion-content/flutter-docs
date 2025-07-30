---
layout: post
title: Drag modes in Flutter Range Slider widget | Syncfusion
description: Learn here all about adding the multiple drag modes in Syncfusion Flutter Range Slider (SfRangeSlider) widget and more.
platform: Flutter
control: SfRangeSlider
documentation: ug
---

# Drag modes in Flutter Range Slider (SfRangeSlider)

## On thumb

When [`dragMode`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/dragMode.html) is set to `SliderDragMode.onThumb`, only individual thumb can be moved by dragging it. The nearest thumb will move to the touch position if interaction is done anywhere other than the thumb. The default value of the [`dragMode`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/dragMode.html) property is `SliderDragMode.onThumb`.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2014, 01, 01), DateTime(2016, 01, 01));

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Container(
      height: 400,
      width: 400,
      child: SfRangeSlider(
        min: DateTime(2010, 01, 01),
        max: DateTime(2020, 01, 01),
        dragMode: SliderDragMode.onThumb,
        showLabels: true,
        showTicks: true,
        interval: 2,
        dateIntervalType: DateIntervalType.years,
        dateFormat: DateFormat.y(),
        values: _values,
        enableTooltip: true,
        onChanged: (SfRangeValues newValues) {
          setState(() {
            _values = newValues;
          });
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Drag mode on thumb](images/drag-mode/range-slider-drag-mode-on-thumb.gif)

## Between thumbs

When [`dragMode`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/dragMode.html) is set to `SliderDragMode.betweenThumbs`, both the thumbs can be moved at the same time by dragging in the area between start and end thumbs. The range between the start and end thumb will always be the same. Hence, it is not possible to move the individual thumb.

N> It is applicable for both horizontal and vertical range slider.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2012, 01, 01), DateTime(2016, 01, 01));

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Container(
      height: 400,
      width: 400,
      child: SfRangeSlider(
        min: DateTime(2010, 01, 01),
        max: DateTime(2020, 01, 01),
        dragMode: SliderDragMode.betweenThumbs,
        showLabels: true,
        showTicks: true,
        interval: 2,
        dateIntervalType: DateIntervalType.years,
        dateFormat: DateFormat.y(),
        values: _values,
        enableTooltip: true,
        onChanged: (SfRangeValues newValues) {
          setState(() {
            _values = newValues;
          });
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Drag mode between thumb](images/drag-mode/range-slider-drag-mode-between-thumb.gif)

## Both thumbs

When [`dragMode`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfRangeSlider/dragMode.html) is set to `SliderDragMode.both`, individual thumb can be moved by dragging it, and also both the thumbs can be moved at the same time by dragging in the area between start and end thumbs.

N> It is applicable for both horizontal and vertical range slider.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(DateTime(2014, 01, 01), DateTime(2016, 01, 01));

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Container(
      height: 400,
      width: 400,
      child: SfRangeSlider(
        min: DateTime(2010, 01, 01),
        max: DateTime(2020, 01, 01),
        dragMode: SliderDragMode.both,
        showLabels: true,
        showTicks: true,
        interval: 2,
        dateIntervalType: DateIntervalType.years,
        dateFormat: DateFormat.y(),
        values: _values,
        enableTooltip: true,
        onChanged: (SfRangeValues newValues) {
          setState(() {
            _values = newValues;
          });
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Drag mode both thumb](images/drag-mode/range-slider-drag-mode-both.gif)
