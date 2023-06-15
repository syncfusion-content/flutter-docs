---
layout: post
title: Overview of Syncfusion license and unlock keys - Syncfusion
description: Learn here about the Syncfusion license and unlock keys and difference between license and unlock keys.
platform: Flutter
control: Essential Studio
documentation: ug
---


# Syncfusion Licensing Overview

The License key registration is no longer required for Flutter from version 18.3.0.x. So, there is no need to generate or register Syncfusion Flutter license keys in your Flutter projects. 

The Flutter controls from Syncfusion can be used without registering the license keys.

>**Note**: If you are using Syncfusion controls prior to version 18.3.0.x, please follow these following steps to register your license key.

## How To Register In An Application

Register the license key in the **main method** of your example and import the ‘syncfusion_flutter_core/core.dart' library.

{% tabs %} 
{% highlight Dart %}

    // Refer the core package
    import 'package:syncfusion_flutter_core/core.dart';

    void main() { 
      // Register Syncfusion license 
    SyncfusionLicense.registerLicense("YOUR LICENSE KEY"); 
    return runApp(MyApp()); 
    }

{% endhighlight %}
{% endtabs %}
