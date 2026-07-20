---
layout: post
title: Item Builder in Flutter Treemap widget | Syncfusion
description: Learn here all about the Item Builder feature of Syncfusion Flutter Treemap (SfTreemap) widget and more.
platform: flutter
control: SfTreemap
documentation: ug
---

# Item Builder in Flutter Treemap (SfTreemap)

You can add any type of custom widget, such as an image widget as a background, to easily visualize the type of data that a particular tile shows.

## Add images

You can add images as a background of the tiles using the [`TreemapLevel.itemBuilder`](https://pub.dev/documentation/syncfusion_flutter_treemap/latest/treemap/TreemapLevel/itemBuilder.html) callback.

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_treemap/treemap.dart';

class ItemBuilderExample extends StatefulWidget {
  const ItemBuilderExample({super.key});

  @override
  State<ItemBuilderExample> createState() => _ItemBuilderExampleState();
}

class _ItemBuilderExampleState extends State<ItemBuilderExample> {
  late List<SocialMediaUsers> _source;

  @override
  void initState() {
    _source = <SocialMediaUsers>[
      const SocialMediaUsers('India', 'Facebook', 25.4),
      const SocialMediaUsers('USA', 'Instagram', 19.11),
      const SocialMediaUsers('Japan', 'Facebook', 13.3),
      const SocialMediaUsers('Germany', 'Instagram', 10.65),
      const SocialMediaUsers('France', 'Twitter', 7.54),
      const SocialMediaUsers('UK', 'Instagram', 4.93),
    ];
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: SizedBox(
          height: 400,
          width: 400,
          child: SfTreemap(
            dataCount: _source.length,
            weightValueMapper: (int index) {
              return _source[index].usersInMillions;
            },
            levels: [
              TreemapLevel(
                groupMapper: (int index) {
                  return _source[index].country;
                },
                itemBuilder: (BuildContext context, TreemapTile tile) {
                  return Align(
                    alignment: Alignment.center,
                    child: Image.asset(_getImageSource(tile)!),
                  );
                },
              ),
            ],
          ),
        ),
      ),
    );
  }

  String? _getImageSource(TreemapTile tile) {
    if (_source[tile.indices[0]].socialMedia == 'Facebook') {
      return 'images/facebook.png';
    } else if (_source[tile.indices[0]].socialMedia == 'Instagram') {
      return 'images/instagram.png';
    } else if (_source[tile.indices[0]].socialMedia == 'Twitter') {
      return 'images/twitter.png';
    }
    return null;
  }
}

class SocialMediaUsers {
  const SocialMediaUsers(this.country, this.socialMedia, this.usersInMillions);

  final String country;
  final String socialMedia;
  final double usersInMillions;
}

{% endhighlight %}
{% endtabs %}

![item builder support](images/item-builder/item-builder-support.png)

N>
* Refer the [`Align`](https://api.flutter.dev/flutter/widgets/Align-class.html) widget, to change the position of the widget.
* Refer the [`TreemapLevel.labelBuilder`](https://pub.dev/documentation/syncfusion_flutter_treemap/latest/treemap/TreemapLevel/labelBuilder.html), to add labels on the tiles.