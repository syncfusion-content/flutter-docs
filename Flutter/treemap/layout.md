---
layout: post
title: Different layout structure in Syncfusion Flutter Treemap | Syncfusion
description: This section explains the steps required to visualize the treemap widget in the different layout structures.
platform: Flutter
control: SfTreemap
documentation: ug
---

# Layout structure in Treemap

This section explains the different layout structures in the treemap widget. The available layout structures are,

* Squarify
* Slice
* Dice

## Squarify

The Squarify layout structure start to arrange the rectangles in a row and wrapping them to the next row according to the available size. By default, Squarify layout structure is used.

You can visualize the Squarify layout in two ways such as `Flat` and `Hierarchical` structure.

{% tabs %}
{% highlight Dart %}

List<PopulationModel> _dataSource;

@override
void initState() {
   _dataSource = <PopulationModel>[
      PopulationModel('Asia', 25.4),
      PopulationModel('South America', 19.11),
      PopulationModel('North America', 13.3),
      PopulationModel('Europe', 10.65),
      PopulationModel('Africa', 7.54),
      PopulationModel('Australia', 4.93),
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
  const PopulationModel(this.continent, this.populationInMillions);

  final String continent;
  final double populationInMillions;
}

{% endhighlight %}
{% endtabs %}

![Squarify layout structure](images/layout/squarify-layout.png)

## Slice

The Slice layout structure start to arrange each rectangle in a horizontally direction and the size of the rectangle based on the value of [`weightValueMapper`] property and the available height.

You can visualize the Slice layout in two ways such as `Flat` and `Hierarchical` structure.

{% tabs %}
{% highlight Dart %}

List<PopulationModel> _dataSource;

@override
void initState() {
   _dataSource = <PopulationModel>[
      PopulationModel('Asia', 25.4),
      PopulationModel('South America', 19.11),
      PopulationModel('North America', 13.3),
      PopulationModel('Europe', 10.65),
      PopulationModel('Africa', 7.54),
      PopulationModel('Australia', 4.93),
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
  const PopulationModel(this.continent, this.populationInMillions);

  final String continent;
  final double populationInMillions;
}

{% endhighlight %}
{% endtabs %}

![Slice layout structure](images/layout/slice-layout.png)

## Dice

The Dice layout structure start to arrange each rectangle in vertical direction and the size of the rectangle based on the value of [`weightValueMapper`] property and the available width.

You can visualize the Dice layout in two ways such as `Flat` and `Hierarchical` structure.

{% tabs %}
{% highlight Dart %}

List<PopulationModel> _dataSource;

@override
void initState() {
   _dataSource = <PopulationModel>[
      PopulationModel('Asia', 25.4),
      PopulationModel('South America', 19.11),
      PopulationModel('North America', 13.3),
      PopulationModel('Europe', 10.65),
      PopulationModel('Africa', 7.54),
      PopulationModel('Australia', 4.93),
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
  const PopulationModel(this.continent, this.populationInMillions);

  final String continent;
  final double populationInMillions;
}

{% endhighlight %}
{% endtabs %}

![Dice layout structure](images/layout/dice-layout.png)
