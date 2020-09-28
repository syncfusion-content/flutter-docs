---
layout: post
title: Zoom Pan in Syncfusion Flutter maps | Syncfusion
description: This section explains how to use zoom pan in shape and tile layer in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Zooming and Panning features in maps

Zoom in the any layer for a closer look at a specific region by pinching or double tapping the map, scrolling the mouse wheel or track pad, or using the toolbar on the web. Pan the map to navigate across the regions. You can also customize the zoom level and the center point of the initial rendering.

## Customizing the zoom level

You can able to set the current zoom level of the map layer by using `MapZoomPanBehavior.zoomLevel`property. Current zoom level of the map layer.

The default [zoomLevel] value is 1 which will show the whole map in the viewport for [MapShapeLayer] and the possible bounds for the [MapTileLayer] based on the [focalLatLng]. You can also get the current zoom level after interaction using the [MapZoomPanBehavior.zoomLevel] property.

This properties can be changed dynamically.

To perform zooming, enable the `MapZoomPanBehavior.enablePinching`property. By default it will be `true`.

## Customizing the focalLatLng

The `MapZoomPanBehavior.focalLatLng` is the focal point of the map layer based on which zooming happens.It represents the focal latitude and longitude position of the map layer.You can also get the current focalLatLng after interaction using the [MapZoomPanBehavior.focalLatLng] property.

This properties can be changed dynamically. Defaults to `MapLatLng(0.0, 0.0)`.

To perform panning, enable the `MapZoomPanBehavior.enablePanning`property. By default it will be `true`.


## Customizing min and max zoom level

You can able to set the min and max zoom level of the map layer by setting the value to `MapZoomPanBehavior.minZoomLevel` and `MapZoomPanBehavior.maxZoomLevel`properties. The minimum and maximum zooming levels can be restricted using these properties respectively.

By default, the minzoom level will be 1 and the max zoomlevel will be 15.

However, for [MapTileLayer.maxZoomLevel] may slightly vary depends on the providers. Kindly check the respective official website of the map tile providers to know about the maximum zoom level it supports.

## Customizing Toolbar

Toolbar with the options for changing the visible bound for the web platform. By default, the [MapZoomPanBehavior.showToolbar] property is enabled.

[MapZoomPanBehavior.toolbarSettings] provides options for customizing the appearance of the toolbar. you can able to customize its positions, icon color, hover color.






