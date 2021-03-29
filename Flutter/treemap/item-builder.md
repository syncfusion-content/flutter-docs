---
layout: post
title: Place icons and images in Syncfusion Flutter Treemap | Syncfusion
description: This section explains about how to place icons and images on the tiles and customize its appearance in the Flutter treemap.
platform: Flutter
control: SfTreemap
documentation: ug
---

# Item builder in the Flutter Treemap

You can add any type of custom widgets such as image widget as a background of the tiles to easily visualize the type of data that a particular tile shows.

## Add images

You can add images as a background of the tiles using the `TreemapLevel.itemBuilder` callback.

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
            itemBuilder: (BuildContext context, TreemapTile tile) {
              return Align(
                alignment: Alignment.center,
                child: Image.asset(
                  _getImageSource(tile),
                ),
              );
            },
          ),
        ],
      ),
   );
}

String _getImageSource(TreemapTile tile) {
  if (_source[tile.indices[0]].socialMedia == 'Facebook') {
    return 'images/facebook.png';
  } else if (_source[tile.indices[0]].socialMedia == 'Instagram') {
    return 'images/instagram.png';
  } else if (_source[tile.indices[0]].socialMedia == 'Twitter') {
    return 'images/twitter.png';
  }
  return null;
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
* Refer the `TreemapLevel.labelBuilder`, to add labels on the tiles.
