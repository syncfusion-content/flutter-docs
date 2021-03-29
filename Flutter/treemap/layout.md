---
layout: post
title: Different layouts in Syncfusion Flutter Treemap | Syncfusion
description: This section explains the steps required to visualize the treemap widget in the different layouts based on slice, dice, and squarified algorithms.
platform: Flutter
control: SfTreemap
documentation: ug
---

# Layouts in Flutter Treemap

This section explains the different layouts in the treemap widget. The available layouts are,

* Squarified
* Slice
* Dice

## Squarified

The squarified layout will arrange the rectangles in a row and wrap them to the next row according to the available size. The size of the particular rectangle is based on the value returned from `weightValueMapper` callback. By default, squarified layout is used.

{% tabs %}
{% highlight Dart %}

late List<PopulationModel> _dataSource;

@override
void initState() {
   _dataSource = <PopulationModel>[
      PopulationModel(continent: 'Asia', populationInMillions: 25.4),
      PopulationModel(continent: 'South America', populationInMillions: 19.11),
      PopulationModel(continent: 'North America', populationInMillions: 13.3),
      PopulationModel(continent: 'Europe', populationInMillions: 10.65),
      PopulationModel(continent: 'Africa', populationInMillions: 7.54),
      PopulationModel(continent: 'Australia', populationInMillions: 4.93),
   ];
   super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: SfTreemap(
        dataCount: _dataSource.length,
        weightValueMapper: (int index) {
          return _dataSource[index].populationInMillions;
        },
        levels: [
          TreemapLevel(
            groupMapper: (int index) {
              return _dataSource[index].continent;
            },
            color: Colors.teal[200],
            padding: const EdgeInsets.all(1.5),
          ),
        ],
      ),
   );
}

class PopulationModel {
  const PopulationModel({
    required this.continent,
    required this.populationInMillions,
  });

  final String continent;
  final double populationInMillions;
}

{% endhighlight %}
{% endtabs %}

![Squarified layout structure](images/layout/squarified-layout.png)

## Slice

The slice layout will start to arrange each rectangle in a horizontal direction and the size of the rectangle will be based on the value returned from `weightValueMapper` callback and the available height.

{% tabs %}
{% highlight Dart %}

late List<PopulationModel> _dataSource;

@override
void initState() {
   _dataSource = <PopulationModel>[
      PopulationModel(continent: 'Asia', populationInMillions: 25.4),
      PopulationModel(continent: 'South America', populationInMillions: 19.11),
      PopulationModel(continent: 'North America', populationInMillions: 13.3),
      PopulationModel(continent: 'Europe', populationInMillions: 10.65),
      PopulationModel(continent: 'Africa', populationInMillions: 7.54),
      PopulationModel(continent: 'Australia', populationInMillions: 4.93),
   ];
   super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: SfTreemap.slice(
        dataCount: _dataSource.length,
        weightValueMapper: (int index) {
          return _dataSource[index].populationInMillions;
        },
        levels: [
          TreemapLevel(
            groupMapper: (int index) {
              return _dataSource[index].continent;
            },
            color: Colors.teal[200],
            padding: const EdgeInsets.all(1.5),
          ),
        ],
      ),
   );
}

class PopulationModel {
  const PopulationModel({
    required this.continent,
    required this.populationInMillions,
  });

  final String continent;
  final double populationInMillions;
}

{% endhighlight %}
{% endtabs %}

![Slice layout structure](images/layout/slice-layout.png)

## Dice

The dice structure will start to arrange each rectangle in the vertical direction and the size of the rectangle will be based on the value returned from the `weightValueMapper` callback and the available width.

{% tabs %}
{% highlight Dart %}

late List<PopulationModel> _dataSource;

@override
void initState() {
   _dataSource = <PopulationModel>[
      PopulationModel(continent: 'Asia', populationInMillions: 25.4),
      PopulationModel(continent: 'South America', populationInMillions: 19.11),
      PopulationModel(continent: 'North America', populationInMillions: 13.3),
      PopulationModel(continent: 'Europe', populationInMillions: 10.65),
      PopulationModel(continent: 'Africa', populationInMillions: 7.54),
      PopulationModel(continent: 'Australia', populationInMillions: 4.93),
   ];
   super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: SfTreemap.dice(
        dataCount: _dataSource.length,
        weightValueMapper: (int index) {
          return _dataSource[index].populationInMillions;
        },
        levels: [
          TreemapLevel(
            groupMapper: (int index) {
              return _dataSource[index].continent;
            },
            color: Colors.teal[200],
            padding: const EdgeInsets.all(1.5),
          ),
        ],
      ),
   );
}

class PopulationModel {
  const PopulationModel({
    required this.continent,
    required this.populationInMillions,
  });

  final String continent;
  final double populationInMillions;
}

{% endhighlight %}
{% endtabs %}

![Dice layout structure](images/layout/dice-layout.png)
