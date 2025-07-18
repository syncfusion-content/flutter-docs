---
layout: post
title: Custom shapes in Flutter Slider widget | Syncfusion
description: Learn here all about adding the custom shapes in Syncfusion Flutter Slider (SfSlider) widget and more.
platform: Flutter
control: SfSlider
documentation: ug
---

# Shapes in Flutter Slider (SfSlider)

This section helps to learn about how to customize the shapes of the slider elements.

## Track shape

You can change the size and shape of the track using the [`trackShape`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/trackShape.html) property in the [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html).

* getPreferredSize() - Returns the size based on the values passed to it.
* paint() - Used to change the track shape.

N>
* You must use the `thumbCenter` and `currentValue` parameters of paint override method for customizing slider track.
* You must use the `startThumbCenter`, `endThumbCenter`, and `currentValues` parameters of paint override method for customizing range slider and range selector track.

{% tabs %}
{% highlight Dart %}

double _value = 5.0;

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: Center(
        child: SfSliderTheme(
          data: SfSliderThemeData(
            activeTrackHeight: 10,
            inactiveTrackHeight: 10,
          ),
          child: SfSlider(
            min: 0.0,
            max: 10.0,
            value: _value,
            trackShape: _SfTrackShape(),
            onChanged: (dynamic newValue) {
              setState(() {
                _value = newValue;
              });
            },
          ),
        ),
      ),
   );
}

class _SfTrackShape extends SfTrackShape {
  @override
  void paint(PaintingContext context, Offset offset, Offset? thumbCenter,
      Offset? startThumbCenter, Offset? endThumbCenter,
      {required RenderBox parentBox,
      required SfSliderThemeData themeData,
      SfRangeValues? currentValues,
      dynamic currentValue,
      required Animation<double> enableAnimation,
      required Paint? inactivePaint,
      required Paint? activePaint,
      required TextDirection textDirection}) {
    Paint paint = Paint()
      ..color = themeData.activeTrackColor!
      ..style = PaintingStyle.stroke
      ..strokeWidth = 1;
    super.paint(context, offset, thumbCenter, startThumbCenter, endThumbCenter,
        parentBox: parentBox,
        themeData: themeData,
        enableAnimation: enableAnimation,
        inactivePaint: inactivePaint,
        activePaint: paint,
        textDirection: textDirection);
  }
}

{% endhighlight %}
{% endtabs %}

![Track shape](images/shapes/track-shape.png)

## Thumb shape

You can change the size and shape of the thumb using the [`thumbShape`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/thumbShape.html) property in the [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html).

* getPreferredSize() - Returns the size based on the values passed to it.
* paint() - Used to change the thumb shape.

N>
* You must use the `currentValue` parameter of paint override method for customizing slider thumb.
* You must use the `currentValues` parameter of paint override method for customizing range slider and range selector thumbs.

{% tabs %}
{% highlight Dart %}

double _value = 4.0;

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: Center(
        child: SfSliderTheme(
          data: SfSliderThemeData(overlayRadius: 0),
          child: SfSlider(
            min: 2.0,
            max: 10.0,
            value: _value,
            thumbShape: _SfThumbShape(),
            onChanged: (dynamic newValue) {
              setState(() {
                _value = newValue;
              });
            },
          ),
        ),
      ),
   );
}

class _SfThumbShape extends SfThumbShape {
  @override
  void paint(PaintingContext context, Offset center,
      {required RenderBox parentBox,
      required RenderBox? child,
      required SfSliderThemeData themeData,
      SfRangeValues? currentValues,
      dynamic currentValue,
      required Paint? paint,
      required Animation<double> enableAnimation,
      required TextDirection textDirection,
      required SfThumb? thumb}) {
      final Path path = Path();

      path.moveTo(center.dx, center.dy);
      path.lineTo(center.dx + 10, center.dy - 15);
      path.lineTo(center.dx - 10, center.dy - 15);
      path.close();
      context.canvas.drawPath(
          path,
          Paint()
            ..color = themeData.activeTrackColor!
            ..style = PaintingStyle.fill
            ..strokeWidth = 2);
  }
}

{% endhighlight %}
{% endtabs %}

![Thumb shape](images/shapes/thumb-shape.png)

## Divider shape

You can change the size and shape of the divider using the [`dividerShape`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/dividerShape.html) property in the [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html).

* getPreferredSize() - Returns the size based on the values passed to it.
* paint() - Used to change the divider shape.

N>
* You must use the `thumbCenter` and `currentValue` parameters of paint override method for customizing slider divider.
* You must use the `startThumbCenter`, `endThumbCenter`, and `currentValues` parameters of paint override method for customizing range slider and range selector divider.

{% tabs %}
{% highlight Dart %}

double _value = 6.0;

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: SfSlider(
        min: 2.0,
        max: 10.0,
        value: _value,
        interval: 1,
        showDividers: true,
        dividerShape: _DividerShape(),
        onChanged: (dynamic newValue) {
          setState(() {
            _value = newValue;
          });
        },
      ),
   );
}

