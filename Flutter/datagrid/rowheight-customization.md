---
layout: post
title: Row Height Customization for Syncfusion Flutter DataGrid | DataTable
description: Learn how to  customize the header row height and the row height of all the grid rows by using Row Height feature in Syncfusion Flutter DataGrid.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Row Height Customization in Flutter DataGrid (SfDataGrid)

This section explains about options to customize the header row height and the row height of all the grid rows or particular row based on your requirements.

## Set height for header row

`SfDataGrid` allows you to customize the height of the header row by using the `headerRowHeight` property.

{% tabs %}
{% highlight dart %} 

    @override
        Widget build(BuildContext context) {
            return Scaffold(
              body:SfDataGrid(
                source:_employeeDatasource,
                headerRowHeight: 70,
                columns:<GridColumn>[
                   GridNumericColumn(mappingName: 'id')..headerText = 'ID',
                   GridTextColumn(mappingName: 'name')..headerText = 'Name',
                   GridTextColum(mappingName: 'designation')..headerText = 'Designation',
                   GridNumericColumn(mappingName: 'salary')..headerText = 'Salary',
                      ],
                 )
          
              );
    }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows height for header row ](images/row-height-customization/flutter-datagrid-header-row-height.jpg)

## Set height for rows except header row

You can customize the height of the grid rows in `SfDataGrid` by using the `rowHeight` property.

{% tabs %}
{% highlight Dart %} 
        
    @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SfDataGrid(
            source:_employeeDatasource,
            rowHeight: 60,
            columns:<GridColumn>[
              GridNumericColumn(mappingName: 'id')..headerText = 'ID',
              GridTextColumn(mappingName: 'name')..headerText = 'Name',
              GridTextColum(mappingName: 'designation')..headerText = 'Designation',
              GridNumericColumn(mappingName: 'salary')..headerText = 'Salary',
                            ],
                        )
           );
    }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows height for rows except header row ](images/row-height-customization/flutter-datagrid-row-height.jpg)

## Fit row height based on its content

The row height can be fitted based on its content in `onQueryRowHeight` callback using `getAutoRowHeight` method which is available in `ColumnSizer`.

To access the `getAutoRowHeight` method, create an instance of `ColumnSizer`, set this instance in `columnSizer` property and use it in `onQueryRowHeight` callback. 

`ColumnSizer` objects are expected to be long-lived, not recreated with each build. 
 
**NOTE**
    By default, the display text’s overflow behavior is ellipsis. So, to enable the wrap for the display text, set the `softWrap` property as `true` and `overflow` property as clip.


{% tabs %}
{% highlight Dart %} 

    final ColumnSizer _columnSizer = ColumnSizer();

    @override
      Widget build(BuildContext context) {
        return Scaffold(
          body:SfDataGrid(
            source: _employeeDatasource,
            columnSizer: _columnSizer,
            onQueryRowHeight: (rowIndex) {
                  double height = _columnSizer.getAutoRowHeight(rowIndex);
                  return height;
                    },
            columns: <GridColumn>[
              GridTextColumn(mappingName: 'id')..softWrap = true..overflow = TextOverflow.clip..headerText = 'ID',
              GridTextColumn(mappingName: 'contactName')..softWrap = true..overflow = TextOverflow.clip
              ..headerText = 'Contact Name',
              GridTextColumn(mappingName: 'companyName')..softWrap = true ..overflow = TextOverflow.clip..headerText = 'Company Name',
              GridTextColumn(mappingName: 'city')..softWrap = true ..overflow = TextOverflow.clip..headerText = 'City',
              GridTextColumn(mappingName: 'address')..softWrap = true..overflow = TextOverflow.clip..headerText = 'Address',
              GridTextColumn(mappingName: 'designation')..softWrap = true ..overflow = TextOverflow.clip..headerText = 'Designation',
              GridTextColumn(mappingName: 'country')..softWrap = true ..overflow = TextOverflow.clip..headerText = 'Country',
          ]    
        )
      );
    }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows auto fit row height](images/row-height-customization/flutter-datagrid-auto-fit-row.jpg)

### Auto fit row height options

#### Exclude the certain columns from auto-fit row calculation
                
By default, `getAutoRowHeight` method calculates the row height based on all columns. To skip the specific columns from the row height calculation, add that columns to the `excludeColumns` parameter in `getAutoRowHeight` method.

 {% tabs %}
{% highlight Dart %} 

    @override
      Widget build(BuildContext context) {
        return Scaffold(
          body:SfDataGrid(
            source: _autoRowHeightDataGridSource,
            columnSizer: _columnSizer,
            onQueryRowHeight: (int rowIndex) {
              final List<String> _excludeColumns = [
                'designation',
                'address',
                'city',
                ];
                final double height= _columnSizer.getAutoRowHeight(rowIndex,excludedColumns:_excludeColumns);
             return height;
            },
            columns: <GridColumn>[
              GridTextColumn(mappingName: 'id') ..softWrap=true..overflow = TextOverflow.clip..headerText = 'ID',
              GridTextColumn(mappingName: 'contactName')..softWrap = true..overflow = TextOverflow.clip..headerText = 'Contact Name',
              GridTextColumn(mappingName: 'companyName')..softWrap=true..overflow = TextOverflow.clip..headerText = 'Company Name',
              GridTextColumn(mappingName: 'address')..softWrap=true..overflow = TextOverflow.clip ..headerText = 'Address',
              GridTextColumn(mappingName: 'city')..softWrap=true..overflow = TextOverflow.clip
              ..headerText = 'City',
              GridTextColumn(mappingName: 'designation')..softWrap=true..overflow = TextOverflow.clip
              ..headerText = 'Designation',
              GridTextColumn(mappingName: 'country')..softWrap=true..overflow = TextOverflow.clip..headerText = 'Country',
          ]
        );
      );
     }
{% endhighlight %}
{% endtabs %}


#### Include the hidden columns in auto-fit row calculation

The hidden columns can also be considered for the row height calculation by using the `canIncludeHiddenColumns` parameter in 
`getAutoRowHeight` method.


{% tabs %}
{% highlight Dart %} 

    @override
      Widget build(BuildContext context) {
        return Scaffold(
          body:SfDataGrid(
            source: _autoRowHeightDataGridSource,
            columnSizer: _columnSizer,
            onQueryRowHeight: (int rowIndex) {
              final double height = _columnSizer.getAutoRowHeight(rowIndex,  canIncludeHiddenColumns: true);
            return height;
           },
            columns: <GridColumn>[
              GridTextColumn(mappingName: 'id')..softWrap = true..overflow = TextOverflow.clip..headerText = 'ID',
              GridTextColumn(mappingName: 'contactName')..softWrap = true ..overflow = TextOverflow.clip..headerText = 'Contact Name',
              GridTextColumn(mappingName: 'companyName')..softWrap = true ..overflow = TextOverflow.clip
              ..headerText = 'Company Name',
              GridTextColumn(mappingName: 'country')..softWrap = true..overflow = TextOverflow.clip..headerText = 'Country',
              GridTextColumn(mappingName: 'address')..softWrap = true..isHidden = true..overflow = TextOverflow.clip..headerText = 'Address',
              GridTextColumn(mappingName: 'city')..softWrap = true..isHidden = true..overflow = TextOverflow.clip ..headerText = 'City',
              GridTextColumn(mappingName: 'designation') ..softWrap = true ..isHidden = true..overflow = TextOverflow.clip..headerText = 'Designation',
             
        ]
        )
        );
    }
{% endhighlight %}
{% endtabs %}


