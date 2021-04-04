---
layout: post
title: Colors customization in Syncfusion Flutter Treemap | Syncfusion
description: This section explains the steps required to apply colors to the tiles based on specific value or range of values.
platform: Flutter
control: SfTreemap
documentation: ug
---

# Colors in the Flutter Treemap

This section explains about the customization of color for the tiles based on specific value or range of values.

## Level color

You can apply uniform color to the whole level using the `TreemapLevel.color` property.

{% tabs %}
{% highlight Dart %}

late List<JobVacancyModel> _source;

@override
void initState() {
  _source = <JobVacancyModel>[
      JobVacancyModel(country: 'America', job: 'Sales', vacancy: 70),
      JobVacancyModel(
          country: 'America', job: 'Technical', group: 'Testers', vacancy: 35),
      JobVacancyModel(
          country: 'America',
          job: 'Technical',
          group: 'Developers',
          role: 'Windows',
          vacancy: 105),
      JobVacancyModel(
          country: 'America',
          job: 'Technical',
          group: 'Developers',
          role: 'Web',
          vacancy: 40),
      JobVacancyModel(
          country: 'India', job: 'Technical', group: 'Testers', vacancy: 25),
      JobVacancyModel(
          country: 'India',
          job: 'Technical',
          group: 'Developers',
          role: 'Windows',
          vacancy: 155),
      JobVacancyModel(
          country: 'India',
          job: 'Technical',
          group: 'Developers',
          role: 'Web',
          vacancy: 60),
      JobVacancyModel(
          country: 'Germany', job: 'Technical', group: 'Testers', vacancy: 25),
      JobVacancyModel(
          country: 'Germany',
          job: 'Technical',
          group: 'Developers',
          role: 'Windows',
          vacancy: 155),
   ];
   super.initState();
}

@override
  Widget build(BuildContext context) {
    return Scaffold(
       body: SfTreemap(
          dataCount: _source.length,
          weightValueMapper: (int index) {
            return _source[index].vacancy;
          },
          levels: [
            TreemapLevel(
              groupMapper: (int index) => _source[index].country,
              color: Colors.cyan,
              padding: EdgeInsets.all(1.5),
            ),
            TreemapLevel(
              groupMapper: (int index) => _source[index].job,
              color: Colors.pink[200],
              padding: EdgeInsets.all(10),
            ),
            TreemapLevel(
              groupMapper: (int index) => _source[index].group,
              color: Colors.green[400],
              padding: EdgeInsets.all(10),
            ),
          ],
       ),
   );
}

class JobVacancyModel {
  const JobVacancyModel(
      {required this.country,
      required this.job,
      this.group,
      this.role,
      required this.vacancy});
  final String country;
  final String job;
  final String? group;
  final String? role;
  final double vacancy;
}

{% endhighlight %}
{% endtabs %}

![Levels color customization](images/colors/levels-color.png)

N>
* Refer the `TreemapColorMapper.value`, for applying tile color based on specific value.
* Refer the `TreemapColorMapper.range`, for applying tile color based on range of values.

## Equal color mapping

If you return a value of different type other than the color from the `TreemapLevel.colorValueMapper`, then you must set the `colorMappers` property which is a collection of `TreemapColorMapper`.

The value returned from the `TreemapLevel.colorValueMapper` callback will be used for the comparison in the `TreemapColorMapper.value`. For the matched values, the `TreemapColorMapper.color` will be applied to the respective tiles.

N> You can customize the legend icons color and texts using the `TreemapColorMapper.color` and the `TreemapColorMapper.value` properties respectively.

{% tabs %}
{% highlight Dart %}

late List<SocialMediaUsers> _source;
late List<TreemapColorMapper> _colorMappers;

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
      TreemapColorMapper.value(value: 'Facebook', color: Colors.blue[200]!),
      TreemapColorMapper.value(value: 'Instagram', color: Colors.deepOrange),
      TreemapColorMapper.value(value: 'Twitter', color: Colors.blue[800]!),
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
            labelBuilder: (BuildContext context, TreemapTile tile) {
              return Text(_source[tile.indices[0]].socialMedia);
            },
            colorValueMapper: (TreemapTile tile) {
              return _source[tile.indices[0]].socialMedia;
            },
          ),
        ],
        colorMappers: _colorMappers,
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

![Equal color mapping](images/colors/equal-color-mapping.png)

N>
* Refer the `TreemapColorMapper.range`, for applying color based on range of values.

## Range color mapping

If you return a range value in the `TreemapLevel.colorValueMapper`, then you must set the `colorMappers` property.

The value returned from the `TreemapLevel.colorValueMapper` callback will be checked whether it lies in the `TreemapColorMapper.from` and `TreemapColorMapper.to` range. For the matched values, the `TreemapColorMapper.color` will be applied to the respective tiles.

N> You can customize the legend icons color and texts using the `TreemapColorMapper.color` and the `TreemapColorMapper.from` and `TreemapColorMapper.to` properties.

{% tabs %}
{% highlight Dart %}

late List<SocialMediaUsers> _source;
late List<TreemapColorMapper> _colorMappers;

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
      TreemapColorMapper.range(from: 0, to: 10, color: Colors.blue[200]!),
      TreemapColorMapper.range(from: 10, to: 20, color: Colors.deepOrange),
      TreemapColorMapper.range(from: 20, to: 30, color: Colors.blue[800]!),
    ];
   super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body:  SfTreemap(
        dataCount: _source.length,
        weightValueMapper: (int index) {
          return _source[index].usersInMillions;
        },
        levels: [
          TreemapLevel(
            padding: EdgeInsets.all(2.5),
            groupMapper: (int index) {
              return _source[index].country;
            },
            colorValueMapper: (TreemapTile tile) {
              return tile.weight;
            },
          ),
        ],
        colorMappers: _colorMappers,
     ),
  );
}

class SocialMediaUsers {
  SocialMediaUsers(this.country, this.socialMedia, this.usersInMillions);

  final String country;
  final String socialMedia;
  final double usersInMillions;
}

{% endhighlight %}
{% endtabs %}

![Range color mapping](images/colors/range-color-mapping.png)

N>
* Refer the `TreemapColorMapper.value`, for applying color to the tiles based on the specific value.
