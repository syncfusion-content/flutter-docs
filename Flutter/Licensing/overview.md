---
layout: post
title: Overview of Syncfusion license and unlock keys - Syncfusion
description: Learn here about the Syncfusion license and unlock keys and difference between license and unlock keys.
platform: Flutter
control: Essential Studio
documentation: ug
---


# Syncfusion Licensing Overview

Syncfusion Licensing model is determined by two main factors: the count of the developers in your company and your company's annual gross revenue. You need to have either a commercial license or community license to use the Syncfusion Flutter Widgets in your application. 

The Community License provides free access to all the Syncfusion products for individual developers and small businesses. Companies and individuals with less than $1 million USD in annual gross revenue and 5 or fewer developers are eligible for the Community License.

>**Note**: An entity or organization may not have ever received more than $3,000,000 USD in capital from an outside source, such as private equity or venture capital, in order to be eligible for the Community License.

Customers who do not qualify for the community license can contact sales@syncfusion.com for commercial licensing options.

Under no circumstances can you use this product without (1) either a Community License or a commercial license and (2) without agreeing and abiding by Syncfusion’s license containing all terms and conditions. However, there is no need to register the Syncfusion Flutter license keys or to add the license key anywhere in your Flutter project from version 18.3.0.x. 

The Flutter widgets from Syncfusion can be used without registering the license keys.

>**Note**: If you are using Syncfusion widgets prior to version 18.3.0.x, please follow the following steps to register your license key.

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

## Syncfusion Licensing Terms

The Syncfusion license that contains the terms and conditions can be found at 
https://www.syncfusion.com/content/downloads/syncfusion_license.pdf.

Syncfusion provides implementation but you would subsequently need to have a license to use Flutter. The Flutter engine must be licensed from google directly. We do not license Flutter or the Flutter Engine and provide no license or rights even if you end up with the binaries from us by mistake.