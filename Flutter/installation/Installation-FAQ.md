---
layout: post
title: Installation | Frequently Asked Questions | Syncfusion
description: Learn here about frequently asked questions and answers about installing the Syncfusion Flutter Components.
platform: flutter
control: Installation and Deployment
documentation: ug

---

# Installation - Frequently Asked Questions (FAQs)

This page answers the most common questions about installing the Syncfusion<sup>&reg;</sup> Flutter installer. For a complete list of installation issues and solutions, see the [installation troubleshooting guide](https://help.syncfusion.com/flutter/installation/installation-errors).

## General

### Where can I download the Syncfusion Flutter installer?

You can download the trial or licensed installer from the [Download Free Trial](https://www.syncfusion.com/downloads) or [License & Downloads](https://www.syncfusion.com/account/downloads) page. For platform-specific instructions, see the [offline installer](https://help.syncfusion.com/flutter/installation/offline-installer/how-to-download), [web installer](https://help.syncfusion.com/flutter/installation/web-installer/how-to-download), [Linux installer](https://help.syncfusion.com/flutter/installation/linux-installer/how-to-download), or [Mac installer](https://help.syncfusion.com/flutter/installation/mac-installer/how-to-download) guides.

### Do I need an unlock key to install the trial?

No. An unlock key is required only for licensed installations. Trial installers can be unlocked using your Syncfusion registered login credentials.

## Licensing

### Where do I generate an unlock key?

See [How to generate the Syncfusion unlock key](https://support.syncfusion.com/kb/article/2757/how-to-generate-syncfusion-setup-unlock-key-from-syncfusion-support-account) for step-by-step instructions.

### How do I register the license key in my Flutter app?

Register the license key in the `main` method of your application as shown below:

```dart
import 'package:syncfusion_flutter_core/core.dart';

void main() {
  SyncfusionLicenseProvider.registerLicense('YOUR_LICENSE_KEY');
  runApp(const MyApp());
}
```

For more details, see the [Flutter licensing overview](https://help.syncfusion.com/flutter/licensing/overview).

## Troubleshooting

For troubleshooting installation errors such as invalid trial keys, expired licenses, blocked installers, or controlled-folder-access warnings, see the [installation troubleshooting guide](https://help.syncfusion.com/flutter/installation/installation-errors).