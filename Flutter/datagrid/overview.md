---
layout: post
title: About Flutter DataGrid widget | DataTable | Syncfusion®
description: Learn about the introduction of the Syncfusion® Flutter DataGrid (SfDataGrid) widget, its features, and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Flutter DataGrid (SfDataGrid) Overview 

The Syncfusion® Flutter DataGrid is used to display and manipulate data in a tabular view. It is built from the ground up to achieve the best possible performance, even when loading large amounts of data.

**Note:** The SfDataGrid widget is compatible with iOS, Android, Web, macOS, and Windows platforms. Ensure you have Flutter SDK 3.0 or later installed. For detailed setup instructions, refer to the [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive#choose-your-ide) documentation.

![Overview Flutter Datagrid](images/overview/flutter-datagrid-overview.png)


## Key Features

### Data Presentation
* [**Column types**](column-types.md) - Display any widget in each column, allowing for flexible content presentation.
* [**Column sizing**](columns-sizing.md) - Configure column widths with various sizing options. Automatically adjust columns based on cell content to enhance readability.
* [**Row height**](row-height-customization.md) - Customize heights for header and data rows. Automatically adjust row heights based on cell content. Set different heights for specific rows as needed.
* [**Styling**](styles.md) - Customize the appearance of cells and headers with support for conditional styling.
* [**Stacked headers**](stacked-headers.md) - Create unbound header rows that span across multiple rows and columns.
* [**Footer**](footer.md) - Show an additional row that can be displayed under the last row. Widgets can also be displayed in the footer row.

### Data Manipulation
* [**Editing**](editing.md) - Enable users to modify cell values with support for custom editor widgets based on column types.
* [**Sorting**](sorting.md) - Sort data in ascending or descending order across single or multiple columns. 
* [**Filtering**](filtering.md) - Filter data interactively similar to Excel with support for text, numeric, and date-time filtering. Programmatic filtering is also available.
* [**Selection**](selection.md) - Select one or more rows with keyboard navigation support for web platforms.
* [**Swiping**](swiping.md) - Implement swipe actions (left-to-right or right-to-left) for operations like deleting or editing rows.

### Layout and Navigation
* [**Column Drag and Drop**](column-drag-and-drop.md) - Reorder columns by dragging and dropping them to desired positions.
* [**Column resizing**](columns-resizing.md) - Adjust column widths by dragging the right edge of column headers.
* [**Freeze Panes**](freeze-panes.md) - Freeze the rows and columns when scrolling the grid.
* [**Scrolling**](scrolling.md) - Scroll through large datasets efficiently with optimized rendering.

### Data Loading and Performance
* [**Load more**](load-more.md) - Display an interactive view when scrolling reaches the bottom of the grid, enabling on-demand data loading.
* [**Paging**](paging.md) - Load data in segments. It is useful when loading huge amounts of data.
* [**Pull to refresh**](pull-to-refresh.md) - Allows users to refresh data when the DataGrid is pulled down.

### Export and Integration
* [**Exporting**](export-to-excel.md) - Export data to [Excel](export-to-excel.md) and [PDF](export-to-pdf.md) formats.
* [**Grouping**](grouping.md) - Group rows by one or more columns for better data organization.
* [**Summaries**](summaries.md) - Display aggregate values for grouped or all data.

### Customization and Accessibility
* [**Theme**](https://help.syncfusion.com/flutter/themes) - Use a dark or light theme.
* [**Accessibility**](accessibility.md) - Ensure screen readers can properly access and navigate the DataGrid.
* [**Right to Left (RTL)**](right-to-left.md) - Support right-to-left layouts for languages like Hebrew and Arabic.
* [**Localization**](localization.md) - Support multiple languages and regional formats.

## Getting Started

To start using the SfDataGrid widget in your Flutter application, refer to the [Getting Started with Flutter DataGrid](getting-started.md) documentation.

## API Reference

For a complete list of properties, methods, and events of the SfDataGrid widget, refer to the [SfDataGrid API documentation](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html).

## Sample GitHub Repository

You can download a complete working sample from the [GitHub repository](https://github.com/SyncfusionExamples/getting-started-with-flutter-datagrid) to explore the SfDataGrid widget with various features implemented.
