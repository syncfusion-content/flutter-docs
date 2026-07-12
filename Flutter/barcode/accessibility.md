---
layout: post
title: Accessibility in Flutter Barcodes widget | Syncfusion 
description: Learn here all about the accessibility feature of Syncfusion Flutter Barcodes (SfBarcodeGenerator) widget and more.
platform: flutter
control: SfBarcodeGenerator
documentation: ug
---

# Accessibility in Flutter Barcodes (SfBarcodeGenerator)

## Sufficient contrast

The [`SfBarcodeGenerator`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/SfBarcodeGenerator-class.html) [theming](https://help.syncfusion.com/flutter/themes) support offers a consistent and standardized look, as well as the ability to customize colors for all UI elements.

You can customize colors for the following elements:
* [Bar color](https://help.syncfusion.com/flutter/barcode/barcode-customization)
* [Background color](https://help.syncfusion.com/flutter/barcode/barcode-customization)

## Large fonts

The [`SfBarcodeGenerator`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/SfBarcodeGenerator-class.html) automatically adjusts font size based on device settings and scales according to the [`MediaQueryData.textScaleFactor`](https://api.flutter.dev/flutter/widgets/MediaQueryData/textScaleFactor.html). It also allows you to change the font size of all text elements in the barcode generator.
* [Input value of barcode](https://help.syncfusion.com/flutter/barcode/barcode-customization#text-customization)

## Screen reader support

The [`SfBarcodeGenerator`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/SfBarcodeGenerator-class.html) supports Flutter's built-in [`Semantics`](https://api.flutter.dev/flutter/widgets/Semantics-class.html) framework, which provides voice-over and TalkBack screen reader support. You can wrap the barcode generator in a [`Semantics`](https://api.flutter.dev/flutter/widgets/Semantics-class.html) widget and provide a descriptive label using the [`label`](https://api.flutter.dev/flutter/widgets/Semantics/label.html) property so that screen readers can announce the barcode's input value. Alternatively, the [`Semantics`](https://api.flutter.dev/flutter/widgets/Semantics-class.html) widget can be placed on the parent container holding the [`SfBarcodeGenerator`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/SfBarcodeGenerator-class.html). This improves accessibility for visually impaired users, especially since barcodes are inherently visual elements that cannot be interpreted by screen readers without a meaningful label.