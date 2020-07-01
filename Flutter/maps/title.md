---
layout: post
title: Syncfusion Flutter Maps Title | Syncfusion
description: This section explains how to add title and customize its appearance in the flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Title features in flutter maps

This section helps to learn about how to add title in the maps and customize them.

## Title Text

You can define the maps title using [`SfMaps.title`] property. You can set the maps title using the [`MapsTitle.text`] property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.only(left: 15, right: 15),
      child: SfMaps(
        title: MapTitle(
            text: 'World Map',
        ),
        layers: [
          MapShapeLayer(
            delegate: MapShapeLayerDelegate(
              shapeFile: "assets/world_map.json",
              shapeDataField: "continent",
            ),
            color: const Color.fromRGBO(86, 170, 235, 0.35),
          ),
        ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Maps title support](images/title/default_title.png)

## Text Style

### Using title

You can change the appearance of the title text in the maps using the [`MapsTitle.textStyle`]property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.only(left: 15, right: 15),
      child: SfMaps(
        title: MapTitle(
            text: 'World Map',
            textStyle: const TextStyle(
                color: Colors.black,
                fontSize: 20,
                fontStyle: FontStyle.italic,
            ),
        ),
        layers: [
          MapShapeLayer(
            delegate: MapShapeLayerDelegate(
              shapeFile: "assets/world_map.json",
              shapeDataField: "continent",
            ),
            color: const Color.fromRGBO(86, 170, 235, 0.35),
          ),
        ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Using SfMapsTheme

You can also change the appearance of the title text in the maps using the [`titleTextStyle`] property of [`SfMapsThemeData`].

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.only(left: 15, right: 15),
      child: SfMapsTheme(
                data: SfMapsThemeData(
                    titleTextStyle: const TextStyle(
                        color: Colors.black,
                        fontSize: 30,
                        fontStyle: FontStyle.italic,
                    ),
                ),
                child: SfMaps(
                    title: MapTitle(
                        text: 'World Map',
                    ),
                    layers: [
                        MapShapeLayer(
                            delegate: const MapShapeLayerDelegate(
                                shapeFile: "assets/world_map.json",
                                shapeDataField: "continent",
                            ),
                        ),
                    ],
                ),
            ),
        ),
    );
}

{% endhighlight %}
{% endtabs %}

![Maps title support](images/title/default_title.png)

## Text Alignment

You can align the title text in the maps using the [`MapsTitle.alignment`] property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.only(left: 15, right: 15),
      child: SfMaps(
        title: MapTitle(
            text: 'World Map',
            textStyle: const TextStyle(
                color: Colors.black,
                fontSize: 20,
                fontStyle: FontStyle.italic,
            ),
            alignment: Alignment.center,
        ),
        layers: [
          MapShapeLayer(
            delegate: MapShapeLayerDelegate(
              shapeFile: "assets/world_map.json",
              shapeDataField: "continent",
            ),
            color: const Color.fromRGBO(86, 170, 235, 0.35),
          ),
        ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Maps title support](images/title/default_title.png)

## Background color

You can change the background color of the title in the maps using the [`MapsTitle.color`].

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.only(left: 15, right: 15),
      child: SfMaps(
        title: MapTitle(
            text: 'World Map',
            textStyle: const TextStyle(
                color: Colors.black,
                fontSize: 20,
                fontStyle: FontStyle.italic,
            ),
            alignment: Alignment.center,
            color: Colors.red,
        ),
        layers: [
          MapShapeLayer(
            delegate: MapShapeLayerDelegate(
              shapeFile: "assets/world_map.json",
              shapeDataField: "continent",
            ),
            color: const Color.fromRGBO(86, 170, 235, 0.35),
          ),
        ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Maps title support](images/title/default_title.png)

## Decoration

You can decorate the title of maps by using the [`MapsTitle.decoration`] property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.only(left: 15, right: 15),
      child: SfMaps(
        title: MapTitle(
            text: 'World Map',
            textStyle: const TextStyle(
                color: Colors.black,
                fontSize: 20,
                fontStyle: FontStyle.italic,
            ),
            alignment: Alignment.center,
            decoration: BoxDecoration(
                color: Colors.transparent,
                border: Border.all(color: Colors.red, width: 2),
                borderRadius: const BorderRadius.all(Radius.circular(4)),
                shape: BoxShape.rectangle,
            ),
        ),
        layers: [
          MapShapeLayer(
            delegate: MapShapeLayerDelegate(
              shapeFile: "assets/world_map.json",
              shapeDataField: "continent",
            ),
            color: const Color.fromRGBO(86, 170, 235, 0.35),
          ),
        ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Maps title support](images/title/default_title.png)

## Margin

You can add margin to the maps title using the [`MapsTitle.margin`] property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.only(left: 15, right: 15),
      child: SfMaps(
        title: MapTitle(
            text: 'World Map',
            textStyle: const TextStyle(
                color: Colors.black,
                fontSize: 20,
                fontStyle: FontStyle.italic,
            ),
            alignment: Alignment.center,
            margin: const EdgeInsets.all(10),
            decoration: BoxDecoration(
                color: Colors.transparent,
                border: Border.all(color: Colors.red, width: 2),
                borderRadius: const BorderRadius.all(Radius.circular(4)),
                shape: BoxShape.rectangle,
            ),
        ),
        layers: [
          MapShapeLayer(
            delegate: MapShapeLayerDelegate(
              shapeFile: "assets/world_map.json",
              shapeDataField: "continent",
            ),
            color: const Color.fromRGBO(86, 170, 235, 0.35),
          ),
        ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Maps title support](images/title/default_title.png)

## Padding

You can add padding to the maps title using the [`MapsTitle.padding`] property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Padding(
      padding: EdgeInsets.only(left: 15, right: 15),
      child: SfMaps(
        title: MapTitle(
            text: 'World Map',
            textStyle: const TextStyle(
                color: Colors.black,
                fontSize: 20,
                fontStyle: FontStyle.italic,
            ),
            alignment: Alignment.center,
            margin: const EdgeInsets.all(10),
            padding: const EdgeInsets.all(10),
            decoration: BoxDecoration(
                color: Colors.transparent,
                border: Border.all(color: Colors.red, width: 2),
                borderRadius: const BorderRadius.all(Radius.circular(4)),
                shape: BoxShape.rectangle,
            ),
        ),
        layers: [
          MapShapeLayer(
            delegate: MapShapeLayerDelegate(
              shapeFile: "assets/world_map.json",
              shapeDataField: "continent",
            ),
            color: const Color.fromRGBO(86, 170, 235, 0.35),
          ),
        ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Maps title support](images/title/default_title.png)