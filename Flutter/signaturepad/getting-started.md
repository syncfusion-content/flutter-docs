---
layout: post
title: Getting Started for Syncfusion Flutter Signature Pad | Syncfusion
description: This section explains how to use the signature pad widget in flutter applciations and how to save a signature as image in flutter applciations.
platform: Flutter
control: SfSignaturePad
documentation: ug
---

# Getting Started with Flutter Signature Pad (SfSignaturePad)
This section explains the steps required to add the Signature Pad widget and its elements such as minimum and maximum stroke widths, stroke color and background color. This section also covers how to save the signature as image, clear the existing signature in Signature Pad and handle the `onSignStart` and `onSaveEnd` callbacks in the Signature Pad widget.

## Add Flutter Signature Pad to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter SignaturePad dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_signaturepad: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter Signature Pad`](https://pub.dev/packages/syncfusion_flutter_sliders/versions) package.

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

## Initialize Signature Pad

After importing the package, initialize the signature pad widget as a child of any widget. Here, the signature pad widget is added as a child of the Container widget to get a position and size. Also, applied a background color to show the signature pad widget in white background.The default `backgroundColor` is `Colors.transparent`.

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

![Default Signature Pad](images/getting-started/blank_signature_pad.PNG)

## Customize stroke color

You can customize the stroke color of the Signature Pad widget by using the 'strokeColor' property. The default stroke color for the dark theme is `Colors.white` and the default color for the light theme is `Colors.black`.
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

## Customize stroke width

The width of the signature stroke can be customized by setting the `minimumStrokeWidth` and `maximumStrokeWidth` properties. The `minimumStrokeWidth` defines the minimum thickness of the stroke and the `maximumStrokeWidth` defines the maximum thickness of the signature stroke. The stroke will be drawn in `SfSignaturePad` based on the speed of the stroke gesture within its minimum and maximum stroke width ranges. So that the signature will be more realistic.

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


## Save as image in Android and iOS platforms

You can save the signature drawn in the SignaturePad as an image using the toImage() method as shown in the below code example in Android and iOS platforms. Since this toImage() method is defined in the state object of Signature Pad, you have to use a global key assigned to the Signature Pad instance to call this method.

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
                 await _signaturePadKey.currentState.toImage();
            }),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Save as image in web platform

You can save the signature drawn in the SignaturePad as an image using the renderToContext2D() method as show in the below code snippet. Since this renderToContext2D() method is defined in the state object of Signature Pad, you have to use a global key assigned to the Signature Pad instance to call this method.

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
                _signaturePadKey.currentState.renderToContext2D(context);
				
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

## Clear the existing signature in Signature Pad
You can clear the signature drawn in the SignaturePad using the clear() method as show in the below code snippet. Since this clear() method is defined in the state object of Signature Pad, you have to use a global key assigned to the Signature Pad instance to call this method.

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
                 _signaturePadKey.currentState.clear();
            }),
      ],
    ),
  );
}


{% endhighlight %}
{% endtabs %}

## Handle onSignStart and onSignEnd callbacks

The widget allows to handle the onSignStart and onSignEnd callbacks for every strokes updated to the Signature Pad.The `onSignStart` callback will be called when the user starts signing on `SfSignaturePad`and the `onSignEnd` callback will be called when the user completes signing on `SfSignaturePad`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Column(
      children: [
        Container(
          child: SfSignaturePad(
            backgroundColor: Colors.grey[200],
			onSignStart: ()=> {
               print("Signature has been initiated in Signature Pad");
            },
			onSignEnd: ()=> {
               print("Signature has been completed in Signature Pad");
            },
          ),
          height: 200,
          width: 300,
        ),
        RaisedButton(
            child: Text("Save As Image"),
            onPressed: () async {
              ui.Image image =
                 _signaturePadKey.currentState.clear();
            }),
      ],
    ),
  );
}


{% endhighlight %}
{% endtabs %}