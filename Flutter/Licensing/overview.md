---
layout: post
title: Syncfusion Licensing Overview - Syncfusion
description: Learn here about Syncfusion licensing for Flutter and the licensing model introduced in version 18.3.0.x.
platform: flutter
control: Essential Studio
documentation: ug
---


# Syncfusion<sup>&reg;</sup> Licensing Overview

License key registration is no longer required for Flutter from version 18.3.0.x. From version 18.3.0.x, Syncfusion Flutter packages are licensed directly through pub.dev; no separate license key registration is required. This applies to both trial and licensed usage.

The Flutter controls from Syncfusion<sup>&reg;</sup> can be used without registering the license keys.

>**Note**: If you are using Syncfusion<sup>&reg;</sup> controls prior to version 18.3.0.x, please follow these steps to register your license key.

## How to register in an application

Register the license key in the **main method** of your application. Follow these steps:

1. Add `syncfusion_flutter_core` as a dependency in your `pubspec.yaml`:
   ```yaml
   dependencies:
     syncfusion_flutter_core: <latest_version>
   ```

2. Import the core package in your main.dart file.

3. Call `SyncfusionLicense.registerLicense()` in the main method before running your app.

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_core/core.dart';

void main() {
  // Register Syncfusion license
  SyncfusionLicense.registerLicense('YOUR LICENSE KEY');
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: const Text('Syncfusion Flutter')),
        body: const Center(child: Text('Hello World')),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

>**Note**: The license key is specific to your Syncfusion account and version. Ensure you use the correct key for your licensed version.

## License key vs. Unlock key

**License Key**: A license key is used to register Syncfusion products on your machine. It validates your subscription and enables all features of the product. License keys are required for older versions of Syncfusion Flutter (prior to 18.3.0.x).

**Unlock Key**: An unlock key is an older form of licensing used in very early versions of Syncfusion products. Unlock keys have been superseded by license keys and are no longer used in modern versions.

For Syncfusion Flutter version 18.3.0.x and later, neither license keys nor unlock keys are required.

## See Also

- [How to generate a Syncfusion license key](https://help.syncfusion.com/common/essential-studio/licensing/how-to-generate)
- [Syncfusion Licensing Knowledge Base](https://www.syncfusion.com/kb/flutter)
- [Installation for older versions](../../installation/how-to-install.md)