class _DividerShape extends SfDividerShape {
  @override
  void paint(PaintingContext context, Offset center, Offset? thumbCenter,
      Offset? startThumbCenter, Offset? endThumbCenter,
      {required RenderBox parentBox,
      required SfSliderThemeData themeData,
      SfRangeValues? currentValues,
      dynamic currentValue,
      required Paint? paint,
      required Animation<double> enableAnimation,
      required TextDirection textDirection}) {
    bool isActive;

    switch (textDirection) {
      case TextDirection.ltr:
        isActive = center.dx <= thumbCenter!.dx;
        break;
      case TextDirection.rtl:
        isActive = center.dx >= thumbCenter!.dx;
        break;
    }

    context.canvas.drawRect(
        Rect.fromCenter(center: center, width: 5.0, height: 10.0),
        Paint()
          ..isAntiAlias = true
          ..style = PaintingStyle.fill
          ..color = isActive ? themeData.activeTrackColor! : Colors.white);
  }
}

{% endhighlight %}
{% endtabs %}

![Divider shape](images/shapes/divider-shape.png)

## Major and minor ticks shapes

You can change the size and shape of the major and minor ticks using the [`tickShape`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/tickShape.html) and [`minorTickShape`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider/minorTickShape.html) properties in the [`SfSlider`](https://pub.dev/documentation/syncfusion_flutter_sliders/latest/sliders/SfSlider-class.html).

* getPreferredSize() - Returns the size based on the values passed to it.
* paint() - Used to change the ticks shape.

N>
* You must use the `thumbCenter` and `currentValue` parameters of paint override method for customizing slider ticks.
* You must use the `startThumbCenter`, `endThumbCenter`, and `currentValues` parameters of paint override method for customizing range slider and range selector ticks.

{% tabs %}
{% highlight Dart %}

double _value = 5.0;

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: SfSlider(
        min: 0.0,
        max: 10.0,
        value: _value,
        interval: 1,
        showTicks: true,
        minorTicksPerInterval: 3,
        tickShape: _SfTickShape(),
        minorTickShape: _SfMinorTickShape(),
        onChanged: (dynamic newValue) {
          setState(() {
            _value = newValue;
          });
        },
      ),
   );
}

class _SfTickShape extends SfTickShape {
  @override
  void paint(PaintingContext context, Offset offset, Offset? thumbCenter,
      Offset? startThumbCenter, Offset? endThumbCenter,
      {required RenderBox parentBox,
      required SfSliderThemeData themeData,
      SfRangeValues? currentValues,
      dynamic currentValue,
      required Animation<double> enableAnimation,
      required TextDirection textDirection}) {
    final Size tickSize = getPreferredSize(themeData);
    final bool isTickRightOfThumb = offset.dx > thumbCenter!.dx;
    final Color begin = isTickRightOfThumb
        ? themeData.disabledInactiveTickColor
        : themeData.disabledActiveTickColor;
    final Color end = isTickRightOfThumb
        ? themeData.inactiveTickColor
        : themeData.activeTickColor;
    final Paint paint = Paint()
      ..isAntiAlias = true
      ..strokeWidth = tickSize.width
      ..color = ColorTween(begin: begin, end: end).evaluate(enableAnimation)!;

    context.canvas.drawLine(
        Offset(
            offset.dx,
            offset.dy -
                2 -
                math.max(themeData.activeTrackHeight,
                    themeData.inactiveTrackHeight)),
        Offset(
            offset.dx,
            offset.dy -
                2 -
                math.max(themeData.activeTrackHeight,
                    themeData.inactiveTrackHeight) -
                tickSize.height),
        paint);
  }
}

class _SfMinorTickShape extends SfTickShape {
  @override
  void paint(PaintingContext context, Offset offset, Offset? thumbCenter,
      Offset? startThumbCenter, Offset? endThumbCenter,
      {required RenderBox parentBox,
      required SfSliderThemeData themeData,
      SfRangeValues? currentValues,
      dynamic currentValue,
      required Animation<double> enableAnimation,
      required TextDirection textDirection}) {
    final Size minorTickSize = getPreferredSize(themeData);
    final bool isMinorTickRightOfThumb = offset.dx > thumbCenter!.dx;

    final Color begin = isMinorTickRightOfThumb
        ? themeData.disabledInactiveMinorTickColor
        : themeData.disabledActiveMinorTickColor;
    final Color end = isMinorTickRightOfThumb
        ? themeData.inactiveMinorTickColor
        : themeData.activeMinorTickColor;
    final Paint paint = Paint()
      ..isAntiAlias = true
      ..strokeWidth = minorTickSize.width
      ..color = ColorTween(begin: begin, end: end).evaluate(enableAnimation)!;

    context.canvas.drawLine(
        Offset(
            offset.dx,
            offset.dy -
                2 -
                math.max(themeData.activeTrackHeight,
                    themeData.inactiveTrackHeight)),
        Offset(
            offset.dx,
            offset.dy -
                2 -
                math.max(themeData.activeTrackHeight,
                    themeData.inactiveTrackHeight) -
                minorTickSize.height),
        paint);
  }
}

{% endhighlight %}
{% endtabs %}

![Ticks shape](images/shapes/ticks-shape.png)