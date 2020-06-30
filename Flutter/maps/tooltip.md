---
layout: post
title: Tooltips in Syncfusion Flutter maps | Syncfusion
description: This section explains about how to show tooltips and customize its appearance in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Tooltips in maps

This section helps to learn about how to add tooltip in the maps.

# Shape tooltip

You can enable shape tooltip. It is used to indicate clearly the information on the current tapped shape. By default, the shape tooltip text will be based on [`shapeDataField`] values.

N> 
* Refer the [`shapeTooltipTextMapper`] for changing the default shape tooltip text.

```dart
SfMaps()
```

![Tooltip support](images/tooltip/tooltip.png)

# Bubble tooltip

You can enable bubble tooltip. It is used to indicate clearly the information on the current tapped bubble. By default, the bubble tooltip text will be [`shapeDataField`] values.

N> 
* Refer the [`bubbleTooltipTextMapper`] for changing the default bubble tooltip text.

```dart
SfMaps()
```

![Tooltip support](images/tooltip/tooltip.png)

# Tooltip text callback

You can customize the shape tooltip text by using the [`shapeTooltipTextMapper`]. The [`shapeTooltipTextMapper`] will be called each time when you tap on a shape with corresponding index.You can pass the information that needs to be shown in the tooltip.

You can also customize the bubble tooltip as same shape tooltip using [`bubbleTooltipTextMapper`].

```dart
SfMaps()
```

![Tooltip support](images/tooltip/tooltip.png)

# Tooltip fill color

You can change the background color of the tooltip in the maps using the [`tooltipColor`] property.

You can also change the background color of the tooltip in the maps using the [`color`] which is property of [`tooltipSettings`].

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

```dart
SfMaps()
```

![Tooltip support](images/tooltip/tooltip.png)

# Tooltip Stroke color and width

You can change the border color and width of the tooltip in the maps using the [`tooltipStrokeColor`] and [`tooltipStrokeWidth`] property.

You can also change the background color of the tooltip in the maps using the [`strokeColor`] and [`strokeWidth`] which is property of [tooltipSettings].

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

```dart
SfMaps()
```

![Tooltip support](images/tooltip/tooltip.png)

# Tooltip label style

You can change the appearance of the tooltip text in the maps using the [`tooltipTextStyle`] property.

You can also change the appearance of the tooltip text in the maps using the [`textStyle`] which is property of [tooltipSettings].

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

```dart
SfMaps()
```

![Tooltip support](images/tooltip/tooltip.png)