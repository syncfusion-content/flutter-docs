---
layout: post
title: Filtering in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about how to filter the data rows in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
--- 

# Filtering in Flutter DataGrid (SfDataGrid)

Filtering is the process of fetching the values from the collection which satisfy the specified condition. In the `SfDataGrid`, the filtering can be applied through the UI as well as programmatically.

## Programmatical Filtering

The SfDataGrid allows you to filter the data rows programmatically by adding the filter conditions along with the respective column name to the `DataGridSource.filterConditions` map collection. In the map collection, the `key` defines the `columnName` and the `values` defines the list of `FilterCondition`.

`DataGridSource.filterConditions` is a unmodifiable map collection. So, it doesn't allow to perform CRUD operations directly in the `DataGridSource.filterConditions` property. But, it can be done by the following public methods.

### Add filter

A filter condition to the specific column can be added by the `DataGridSource.addFilter` method.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Column(
    children: [
      Expanded(
        child: SfDataGrid(source: _employeeDataSource, columns: [
          GridColumn(
              columnName: 'ID',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Name',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Designation',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Salary',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  ))),
        ]),
      ),
      MaterialButton(
          child: Text('Add Filter'),
          onPressed: () {
            _employeeDataSource.addFilter('ID',
                FilterCondition(type: FilterType.lessThan, value: 1005));
          }),
    ],
  );
}

{% endhighlight %}
{% endtabs %}

### Remove filter

A filter condition to the specific column can be removed by the `DataGridSource.removeFilter` method.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Column(
    children: [
      Expanded(
        child: SfDataGrid(source: _employeeDataSource, columns: [
          GridColumn(
              columnName: 'ID',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Name',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Designation',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Salary',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  ))),
        ]),
      ),
      MaterialButton(
          child: Text('Add Filter'),
          onPressed: () {
            _employeeDataSource.removeFilter('Name',
                FilterCondition(type: FilterType.equals, value: 'James'));
          }),
    ],
  );
}

{% endhighlight %}
{% endtabs %}

### Clear filter

The filter conditions from the entire column can be cleared by the `DataGridSource.clearFilters` method. The filter conditions in the specific column can also be cleared by invoking the `DataGridSource.clearFilters` method along with the corresponding `columnName` as an argument.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Column(
    children: [
      Expanded(
        child: SfDataGrid(source: _employeeDataSource, columns: [
          GridColumn(
              columnName: 'ID',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Name',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Designation',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Salary',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  ))),
        ]),
      ),
      MaterialButton(
          child: Text('Add Filter'),
          onPressed: () {
            // To clear filter conditions from a specific column.
            _employeeDataSource.clearFilters(columnName: 'Salary');
            
            // To clear filter conditions from the entire filtered columns.
            _employeeDataSource.clearFilters();
          }),
    ],
  );
}

{% endhighlight %}
{% endtabs %}

### Filter behavior

The `FilterBehavior` enum property is used to specify whether to consider the `FilterValue` as the string or actual data type.

* **stringDataType** - It converts the cell value as string data type and compare the condition.
* **strongDataType** - It compares the cell value with its actual data type.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Column(
    children: [
      Expanded(
        child: SfDataGrid(source: _employeeDataSource, columns: [
          GridColumn(
              columnName: 'ID',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Name',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Designation',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Salary',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  ))),
        ]),
      ),
      MaterialButton(
          child: Text('Add Filter'),
          onPressed: () {
            _employeeDataSource.addFilter(
              'ID',
              FilterCondition(
                value: 1005,
                type: FilterType.contains,
                filterBehavior: FilterBehavior.stringDataType,
              ),
            );
          }),
    ],
  );
}

{% endhighlight %}
{% endtabs %}

### Filter operator

The `FilterOperator` enum property is used to decide how a logical operator is to be applied between multiple filter conditions.

* **and** - `AND` logical operator applies between multiple filter conditions 
* **or** - `OR` logical operator applies between multiple filter conditions

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Column(
    children: [
      Expanded(
        child: SfDataGrid(source: _employeeDataSource, columns: [
          GridColumn(
              columnName: 'ID',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Name',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Designation',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'Salary',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  ))),
        ]),
      ),
      MaterialButton(
          child: Text('Add Filter'),
          onPressed: () {
            _employeeDataSource.addFilter(
              'ID',
              FilterCondition(
                value: 1005,
                filterOperator: FilterOperator.and,
                type: FilterType.greaterThanOrEqual,
              ),
            );

            _employeeDataSource.addFilter(
              'ID',
              FilterCondition(
                value: 1010,
                filterOperator: FilterOperator.and,
                type: FilterType.lessThanOrEqual,
              ),
            );
          }),
    ],
  );
}

{% endhighlight %}
{% endtabs %}

## UI Filtering

The `SfDataGrid` provides excel like filtering UI and also advanced filter UI to filter the data easily. UI filtering can be enabled by setting `SfDataGrid.allowFiltering` property to `true`. This allows to open the filter UI by clicking on the filter icon in column header to filter the records. The filtering UI will be shown as a popup menu on the desktop and web platforms and it will be shown as a new page on the mobile platforms.

The `SfDataGrid` provides the following types of filter popup modes,

* **Checkbox Filter** - Provides excel like filter interface with list of check boxes.
* **Advanced Filter** - Provides advanced filter options to filter the data.

![Flutter datagrid shows a checkbox filter in web platform](images/filtering/flutter-datagrid-checkbox-filter-view.png)

![Flutter datagrid shows a advanced filter in web platform](images/filtering/flutter-datagrid-advanced-filter-view.png)

![Flutter datagrid shows a checkbox filter in mobile platform](images/filtering/flutter-datagrid-checkbox-filter-view-mobile.png)

