---
layout: post
title: Tooltip in Syncfusion Flutter treemap | Syncfusion
description: This section explains how to show tooltip on a tile and customize its appearance in the Flutter treemap.
platform: Flutter
control: SfTreemap
documentation: ug
---

# Tooltip features in treemap

Tooltip is used to provide information about the tile during the tap, or click interaction. This section helps to learn about how to show tooltip on a tile and customize them.

## Tooltip for the shapes

It is used to clearly indicate the tile information on the tap or click. To show tooltip for the tile, return a widget in `TreemapLevel.tooltipBuilder`. This widget will then be wrapped in the builtin shape which comes with the nose at the bottom.

The `TreemapLevel.tooltipBuilder` will be called with the corresponding tile details every time you interact with the tile i.e., while tapping in touch devices and hover enter in the mouse enabled devices.

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
                padding: EdgeInsets.all(5),
                child: Column(
                  mainAxisSize: MainAxisSize.min,
                  mainAxisAlignment: MainAxisAlignment.start,
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    Row(
                      mainAxisSize: MainAxisSize.min,
                      mainAxisAlignment: MainAxisAlignment.start,
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text('Country          : ',
                            style: TextStyle(color: Colors.white)),
                        Text(tile.group, style: TextStyle(color: Colors.white)),
                      ],
                    ),
                    Row(
                      mainAxisSize: MainAxisSize.min,
                      mainAxisAlignment: MainAxisAlignment.start,
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text('Social media : ',
                            style: TextStyle(color: Colors.white)),
                        Text(tile.weight.toString(),
                            style: TextStyle(color: Colors.white)),
                      ],
                    ),
                  ],
                ),
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

![Treemap tooltip builder](images/tooltip/tile_tooltip_builder.png)

N>
* Refer the `TreemapTooltipSettings`, for customizing the tooltip shape.

## Appearance customization

You can customize the appearance of the tooltip.

* **Background color** - Change the background color of the tooltip in the treemap using the `TreemapTooltipSettings.color` property.
* **Border color** - Change the border color of the tooltip in the treemap using the `TreemapTooltipSettings.borderColor` property.
* **Border width** - Change the border width of the tooltip in the treemap using the `TreemapTooltipSettings.borderWidth` property.
* **Border radius** - Change the border radius of the tooltip in the treemap using the `TreemapTooltipSettings.borderRadius` property.

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
                padding: EdgeInsets.all(5),
                child: Column(
                  mainAxisSize: MainAxisSize.min,
                  mainAxisAlignment: MainAxisAlignment.start,
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    Row(
                      mainAxisSize: MainAxisSize.min,
                      mainAxisAlignment: MainAxisAlignment.start,
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text('Country          : '),
                        Text(tile.group),
                      ],
                    ),
                    Row(
                      mainAxisSize: MainAxisSize.min,
                      mainAxisAlignment: MainAxisAlignment.start,
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text('Social media : '),
                        Text(tile.weight.toString()),
                      ],
                    ),
                  ],
                ),
              );
            },
          ),
        ],
        tooltipSettings: TreemapTooltipSettings(
          color: Colors.orange[300],
          borderColor: Colors.deepOrange[900],
          borderWidth: 2,
          borderRadius: BorderRadius.circular(10),
        ),
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

![Treemap tooltip appearance customization](images/tooltip/tooltip_customization.png)

N>
* Refer the `TreemapLevel.tooltipBuilder`, for enabling tooltip for the tile.
