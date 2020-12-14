---
layout: post
title: Scrolling in Syncfusion Flutter DataGrid | DataTable
description: Learn about scrolling and how to customize the appearance of scrollbar in Syncfusion Flutter DataGrid.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Scrolling in Flutter (SfDataGrid)

SfDataGrid supports to scroll the data in both the horizontal and vertical direction. 

## ScrollBar

You can change the visibility of the scrollbar by using the [SfDataGrid.isScrollbarAlwaysShown](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/isScrollbarAlwaysShown.html) property. When the `isScrollbarAlwaysShown` is set to false, the scrollbar will be shown during scrolling and will fade out otherwise. When it is true, the scrollbar will always be visible and never fade out.

N> The `isScrollbarAlwaysShown` property default value is false.

{% tabs %}
{% highlight Dart %}

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: SfDataGrid(
        isScrollbarAlwaysShown: true,
        source: _employeeDataSource,
        columns: [
          GridNumericColumn(mappingName: 'id', headerText: 'ID'),
          GridTextColumn(mappingName: 'name', headerText: 'Name'),
          GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
          GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
        ],
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## ScrollPhysics

SfDataGrid allows you to change the physics of the scrollable data by using [SfDataGrid.horizontalScrollPhysics](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/horizontalScrollPhysics.html) and [SfDataGrid.verticalScrollPhysics](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/verticalScrollPhysics.html) properties.

N> By default, `horizontalScrollPhysics` and `verticalScrollPhysics` property value is `AlwaysScrollableScrollPhysics()`.

{% tabs %}
{% highlight Dart %}

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: SfDataGrid(
        horizontalScrollPhysics: NeverScrollableScrollPhysics(),
        verticalScrollPhysics: NeverScrollableScrollPhysics(),
        source: _employeeDataSource,
        columns: [
          GridNumericColumn(mappingName: 'id', headerText: 'ID'),
          GridTextColumn(mappingName: 'name', headerText: 'Name'),
          GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
          GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
        ],
      ),
    );
  }

{% endhighlight %}
{% endtabs %}