![Flutter datagrid shows a advanced filter in mobile platform](images/filtering/flutter-datagrid-advanced-filter-view-mobile.png)

### Checkbox filtering

The Checkbox filtering is like the Excel like filter popup that shows the checked list box of the unique items with the search text field. The items which are in the checked state will be visible in the view other items will be filtered out from the view.

![Flutter datagrid shows a checkbox filter popup view](images/filtering/flutter-datagrid-checkbox-view-before-filter.png)

![Flutter datagrid shows the filtered rows](images/filtering/flutter-datagrid-checkbox-view-after-filter.png)

### Advanced filtering

Advanced filter UI provides multiple filter options to filter the data rows. The filter menu options are loaded based on advanced filter type by automatically detecting the underlying date type of the current column.
Below are the built-in filter types supported.

* **Text Filters** – Loads various menu options to filter the display text effectively.
* **Number Filters** – Loads various menu options to filter the numeric data.
* **Date Filters** – Loads various menu options and `DatePicker` to filter DateTime type column.

<table>
<tr>
<th>Text Filters </th>
<th>Number Filters </th>
<th>Date Filters </th>
</tr>
<tr>
<td>When the string value is bounded to the <code>GridColumn</code>, then <code>TextFilters</code> are loaded in <code>AdvancedFilterControl</code>. </td>
<td>When the int or double values are bounded to the <code>GridColumn</code>, then <code>NumberFilters</code> are loaded in <code>AdvancedFilterControl</code>. </td>
<td> When the DateTime type value is bounded to the <code>GridColumn</code>, then <code>DateFilters</code> are loaded in <code>AdvancedFilterControl</code>. </td>
</tr>
<tr>
<td> <img src="images/filtering/flutter-datagrid-advanced-text-filter.png"/> </td>
<td> <img src="images/filtering/flutter-datagrid-advanced-number-filter.png"/> </td>
<td> <img src="images/filtering/flutter-datagrid-advanced-date-filter.png"/> </td>
</tr>
<tr>
<td align="left" valign="top"><b>Filter menu options</b> <ul><li>Equals</li> <li>Does Not Equal</li> <li>Begins With</li> <li>Does Not Begin With</li> <li>Ends With</li> <li>Does Not End With</li> <li>Contains</li> <li>Does Not Contain</li> <li>Empty</li> <li>Not Empty</li> <li>Null</li> <li>Not Null</li></ul> </td>
<td align="left" valign="top"><b>Filter menu options</b> <li>Equals</li> <li>Does Not Equal</li> <li>Less Than</li> <li>Less Than Or Equal</li> <li>Greater Than</li> <li>Greater Than Or Equal</li> <li>Null</li> <li>Not Null</li></ul> </td>
<td align="left" valign="top"><b>Filter menu options</b> <li>Equals</li> <li>Does Not Equal</li> <li>Before</li> <li>Before Or Equal</li> <li>After</li> <li>After Or Equal</li> <li>Null</li> <li>Not Null</li></ul> </td>
</tr>
<table>

![Flutter datagrid shows a advanced filter popup view](images/filtering/flutter-datagrid-advanced-view-before-filter.png)

![Flutter datagrid shows the filtered rows](images/filtering/flutter-datagrid-advanced-view-after-filter.png)

#### Case sensitive filtering

The case sensitive filtering can be enabled for the column by using the casing icon available in the advanced filter UI. If the icon is active, the filtering will be applied with the case sensitive with the filter text. The case sensitive icon will be shown only to the string type columns.

![Flutter datagrid shows the case sensitive icon](images/filtering/flutter-datagrid-casesensitive-filtering.png)

### Disable filtering for an individual column

The `GridColumn.allowFiltering` has higher priority than `SfDataGrid.allowFiltering` property. So, you can disable the filtering for any particular column by setting `GridColumn.allowFiltering` property to `false`.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return SfDataGrid(
      allowFiltering: true,
      source: _employeeDataSource,
      columns: [
        GridColumn(
            allowFiltering: false,
            columnName: 'ID',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'Name',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'Designation',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'Salary',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Salary',
                  overflow: TextOverflow.ellipsis,
                ))),
      ]);
}

{% endhighlight %}
{% endtabs %}

## Callbacks

The SfDataGrid provides the following callbacks to notify the filtering stages:

### OnFilterChanging callback

`onFilterChanging` callback invokes when the filtering is being appiled to the particular column through UI filtering. You can return `false` from this callback to restrict the column from being filtered.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return SfDataGrid(
      allowFiltering: true,
      source: _employeeDataSource,
      onFilterChanging: (DataGridFilterChangeDetails details) {
        if (details.column.columnName == 'Salary') {
          return false;
        }
        return true;
      },
      columns: [
        GridColumn(
            columnName: 'ID',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'Name',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'Designation',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'Salary',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Salary',
                  overflow: TextOverflow.ellipsis,
                ))),
      ]);
}

{% endhighlight %}
{% endtabs %}

### OnFilterChanged callback

`onFilterChanged` callback invokes after the filtering is appiled to the particular column through UI filtering. You can use this callback to get filter conditions.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return SfDataGrid(
      allowFiltering: true,
      source: _employeeDataSource,
      onFilterChanged: (DataGridFilterChangeDetails details) {
        print('Column Name: ${details.column.columnName}');
        print('Filter Type: ${details.filterConditions.last.type}');
        print('Filter Value : ${details.filterConditions.last.value}');
      },
      columns: [
        GridColumn(
            columnName: 'ID',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'Name',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'Designation',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'Salary',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Salary',
                  overflow: TextOverflow.ellipsis,
                ))),
      ]);
}

{% endhighlight %}
{% endtabs %}