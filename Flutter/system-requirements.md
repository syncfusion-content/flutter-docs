---
layout: post
title: System Requirements for Syncfusion Flutter Widgets
description: Describes the supported platforms and the system requirements to install the Syncfusion Flutter widgets.
platform: flutter
control: Installation and Deployment
documentation: ug
---

# System Requirements for Flutter

The system requirements for using our Syncfusion<sup>&reg;</sup> Flutter platform are as follows:

## Operating Systems

Syncfusion Flutter widgets can be developed on Windows, macOS, or Linux and deployed to mobile, desktop, and web targets. The supported deployment platforms and versions follow the [Flutter supported platforms](https://docs.flutter.dev/reference/supported-platforms) matrix.

**Development operating systems**

* Windows 10, 11
* macOS Catalina (10.15) and later
* Linux (Ubuntu 20.04 LTS to 24.04 LTS)

**Mobile deployment targets**

* Android: API level 24 to 36 (API 23 and earlier unsupported)
* iOS: 13 to 26 (iOS 12 and earlier unsupported)

**Desktop deployment targets**

* Windows: 10, 11 (Windows 8 and earlier unsupported)
* macOS: Catalina (10.15) to Tahoe (26) (Mojave 10.14 and earlier unsupported)
* Linux: Ubuntu 20.04 LTS to 24.04 LTS

**Web deployment targets**

* Chrome (latest 2 stable releases)
* Edge (latest 2 stable releases)
* Firefox (latest 2 stable releases)
* Safari 15.6 and newer

## Hardware Environment

* Processor: x64 or Arm64
* RAM: 8 GB (minimum), 16 GB (recommended)
* Hard disk: up to 3 GB of free space required.

## Development Environment

Install one of the following IDEs along with the Flutter SDK:

* **Android Studio** - Required for Android development (includes the Android SDK and emulator).
* **Xcode** - Required for iOS development (available only on macOS).
* **VS Code** - Recommended lightweight editor that supports all Flutter target platforms.

See the links below for the recommended Flutter SDK installation guides:

* Windows - [`https://docs.flutter.dev/get-started/install/windows`](https://docs.flutter.dev/get-started/install/windows)
* macOS - [`https://docs.flutter.dev/get-started/install/macos`](https://docs.flutter.dev/get-started/install/macos)
* Linux - [`https://docs.flutter.dev/get-started/install/linux`](https://docs.flutter.dev/get-started/install/linux)

To verify your installed Flutter SDK version after setup, run the following command:

{% highlight dart %}

    $ flutter --version

{% endhighlight %}

### SDK Version Compatibility

N> All Syncfusion Flutter packages share the same version number. The version links below point to the `syncfusion_flutter_charts` package as a reference; the same version range applies to every Syncfusion Flutter package.

<table>
    <tr>
        <th style="text-align:center">Flutter SDK Stable Version</th>
        <th style="text-align:center">Syncfusion<sup>&reg;</sup> Compatible Package Version</th>
   </tr>
   <tr>
      <td style="text-align:center">
         <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.44.0-stable.zip">3.44.0</a>
      </td>
      <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/33.2.13">33.2.13</a> <34.1.xx(<a href="https://pub.dev/packages?q=publisher%3Asyncfusion.com&page=2">latest</a>)
      </td>
   </tr>
      <tr>
      <td style="text-align:center">
         <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.41.0-stable.zip">3.41.0</a>
      </td>
      <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/31.2.15">31.2.15</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/33.2.12">33.2.12</a>
      </td>
   </tr>
   <tr>
       <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.38.1-stable.zip">3.38.1</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/31.2.15">31.2.15</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/33.2.12">33.2.12</a>
         </td>
    </tr>
    <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.35.1-stable.zip">3.35.1</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/31.1.20">31.1.20</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/31.2.15">31.2.15</a>
        </td>
    </tr>
    <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.32.0-stable.zip">3.32.0</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/30.1.37">30.1.37</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/31.1.19">31.1.19</a>
        </td>
    </tr>
    <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.29.0-stable.zip">3.29.0</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/29.1.33">29.1.33</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/29.2.11">29.2.11</a>
        </td>
    </tr>
        <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.27.0-stable.zip">3.27.0</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/28.1.36">28.1.36</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/28.2.12">28.2.12</a>
        </td>
    </tr>
    <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.24.0-stable.zip">3.24.0</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/26.2.14">26.2.14</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/28.1.35">28.1.35</a>
        </td>
    </tr>
    <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.22.0-stable.zip">3.22.0</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/25.2.5">25.2.5</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/26.2.13">26.2.13</a>
        </td>
    </tr>
      <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.19.0-stable.zip">3.19.0</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/24.2.7">24.2.7</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/25.2.4">25.2.4</a>
        </td>
    </tr>
      <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.16.0-stable.zip">3.16.0</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/23.2.5">23.2.5</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/24.2.6">24.2.6</a>
        </td>
    </tr>
     <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.13.0-stable.zip">3.13.0</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/22.2.11">22.2.11</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/23.2.4">23.2.4</a>
        </td>
    </tr>
     <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.10.0-stable.zip">3.10.0</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/21.2.9">21.2.9</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/22.2.10">22.2.10</a>
        </td>
    </tr>
     <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.7.0-stable.zip">3.7.0</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/20.4.50">20.4.50</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/21.2.8">21.2.8</a>
        </td>
    </tr>
     <tr>
        <td style="text-align:center">
           <a href="https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.3.0-stable.zip">3.3.0</a>
        </td>
        <td style="text-align:center">>=<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/20.3.47">20.3.47</a> <<a href="https://pub.dev/packages/syncfusion_flutter_charts/versions/20.4.49">20.4.49</a>
        </td>
    </tr>
</table>

### Supported Platforms

Syncfusion Flutter packages are compatible with iOS, Android, Web, Windows, macOS, and Linux. The full list of supported platform versions is maintained by the Flutter team in the [supported deployment platforms](https://docs.flutter.dev/reference/supported-platforms) reference.

