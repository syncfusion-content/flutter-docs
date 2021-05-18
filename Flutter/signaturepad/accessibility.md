---
layout: post
title:  Accessibility in Flutter SignaturePad widget | Syncfusion
description: Learn here all about the accessibility support in Syncfusion Flutter SignaturePad (SfSignaturePad) widget and how to customize it.
platform: Flutter
control: SfSignaturePad
documentation: ug
---

# Accessibility in Flutter SignaturePad (SfSignaturePad)

## Screen reader

The [`SfSignaturePad`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad-class.html) can be accessed by the screen readers by wrapping the [`SfSignaturePad`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad-class.html) widget to the [`Semantics`](https://api.flutter.dev/flutter/widgets/Semantics-class.html) widget.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: Semantics(
        label: 'Syncfusion Flutter SignaturePad',
        hint: 'Mark your signature in this',
        child: Container(
          child: SfSignaturePad(
            strokeColor: Colors.black,
            backgroundColor: Colors.white,
            maximumStrokeWidth: 5,
            minimumStrokeWidth: 1,
          ),
          width: 200,
          height: 200,
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Sufficient contrast

You can customize the color of the [`SfSignaturePad`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad-class.html) using the following APIs for the sufficient contrast.

* [`Background`](https://help.syncfusion.com/flutter/signaturepad/getting-started#initialize-signaturepad)
* [`Stroke`](https://help.syncfusion.com/flutter/signaturepad/getting-started#customize-signature-stroke-color)

## Easier touch targets

The [`SfSignaturePad`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad-class.html) has touch target as 48 * 48 as per the standard.
