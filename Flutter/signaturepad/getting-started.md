---
layout: post
title: Getting started with Flutter Signature Pad widget | Syncfusion
description: Learn here about getting started with Syncfusion Flutter Signature Pad (SfSignaturePad) widget, its elements, and more.
platform: Flutter
control: SfSignaturePad
documentation: ug
---

# Getting Started with Flutter SignaturePad (SfSignaturePad)
This section explains the steps required to add the SignaturePad widget and its elements such as minimum and maximum stroke widths, stroke color and background color. This section also covers how to save the signature as image, clear the existing signature in SignaturePad and handle the [`onDrawStart`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/onDrawStart.html) and [`onDrawEnd`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/onDrawEnd.html) callbacks in the SignaturePad widget.

To get start quickly with our Flutter SignaturePad widget, you can check on this video.

<style>#FlutterSignaturePadVideoTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='FlutterSignaturePadVideoTutorial' src='https://www.youtube.com/embed/z2fx1Vg518Q'></iframe>

To get start quickly with our Flutter SignaturePad widget, you can check on this video.

<style>#FlutterSignaturePadVideoTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='FlutterSignaturePadVideoTutorial' src='https://www.youtube.com/embed/z2fx1Vg518Q'></iframe>

## Add Flutter SignaturePad to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive#choose-your-ide) documentation.

**Add dependency**

