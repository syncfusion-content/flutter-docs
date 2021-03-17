---
layout: post
title: Getting Started for Syncfusion Flutter Treemap | Syncfusion
description: This section explains the steps required to add the treemap widget and its elements such as tooltip, labels and legends.
platform: Flutter
control: SfTreemap
documentation: ug
---

# Getting Started with Flutter Treemap (SfTreemap)
This section explains the steps required to add the treemap widget and its elements such as tooltip, assignable colors based on region, and legends. This section covers only basic features needed to know to get started with Syncfusion treemap.

## Add Flutter treemap to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter treemap dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_treemap: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter Treemap`](https://pub.dev/packages/syncfusion_flutter_treemap/versions) package.

**Get packages**

Run the following command to get the required packages.

{% highlight dart %}

$ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_treemap/treemap.dart';

{% endhighlight %}
{% endtabs %}

## Initialize maps

After importing the package, initialize the treemap widget as a child of any widget.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: SfTreemap(),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Populate data source

To populate the data source, set its count to the `dataCount` property of the treemap. The data will be grouped based on the values returned from the `TreemapLevel.groupMapper` callback. You can have more than one TreemapLevel in the treemap `levels` collection to form a hierarchical treemap. The quantitative value of the underlying data has to be returned from the `weightValueMapper` callback. Based on this value, every tile (rectangle) will have its size.

{% tabs %}
{% highlight Dart %}

List<SocialMediaUsers> _source;

@override
void initState() {
   _source = <SocialMediaUsers>[
      SocialMediaUsers('India', 'Facebook', 25.4),
      SocialMediaUsers('USA', 'Instagram', 19.11),
      SocialMediaUsers('Japan', 'Facebook', 13.3),
      SocialMediaUsers('Germany', 'Instagram', 10.65),
      SocialMediaUsers('France', 'Twitter', 7.54),
      SocialMediaUsers('UK', 'Instagram', 4.93),
   ];
   super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: SfTreemap(
        dataCount: _source.length,
        weightValueMapper: (int index) {
          return _source[index].usersInMillions;
        },
        levels: [
          TreemapLevel(
            groupMapper: (int index) {
              return _source[index].country;
            },
          ),
        ],
      ),
   );
}

class SocialMediaUsers {
  const SocialMediaUsers(this.country, this.socialMedia, this.usersInMillions);

  final String country;
  final String socialMedia;
  final double usersInMillions;
}

{% endhighlight %}
{% endtabs %}

![Treemap default view](images/getting-started/default-view.png)

N>
* Refer the [`SfTreemap.levels`], for adding flat or hierarchical structured treemap.
* Refer the [`SfTreemap.colorMappers`], for customizing the tiles color.

## Add labels

You can add any type of custom widgets to the tiles as labels based on the index using the `TreemapLevel.labelBuilder` property.

{% tabs %}
{% highlight Dart %}

List<SocialMediaUsers> _source;

@override
void initState() {
   _source = <SocialMediaUsers>[
      SocialMediaUsers('India', 'Facebook', 25.4),
      SocialMediaUsers('USA', 'Instagram', 19.11),
      SocialMediaUsers('Japan', 'Facebook', 13.3),
      SocialMediaUsers('Germany', 'Instagram', 10.65),
      SocialMediaUsers('France', 'Twitter', 7.54),
      SocialMediaUsers('UK', 'Instagram', 4.93),
   ];
   super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: SfTreemap(
        dataCount: _source.length,
        weightValueMapper: (int index) {
          return _source[index].usersInMillions;
        },
        levels: [
          TreemapLevel(groupMapper: (int index) {
            return _source[index].country;
          }, labelBuilder: (BuildContext context, TreemapTile tile) {
            return Padding(
              padding: EdgeInsets.all(2.5),
              child: Text(tile.group),
            );
          }),
        ],
      ),
   );
}

class SocialMediaUsers {
  const SocialMediaUsers(this.country, this.socialMedia, this.usersInMillions);

  final String country;
  final String socialMedia;
  final double usersInMillions;
}

{% endhighlight %}
{% endtabs %}

![Treemap labels](images/getting-started/labels.png)

## Add tooltip

You can enable tooltip for any tile in the treemap and able to return the completely customized widget using the `tooltipBuilder` property.

{% tabs %}
{% highlight Dart %}

List<SocialMediaUsers> _source;

@override
void initState() {
   _source = <SocialMediaUsers>[
      SocialMediaUsers('India', 'Facebook', 25.4),
      SocialMediaUsers('USA', 'Instagram', 19.11),
      SocialMediaUsers('Japan', 'Facebook', 13.3),
      SocialMediaUsers('Germany', 'Instagram', 10.65),
      SocialMediaUsers('France', 'Twitter', 7.54),
      SocialMediaUsers('UK', 'Instagram', 4.93),
   ];
   super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: SfTreemap(
        dataCount: _source.length,
        weightValueMapper: (int index) {
          return _source[index].usersInMillions;
        },
        levels: [
          TreemapLevel(
            groupMapper: (int index) {
              return _source[index].country;
            },
            tooltipBuilder: (BuildContext context, TreemapTile tile) {
              return Padding(
                padding: const EdgeInsets.all(10),
                child: Text(
                    'Country          : ${tile.group}\nSocial media : ${tile.weight}M',
                    style: TextStyle(color: Colors.white)),
              );
            },
          ),
        ],
      ),
   );
}

class SocialMediaUsers {
  const SocialMediaUsers(this.country, this.socialMedia, this.usersInMillions);

  final String country;
  final String socialMedia;
  final double usersInMillions;
}

{% endhighlight %}
{% endtabs %}

![Treemap tooltip](images/getting-started/tooltip.png)

## Add legend

You can show legend by initializing the `legend` property in the `SfTreemap`. It is possible to customize the legend item's color and text using the `SfTreemap.colorMappers` property.

{% tabs %}
{% highlight Dart %}

List<SocialMediaUsers> _source;

@override
void initState() {
   _source = <SocialMediaUsers>[
      SocialMediaUsers('India', 'Facebook', 25.4),
      SocialMediaUsers('USA', 'Instagram', 19.11),
      SocialMediaUsers('Japan', 'Facebook', 13.3),
      SocialMediaUsers('Germany', 'Instagram', 10.65),
      SocialMediaUsers('France', 'Twitter', 7.54),
      SocialMediaUsers('UK', 'Instagram', 4.93),
   ];
   super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: SfTreemap(
        dataCount: _source.length,
        weightValueMapper: (int index) {
          return _source[index].usersInMillions;
        },
        levels: [
          TreemapLevel(
            groupMapper: (int index) {
              return _source[index].country;
            },
          ),
        ],
        legend: TreemapLegend(),
      ),
   );
}

class SocialMediaUsers {
  const SocialMediaUsers(this.country, this.socialMedia, this.usersInMillions);

  final String country;
  final String socialMedia;
  final double usersInMillions;
}

{% endhighlight %}
{% endtabs %}

![Treemap legend](images/getting-started/legend.png)
