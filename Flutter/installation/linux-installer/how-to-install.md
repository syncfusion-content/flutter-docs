---
layout: post
title: Installing Syncfusion Flutter Linux installer - Syncfusion
description: Learn here about how to install Syncfusion Flutter linux installer after downloading from our Syncfusion website.
platform: flutter
control: Installation and Deployment
documentation: ug

---

# Installing Syncfusion<sup>&reg;</sup> Flutter Linux installer

## Prerequisites

* You must have a Syncfusion account. If you do not have one, sign up at [Syncfusion Account](https://www.syncfusion.com/account/register).
* You must have already downloaded the Syncfusion<sup>&reg;</sup> Flutter Linux installer (ZIP) from the [Linux installer download page](https://help.syncfusion.com/flutter/installation/linux-installer/how-to-download).
* Flutter SDK 1.22 or later installed on the development machine.

## Step-by-Step Installation

The steps below show how to install the Flutter Linux installer.

1. Extract the Syncfusion<sup>&reg;</sup> Flutter Linux installer (`.zip`) file. The files are extracted to your machine.

   ![Welcome wizard](images/Linux_Installer1.png)
   

2. The Linux ZIP file contains the following folders.

   ![License Agreement](images/Linux_Installer2.png)   
   
   > N> An unlock key is not required to install the Linux installer.


3. You can launch the demo source and use the packages included in the Linux installer.


4. To install dependencies for the demo source, run the following command in the Linux terminal:

   ```bash
   flutter pub get
   ```

## License key registration in samples

After installation, the license key is required to register the demo source that is included in the Linux installer. To learn about the steps for license registration for the Flutter Linux installer, refer to the [licensing overview](https://help.syncfusion.com/flutter/licensing/overview).

If you are using Syncfusion<sup>&reg;</sup> controls prior to version 18.3.0.x, follow the steps below to register your license key.

Register the license key in the `main` method of your example and import the `syncfusion_flutter_core/core.dart` library.