---
layout: post
title: Installing Syncfusion Flutter Mac installer - Syncfusion
description: Learn here about how to install Syncfusion Flutter mac installer after downloading from our Syncfusion website.
platform: flutter
control: Installation and Deployment
documentation: ug

---

# Installing Syncfusion<sup>&reg;</sup> Flutter Mac Installer

The Essential Studio<sup>&reg;</sup> Flutter Mac installer provides the Syncfusion<sup>&reg;</sup> Flutter components, samples, and utilities for use in your Flutter development environment.

## Prerequisites

* You must have already downloaded the Syncfusion<sup>&reg;</sup> Flutter Mac installer (DMG) from the [Mac installer download page](how-to-download.md).
* A Mac running macOS Catalina (10.15) or later (see [System Requirements](https://help.syncfusion.com/flutter/system-requirements) for the latest supported versions).
* Flutter SDK 3.0 or later installed on your development machine.
* You must have a Syncfusion account. If you do not have one, sign up at [Syncfusion Account](https://www.syncfusion.com/account/register).


## Steps to resolve the warning message in Catalina OS or later

   While running the Essential Studio<sup>&reg;</sup> Flutter Mac Installer on macOS Catalina or later, the alert below may be displayed.

   ![Alert Image](images/Mac_Catalina_MacOS_Alert1.png)  
     
   If you receive this alert, follow the steps below to resolve this.   

   1.	Right-click the downloaded DMG file.
   2.	Select the **Open With** option and choose **DiskImageMounter (Default)**. The pop-up below appears.

	    ![pop-up Image](images/Mac_Catalina_MacOS_Alert2.png)

   3.	When you click **Open**, the installer window opens.

## Step-by-Step Installation

The steps below show how to install the Essential Studio<sup>&reg;</sup> Flutter Mac installer.

1. Locate the downloaded DMG file and open it by double-clicking it.

   ![Mounted DMG](images/Mac_Installer1.png)
   

2. This action automatically mounts the disk image and creates a virtual drive on your desktop or in the Finder sidebar.

   ![Mounted disk image](images/Mac_Installer2.png)   
   

3. In the mounted disk, drag the **Syncfusion Essential Studio Flutter** application to the **Applications** folder shortcut.

   ![Syncfusion Essential Studio Flutter in mounted disk](images/Mac_Installer3.png)
   
   > N> An unlock key is not required to install the Mac installer. The Syncfusion<sup>&reg;</sup> Essential Studio Flutter Mac installer can be used for development purposes without registering the unlock key.


4. Wait for the file copy to complete.

   ![Copying to Applications](images/Mac_Installer4.png)


5. Open the **Applications** folder to explore the Syncfusion<sup>&reg;</sup> Essential Studio Mac installer.

   ![Applications folder](images/Mac_Installer5.png)


6. To remove the DMG file, right-click the virtual drive on your desktop or in the Finder sidebar and select **Eject**.

   ![Eject virtual drive](images/Mac_Installer6.png)

   
## License key registration in samples

After installation, the license key is required to register the demo source that is included in the Mac installer. To learn about the steps for license registration for the Flutter Mac installer, refer to the [licensing overview](https://help.syncfusion.com/flutter/licensing/overview).

Register the license key in the `main` method of your application by importing the license package and calling `SyncfusionLicenseProvider.registerLicense`:

```dart
import 'package:syncfusion_flutter_core/core.dart';

void main() {
  SyncfusionLicenseProvider.registerLicense('YOUR_LICENSE_KEY');
  runApp(const MyApp());
}
```

> N> If you are using Syncfusion<sup>&reg;</sup> controls prior to version 18.3.0.x, refer to the [legacy licensing guide](https://help.syncfusion.com/flutter/licensing/overview) for older registration steps.