Add the Syncfusion<sup>&reg;</sup> Flutter SignaturePad dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_signaturepad: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter SignaturePad`](https://pub.dev/packages/syncfusion_flutter_signaturepad) package.

**Get packages** 

Run the following command to get the required packages.

{% highlight dart %}

$ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_signaturepad/signaturepad.dart';

{% endhighlight %}
{% endtabs %}

## Initialize SignaturePad

After importing the package, initialize the SignaturePad widget as a child of any widget. Here, the SignaturePad widget is added as a child of the Container widget to get a position and size. Also, applied a background color to show the SignaturePad widget in white background.The default [`backgroundColor`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/backgroundColor.html) is `Colors.transparent`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: Container(
        child: SfSignaturePad(
          backgroundColor: Colors.grey[200],
        ),
        height: 200,
        width: 300,
      ),
    ),
  );
}
	
{% endhighlight %}
{% endtabs %}

![Flutter SignaturePad](images/getting-started/blank_signature_pad.PNG)

## Customize signature stroke color

You can customize the stroke color of the SignaturePad widget by using the [`strokeColor`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/strokeColor.html) property. The default stroke color for the dark theme is `Colors.white` and the default color for the light theme is `Colors.black`.
{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: Container(
        child: SfSignaturePad(
		  strokeColor: Colors.green,
          backgroundColor: Colors.grey[200],
        ),
        height: 200,
        width: 300,
      ),
    ),
  );
}
	
{% endhighlight %}
{% endtabs %}

## Customize signature stroke width

The width of the signature stroke can be customized by setting the [`minimumStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/minimumStrokeWidth.html) and [`maximumStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/maximumStrokeWidth.html) properties. The [`minimumStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/minimumStrokeWidth.html) defines the minimum thickness of the stroke and the [`maximumStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/maximumStrokeWidth.html) defines the maximum thickness of the signature stroke. The stroke will be drawn in [`SfSignaturePad`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/SfSignaturePad.html) based on the speed of the stroke gesture within its minimum and maximum stroke width ranges. So that the signature will be more realistic.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: Container(
        child: SfSignaturePad(
		  minimumStrokeWidth: 3.0,
          maximumStrokeWidth: 6.0,
          backgroundColor: Colors.grey[200],
        ),
        height: 200,
        width: 300,
      ),
    ),
  );
}
	
{% endhighlight %}
{% endtabs %}


## Save signatures as images in Mobile and Desktop platforms

You can save the signature drawn in the SignaturePad as an image using the [`toImage()`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePadState/toImage.html) method as shown in the below code example in Android, iOS and Desktop platforms. Since this [`toImage()`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePadState/toImage.html) method is defined in the state object of SignaturePad, you have to use a global key assigned to the SignaturePad instance to call this method. Optionally, the `pixelRatio` parameter may be used to set the pixel ratio of the image. The higher the pixel ratio value, the high-quality picture you get. The default value of the pixel ratio parameter is 1.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  GlobalKey<SfSignaturePadState> _signaturePadKey = GlobalKey();
  return Scaffold(
    body: Column(
      children: [
        Container(
          child: SfSignaturePad(
            key: _signaturePadKey,
            backgroundColor: Colors.grey[200],
          ),
          height: 200,
          width: 300,
        ),
        RaisedButton(
            child: Text("Save As Image"),
            onPressed: () async {
              ui.Image image =
                 await _signaturePadKey.currentState!.toImage();
            }),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Save signatures as images in web (Desktop browser)

This is similar to the mobile and desktop platforms. You can save the signature drawn in the SignaturePad as an image using the [`toImage()`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePadState/toImage.html) method as shown in the below code example in web platform (Desktop browser). Since this [`toImage()`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePadState/toImage.html) method is defined in the state object of SignaturePad, you have to use a global key assigned to the SignaturePad instance to call this method. Optionally, the `pixelRatio` parameter may be used to set the pixel ratio of the image. The higher the pixel ratio value, the high-quality picture you get. The default value of the pixel ratio parameter is 1.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  GlobalKey<SfSignaturePadState> _signaturePadKey = GlobalKey();
  return Scaffold(
    body: Column(
      children: [
        Container(
          child: SfSignaturePad(
            key: _signaturePadKey,
            backgroundColor: Colors.grey[200],
          ),
          height: 200,
          width: 300,
        ),
        RaisedButton(
            child: Text("Save As Image"),
            onPressed: () async {
              ui.Image image =
                 await _signaturePadKey.currentState!.toImage();
            }),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Save signatures as images in web (mobile browser)

You can save the signature drawn in the SignaturePad as an image using the [`renderToContext2D`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePadState/renderToContext2D.html) method as show in the below code snippet. Since this [`renderToContext2D()`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePadState/renderToContext2D.html) method is defined in the state object of SignaturePad, you have to use a global key assigned to the SignaturePad instance to call this method.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  GlobalKey<SfSignaturePadState> _signaturePadKey = GlobalKey();
  return Scaffold(
    body: Column(
      children: [
        Container(
          child: SfSignaturePad(
            key: _signaturePadKey,
            backgroundColor: Colors.grey[200],
          ),
          height: 200,
          width: 300,
        ),
        RaisedButton(
            child: Text("Save As Image"),
            onPressed: () async {
			
				//Get a html canvas context.
                final canvas = html.CanvasElement(width: 500, height: 500);
                final context = canvas.context2D;
				
				//Get the signature in the canvas context.
                _signaturePadKey.currentState!.renderToContext2D(context);
				
				//Get the image from the canvas context
                final blob = await canvas.toBlob('image/jpeg', 1.0);
				
				//Save the image as Uint8List to use it in local device.
                final completer = Completer<Uint8List>();
                final reader = html.FileReader();
                reader.readAsArrayBuffer(blob);
                reader.onLoad.listen((_) => completer.complete(reader.result));
                Uint8List imageData = await completer.future;

            }),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

N> Since Flutter uses two separate default web renderers, here we have two different code snippets to convert signatures to images in desktop and mobile browsers. Please refer to this Flutter [`web-renderers`](https://docs.flutter.dev/development/tools/web-renderers) page for more details. 

## Clear the existing signature in SignaturePad

You can clear the signature drawn in the SignaturePad using the [`clear()`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePadState/clear.html) method as show in the below code snippet. Since this [`clear()`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePadState/clear.html) method is defined in the state object of SignaturePad, you have to use a global key assigned to the SignaturePad instance to call this method.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  GlobalKey<SfSignaturePadState> _signaturePadKey = GlobalKey();
  return Scaffold(
    body: Column(
      children: [
        Container(
          child: SfSignaturePad(
            key: _signaturePadKey,
            backgroundColor: Colors.grey[200],
          ),
          height: 200,
          width: 300,
        ),
        RaisedButton(
            child: Text("Save As Image"),
            onPressed: () async {
              ui.Image image =
                 _signaturePadKey.currentState!.clear();
            }),
      ],
    ),
  );
}


{% endhighlight %}
{% endtabs %}

## Signature path collection

You can get the path collection of the signature drawn in the SignaturePad using the [`toPathList()`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePadState/toPathList.html) method. Since this [`toPathList()`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePadState/toPathList.html) method is defined in the state object of SignaturePad, you have to use a global key assigned to the SignaturePad instance to call this method.

{% tabs %}
{% highlight Dart %}

GlobalKey<SfSignaturePadState> _signatureGlobalKey = GlobalKey();

@override
Widget build(BuildContext context) {
   return Scaffold(
      body: Column(
        children: [
          Container(
            child: SfSignaturePad(
              key: _signatureGlobalKey,
              backgroundColor: Colors.grey[200],
            ),
            height: 200,
            width: 300,
          ),
          ElevatedButton(
              child: Text("Path collection"),
              onPressed: () {
                List<Path> paths =
                    _signatureGlobalKey.currentState!.toPathList();
              },
          ),
        ],
      ),
   );
}

{% endhighlight %}
{% endtabs %}

## Handle onDrawStart, onDraw, and onDrawEnd callbacks

The widget allows to handle the [`onDrawStart`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/onDrawStart.html), [`onDraw`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/onDraw.html), and [`onDrawEnd`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/onDrawEnd.html) callbacks for every strokes updated to the SignaturePad. The [`onDrawStart`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/onDrawStart.html) callback will be called when the user starts signing on `SfSignaturePad`, the [`onDraw`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/onDraw.html) callback will be called when updating a stroke on the [`SfSignaturePad`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/SfSignaturePad.html) and the [`onDrawEnd`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/onDrawEnd.html) callback will be called when the user completes signing on [`SfSignaturePad`](https://pub.dev/documentation/syncfusion_flutter_signaturepad/latest/signaturepad/SfSignaturePad/SfSignaturePad.html).

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: Container(
        child: SfSignaturePad(
          backgroundColor: Colors.grey[200],
          onDrawStart: () {
            return false;
          },
          onDraw: (offset, time) {
            Offset offsetValue = offset;
            DateTime dateTime = time;
          },
          onDrawEnd: () {
            print("Signature has been completed in Signature Pad");
          },
        ),
        height: 200,
        width: 300,
      ),
   );
}

{% endhighlight %}
{% endtabs %}