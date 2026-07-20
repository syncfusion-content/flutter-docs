---
layout: post
title: Installing Syncfusion Flutter Linux installer - Syncfusion
description: Learn here how to install the Syncfusion Flutter Linux installer after downloading it from the Syncfusion website.
platform: flutter
control: Installation and Deployment
documentation: ug

---

# Installing Syncfusion<sup>&reg;</sup> Flutter Linux installer

## Step-by-step installation

The steps below show how to install Flutter Linux installer.

1. Extract the Syncfusion<sup>&reg;</sup> Flutter Linux installer (.zip) file. The files are extracted on your machine.

   ![Welcome wizard](images/Linux_Installer1.png)
   

2. The Linux zip file contains the following folders:
   - Samples
   - Shortcuts
   - Licensing

   ![License Agreement](images/Linux_Installer2.png)   
   
   N> The Unlock key is not required to install the Linux installer.


3. You can launch the samples from the extracted folders to explore the Syncfusion Flutter widgets.

4. You can access the pub.dev packages included in the Linux installer.

## License key registration in samples

After the installation, if you are using Syncfusion<sup>&reg;</sup> controls prior to version 18.3.0.x, you must register the license key. To learn about the steps for license registration, please refer to the [licensing overview](https://help.syncfusion.com/flutter/licensing/overview).

Register the license key in the **main method** of your application and import the `syncfusion_flutter_core/core.dart` library:

```dart
import 'package:syncfusion_flutter_core/core.dart';

void main() {
  // Register Syncfusion license
  SyncfusionLicense.registerLicense('YOUR LICENSE KEY');
  runApp(const MyApp());
}
```