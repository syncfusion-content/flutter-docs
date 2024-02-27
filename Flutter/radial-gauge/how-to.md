---
layout: post
title: Widget Pointer in Flutter Radial Gauge widget | Syncfusion
description: Learn here all about adding and customizing Widget Pointer of Syncfusion Flutter Radial Gauge (SfRadialGauge) widget and more.
platform: Flutter
control: SfRadialGauge
documentation: ug
---

# How to add Syncfusion Radial Gauge Widgets in FlutterFlow framework?

## Overview of FlutterFlow

[FlutterFlow](https://app.flutterflow.io/) is a visual programming tool designed to simplify the development process of Flutter applications, particularly for those who may not have extensive experience with traditional coding. It allows users to create Flutter apps through a drag-and-drop interface, reducing the need for manual coding and speeding up the development cycle.

### Steps for creating the custom widget:

Before proceeding with the steps, please visit [FlutterFlow](https://app.flutterflow.io/) and sign up or sign in. Once logged in, on the start page of FlutterFlow, locate the **+ Create New** button and click on it. A popup for creating a new project will appear. Firstly, provide a name for your project and then select **Create Blank** below the project name. After that, you can choose to **Skip** or **Enable Web** in the project page setup, and click on **Next**. This will navigate you to the project's homepage. Now, follow the steps below to create a custom widget.

## Step 1: Creating the custom widget

1. Navigate to [FlutterFlow](https://app.flutterflow.io/) and select the **Custom Code** option from the left side of the navigation menu.
2. Click on the **+ Add** button. You will be presented with three options: Function, Widget, and Action. Choose **Widget**.
3. Initially, the widget name shows as **NewCustomWidget**. Rename the widget name.
4. Go to widget settings on the right side, and click on the **View Boilerplate Code** button, represented by this icon **[</>]**.
5. A popup will appear; scroll down to find the button labeled **[</>] Copy to Editor**, and click on it.
6. Save the widget.

![Custom Widget](images/how-to/custom-widget.png)

## Step 2: Requirements for including a dependency

To add dependencies to the custom widget, follow these steps:

1. Visit [pub.dev](https://pub.dev/) and search for the [Syncfusion Radial Gauge](https://pub.dev/packages/syncfusion_flutter_gauges) dependency using the search bar.

2. Once you've found the dependency, copy its name along with the version, as demonstrated in the snapshot below.

![Version](images/how-to/copy-version.png)

3. Click on the **+ Add Dependency** button located on the right side of the navigation menu to add the dependency. Once added, save the process.

![Dependency](images/how-to/demo2.png)

## Step 3: Importing packages from the dependency

To import the packages from the dependency, follow these steps:

1. From the [installing](https://pub.dev/packages/syncfusion_flutter_gauges/install) tab on [pub.dev](https://pub.dev/). Scroll down to find the package to copy, as illustrated in the snapshot.

![Package](images/how-to/copy-package.png)

2. Insert the header into the code editor as represented in the snapshot below, and then save the process.

![Import](images/how-to/import-package-flutterflow.png)

## Step 4: Adding the widget code snippet in code editor

To add the code snippet in the code editor, follow these steps:

1. Navigate to the [example](https://pub.dev/packages/syncfusion_flutter_gauges/example) tab on [pub.dev](https://pub.dev/), and scroll down to find the widget code.

2. Instead of copying the entire code, select only the widget snippet, and copy it as illustrated in the picture below.

![Code](images/how-to/code-snippet.png)
    
N> Don't copy the entire code, copy only the widget code.

3. Add the copied code snippet to the code editor and save the process, follow the steps shown in the video.

-> need to add video.

## Step 5: Compiling code

To compile the code:

1. To compile the code, click on the **Compile Code** button located on the right side, as demonstrated in the snapshot, and then save the process.

![Compile code](images/how-to/compile-code.png)

## Step 6: Utilizing the custom widget on a page

To use this custom widget on the page, follow these steps:

1. On the left navigation menu, click on the **Widget Palette** option.
2. You will see a **Diamond** symbol; click on that icon.
3. Once clicked, you will find the custom code widget with your widget file name listed below it.
4. To add it to the page, simply drag and drop it on the page.
5. Adjust the width and height of the widget using the **Custom Widget Properties** available on the right side in [FlutterFlow](https://app.flutterflow.io/).

![Page](images/how-to/page.png)
