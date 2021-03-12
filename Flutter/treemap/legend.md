---
layout: post
title: Legend in Syncfusion Flutter Treemap | Syncfusion
description: This section explains how to show legend in the Flutter treemap and customize its appearance including text, icon, position, etc.
platform: Flutter
control: SfTreemap
documentation: ug
---

# Legend in the Flutter Treemap

You can provide clear information on the data plotted on the treemap using legend.

## Enable default legend

You can show legend by initializing the `SfTreemap.legend` property. By default, the legend item's text is rendered based on the value of `TreemapLevel.groupMapper` property. The default value of the `legend` property is `null` and hence the legend will not be shown by default.

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
            padding: const EdgeInsets.all(1.5),
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

N>
* Refer the `TreemapLegend.bar`, for showing bar shape legend.

## Bar shape legend

You can show bar shape legend by initializing the `SfTreemap.legend` property as `TreemapLegend.bar`. By default, the legend item's text is rendered based on the value of `TreemapLevel.groupMapper` property.

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
            padding: const EdgeInsets.all(1.5),
            groupMapper: (int index) {
              return _source[index].country;
            },
          ),
        ],
        legend: TreemapLegend.bar(),
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

N>
* Refer the `TreemapLegend`, for showing default legend.

## Icon and text customization

The icons color and text of the legend is applied based on the `TreemapLevel.color` and `TreemapLevel.groupMapper` properties respectively by default. It is possible to customize the legend icons color and texts using the `TreemapColorMapper.color` based on the `TreemapColorMapper.value` or `TreemapColorMapper.from` and `TreemapColorMapper.to` properties. You can also customize the legend item's text using the `TreemapColorMapper.legendItemText` when setting the `TreemapColorMapper.range` color mapper constructor.

{% tabs %}
{% highlight Dart %}

List<SocialMediaUsers> _source;
List<TreemapColorMapper> _colorMappers;

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

   _colorMappers = <TreemapColorMapper>[
      TreemapColorMapper.range(0, 10, Colors.blue[200]),
      TreemapColorMapper.range(10, 20, Colors.deepOrange),
      TreemapColorMapper.range(20, 30, Colors.blue[800]),
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
            padding: const EdgeInsets.all(1.5),
            groupMapper: (int index) {
              return _source[index].country;
            },
            colorValueMapper: (TreemapTile tile) {
              return tile.weight;
            },
          ),
        ],
        colorMappers: _colorMappers,
        legend: TreemapLegend.bar(),
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

## Position

You can position the legend items in different directions using the `TreemapLegend.position` property. The default value of the `position` property is `TreemapLegendPosition.top`. The possible values are `left`, `right`, `top`, and `bottom`.

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
            padding: const EdgeInsets.all(2.5),
            groupMapper: (int index) {
              return _source[index].country;
            },
          ),
        ],
        legend: TreemapLegend(
          position: TreemapLegendPosition.bottom,
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

N>
* Refer the `offset`, for placing the legend in custom position.

## Offset

You can place the legend in custom position using the `TreemapLegend.offset` property. The default value of the `offset` property is `null`.

If the property `TreemapLegend.offset` has been set with the property `TreemapLegend.position` as top, then the legend will be placed in top but with absolute position, i.e. legend will not take dedicated position for it and will be drawn at the top of the map.

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
            padding: const EdgeInsets.all(1.5),
            groupMapper: (int index) {
              return _source[index].country;
            },
          ),
        ],
        legend: TreemapLegend(
          offset: Offset(70, 250),
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

## Overflow mode

<b>For default legend</b>

You can wrap or scroll the legend items using the `TreemapLegend.overflowMode` property. The default value of the `overflowMode` property is `TreemapLegendOverflowMode.wrap`. The possible values are `scroll` and `wrap`.

If the legend position is `left` or `right`, then the default scroll direction is `vertical`.

If the legend position is `top` or `bottom`, then the default scroll direction is `horizontal`.

{% tabs %}
{% highlight Dart %}

List<SocialMediaUsers> _source;

@override
void initState() {
   _source = <SocialMediaUsers>[
      SocialMediaUsers('India', 'Facebook', 25.4),
      SocialMediaUsers('USA', 'Instagram', 19.11),
      SocialMediaUsers('Japan', 'Facebook', 13.3),
      SocialMediaUsers('China', 'Facebook', 12.3),
      SocialMediaUsers('Germany', 'Instagram', 10.65),
      SocialMediaUsers('France', 'Twitter', 7.54),
      SocialMediaUsers('South America', 'Twitter', 5.54),
      SocialMediaUsers('United Kingdom', 'Instagram', 4.93),
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
            padding: const EdgeInsets.all(1.5),
            groupMapper: (int index) {
              return _source[index].country;
            },
          ),
        ],
        legend: TreemapLegend(
          overflowMode: TreemapLegendOverflowMode.scroll,
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

<b>For bar legend</b>

You can wrap or scroll the bar legend items using the `TreemapLegend.overflowMode` property. The default value of the `overflowMode` property is `TreemapLegendOverflowMode.scroll`. The possible values are `scroll` and `wrap`.

If the legend position is `left` or `right`, then the default scroll direction is `vertical`.

If the legend position is `top` or `bottom`, then the default scroll direction is `horizontal`.

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
            padding: const EdgeInsets.all(1.5),
            groupMapper: (int index) {
              return _source[index].country;
            },
          ),
        ],
        legend: TreemapLegend.bar(
          overflowMode: TreemapLegendOverflowMode.scroll,
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

N>
* Refer the `iconSize`, for changing the size of the icon.
