---
layout: post
title: Zoom Pan in Syncfusion Flutter maps | Syncfusion
description: This section explains how to zoom pan in both layers in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Zooming and Panning features in maps

Zoom in the any layer for a closer look at a specific region by pinching or double tapping the map, scrolling the mouse wheel or track pad, or using the toolbar on the web. Pan the map to navigate across the regions. You can also customize the zoom level and the center point of the initial rendering.

## Customizing the zoom level

You can able to set the zoom level by using `MapZoomPanBehavior.zoomLevel`property. You can also able to set the initial zoom level by setting the `MapTileLayer.initialFocalLatLng` property.

## Customizing the focalLatLng

The `MapZoomPanBehavior.focalLatLng` is the focal point of the map layer based on which zooming happens. Based on this point, the bounds of the layer get changed.

You can also able to set the intial focalLatLng by setting the `MapTileLayer.initialFocalLatLng` property.

## Customizing min and max zoom level



