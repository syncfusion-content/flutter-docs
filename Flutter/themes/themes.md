---
layout: post
title: Applying themes for Syncfusion FLutter widgets
description: This section explains about theming in Syncfusion Flutter widgets
platform: flutter
control: General
documentation: ug
---

# Theme

Syncfusion Flutter themes allow you to apply colors, font-styles, etc across all the Synfusion Flutter widgets with a uniform approach and provide a consistent look to your applications. 

## Getting started

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

The theme widget is available in the `Syncfusion Core` package. Since all our widgets are core dependent, you don't need to include the core as a separate package. Here we have included the chart package in the pub spec file.

{% highlight dart %} 

    dependencies:

    syncfusion_flutter_charts: ^XX.X.XX

{% endhighlight %}

*Note* - Here **XX.X.XX** denotes the current version of [`Synfusion Flutter Chart`](https://pub.dev/packages/syncfusion_flutter_charts/versions) widget.

**Get packages**

Run the following command to get the required packages.

{% highlight dart %} 

    $ flutter pub get

{% endhighlight %}

**Import package**

To use the theme widgets, import the following package in your Dart code.

{% highlight dart %} 

    import 'package:syncfusion_flutter_core/theme.dart';

{% endhighlight %}

## Applying light and dark themes

Syncfusion Flutter widgets provide support for light and dark themes. As the name suggests, these themes will have colors with light and dark color contrasts, respectively. 

By default, the light theme will be applied. You can apply a dark theme using the brightness property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: SfTheme(
                    data: SfThemeData(
                        brightness: Brightness.dark
                    ),
                    child: SfCartesianChart())
            )
        );
    }

{% endhighlight %}

![Dark theme](images/theme_chart.png)

Using the `SfTheme` widget you can apply theme across all the Synfusion Flutter widgets with a uniform approach. If you wish to apply a specific theme to a specific widget alone, this can be achieved using the individual theme widget. For example, `SfChartTheme` widget in case of `chart` widget and `SfCalendarTheme` in case of `calendar` widget.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SingleChildScrollView(
          child: Center(
            child: SfTheme(
              data: SfThemeData(brightness: Brightness.dark),
              child: Column(
                children: <Widget>[
                  Container(
                      child: SfChartTheme(
                          data: SfChartThemeData(
                              brightness: Brightness.light,
                              backgroundColor: Colors.blue[300]),
                          child: SfCartesianChart())),
                  Container(
                      child: SfRadialGauge(
                          // Other configurations
                          )),
                  Container(
                      child: SfCalendar(
                          // Other configurations
                          ))
                ],
              ))),
    ));
  }

{% endhighlight %}

In the above example, other than the chart widget, the dark theme will be applied and for the chart widget, the light theme will be applied.

N> When dark or light theme is applied to the material app, and Syncfusion theme widgets are not initialized in your application, then based on the theme applied to the material app, the appropriate theme will be applied to Syncfusion widgets.