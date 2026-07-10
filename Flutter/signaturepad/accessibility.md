---
layout: post
title: Accessibility in Flutter SignaturePad widget | Syncfusion
description: Learn here all about the accessibility support in Syncfusion Flutter SignaturePad (SfSignaturePad) widget and how to customize it.
platform: flutter
control: SfSignaturePad
documentation: ug
---

# Accessibility in Flutter SignaturePad (SfSignaturePad)

## Screen reader

The [`SfSignaturePad`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad-class.html) can be accessed by screen readers by wrapping the [`SfSignaturePad`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad-class.html) widget with the [`Semantics`](https://api.flutter.dev/flutter/widgets/Semantics-class.html) widget.

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_signaturepad/signaturepad.dart';

class AccessibilityExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Semantics(
          label: 'Syncfusion Flutter SignaturePad',
          hint: 'Draw your signature here',
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
}

{% endhighlight %}
{% endtabs %}

## Sufficient contrast

You can customize the colors of the [`SfSignaturePad`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad-class.html) using the following APIs to ensure sufficient contrast:

* [`Background`](getting-started.md#initialize-signaturepad)
* [`Stroke`](getting-started.md#customize-signature-stroke-color)

## Easier touch targets

The [`SfSignaturePad`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad-class.html) has a touch target size of 48 × 48 pixels, which meets accessibility standards.
