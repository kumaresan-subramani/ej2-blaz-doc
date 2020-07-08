---
title: "Context Menu"
component: "Grid"
description: "Learn how to use the context menu and add custom context menu items in the Essential JS 2 DataGrid control."
---

# Context menu

The Grid has options to show the context menu when right clicked on it. To enable this feature, you need to define either default or custom item in the [`contextMenuItems`](../api/grid/#contextmenuitems).

To use the context menu, inject the `ContextMenu` module in the grid.

The default items are in the following table.

Items| Description
----|----
`AutoFit`|  Auto fit the current column.
`AutoFitAll` | Auto fit all columns.
`Edit`|  Edit the current record.
`Delete` | Delete the current record.
`Save` | Save the edited record.
`Cancel` | Cancel the edited state.
`Copy` | Copy the selected records.
`PdfExport` | Export the grid data as Pdf document.
`ExcelExport` | Export the grid data as Excel document.
`CsvExport` | Export the grid data as CSV document.
`Group` | Group the current column.
`Ungroup` | Ungroup the current column.
`SortAscending` | Sort the current column in ascending order.
`SortDescending` | Sort the current column in descending order.
`FirstPage` | Go to the first page.
`PrevPage` | Go to the previous page.
`LastPage` | Go to the last page.
`NextPage` | Go to the next page.

{% tab template="grid/row-template", es5Template="contextmenu" %}

```typescript
import { Grid, Resize, Sort, Group, ContextMenu, Edit, Page, PdfExport, ExcelExport } from '@syncfusion/ej2-grids';
import { data  } from './datasource.ts';

Grid.Inject(Resize, Sort, Group, Edit, ContextMenu, Page, PdfExport, ExcelExport);

let grid: Grid = new Grid({
    dataSource: data,
    allowSorting: true,
    allowPaging: true,
    editSettings: {allowEditing: true, allowDeleting: true},
    allowPdfExport: true,
    allowExcelExport: true,
    contextMenuItems: ['AutoFit', 'AutoFitAll', 'SortAscending', 'SortDescending',
                'Copy', 'Edit', 'Delete', 'Save', 'Cancel',
                'PdfExport', 'ExcelExport', 'CsvExport', 'FirstPage', 'PrevPage',
                'LastPage', 'NextPage'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', width: 200, textAlign: 'Right'},
        { field: 'Freight', width: 150, format: 'C2', textAlign: 'Right', editType: 'numericedit' },
        { field: 'ShipName', headerText: 'Ship Name', width: 300 },
        { field: 'ShipCountry', headerText: 'Ship Country',  width: 200 },
        { field: 'ShipCity', headerText: 'Ship City', width: 200 }
    ]
});
grid.appendTo('#Grid');


```

{% endtab %}

## Custom context menu items

The custom context menu items can be added by defining the [`contextMenuItems`](../api/grid/#contextmenuitems) as a collection of
[`contextMenuItemModel`](../api/grid/contextMenuItemModel).
Actions for this customized items can be defined in the [`contextMenuClick`](../api/grid/#contextmenuclick) event.

{% tab template="grid/row-template", es5Template="customcontext" %}

```typescript
import { Grid, ContextMenu, Page } from '@syncfusion/ej2-grids';
import { data  } from './datasource.ts';

Grid.Inject(ContextMenu, Page);

let grid: Grid = new Grid({
    dataSource: data,
    contextMenuItems: [{text: 'Copy with headers', target: '.e-content' id: 'copywithheader'}],
    allowSelection: true,
    allowPaging: true,
    contextMenuClick: function(args: MenuEventArgs){
        if(args.item.id === 'copywithheader'){
            grid.copy(true);
        }
    },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Left', width: 125, isPrimaryKey: true },
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 125 },
        { field: 'ShipName', headerText: 'Ship Name', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 170 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150, textAlign: 'Right' }
    ]
});
grid.appendTo('#Grid');


```

{% endtab %}

> You can hide or show an item in context menu for specific area inside of grid by defining the [`target`](../api/grid/contextMenuItemModel) property.
