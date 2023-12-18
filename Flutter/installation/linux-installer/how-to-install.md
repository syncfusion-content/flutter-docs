---
layout: post
title: Installing Syncfusion Essential Studio Linux installer - Syncfusion
description: Learn here about how to install Syncfusion Essential Studio Linux installer after downloading from our Syncfusion website.
platform: common
control: Essential Studio
documentation: ug
---

# Installing Syncfusion Essential Studio Linux installer

## Overview

Syncfusion provides the Linux installer for the following Essential Studio products.

* Blazor
* Flutter
* ASP.NET Core
* JavaScript
* File Formats
* PDF
* Word
* Excel
* PowerPoint


## Step-by-Step Installation

The steps below show how to install Essential Studio Linux installer.

1. Extract the Syncfusion Essential Studio Linux installer(.zip) file. The files are extracted in your machine.

   ![Welcome wizard](images/Linux_Installer1.png)
   

2. The Linux zip file contains the following folders.

   ![License Agreement](images/Linux_Installer2.png)   
   
   N> The Unlock key is not required to install the Linux installer.


4. You can launch the demo source and use the NuGet packages included in the Linux installer.


5. Run the following command in linux machine to deploy the ASP.NET Core samples
 
  **dotnet restore projectname -s \nuget** in order to restore.

## License key registration in samples

After the installation, the license key is required to register the demo source that is included in the Linux installer. To learn about the steps for license registration for the Flutter Linux installer, please refer to this.

If you are using Syncfusion controls prior to version 18.3.0.x, please follow the following steps to register your license key.

Register the license key in the [main method](https://help.syncfusion.com/flutter/licensing/overview) of your example and import the ‘syncfusion_flutter_core/core.dart’ library.