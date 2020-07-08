---
title: "Create custom toolbar with drop-down list"
component: "Grid"
description: "Learn how to create custom toolbar with drop-down list."
---

# Create custom toolbar with drop-down list

You can create your own ToolBar items in the Grid. It can be added by defining the [`toolbar`](../../api/grid/#toolbar) as HTML element ID. Actions for this ToolBar template items are defined in the [`toolbarClick`](../../api/grid/#toolbarclick).

To include components in the ToolBar, please ensure the following steps:

**Step 1**:

Initialize the template for your custom component. Using the following code add the DropDownList component to the ToolBar.

```html
        <div id='toolbar-template'>
            <div id='dropdown' style="margin-top:5px">
                <input type="text" tabindex="1" id='ddlelement' />
            </div>
        </div>

```

**Step 2**:

To render the DropDownList component, use the [`dataBound`](../../api/grid/#databound) event of the Grid.

* You can select the grid row index based on the selected data in the DropDownList. The output will appear as follows.

{% tab template="grid/toolbar-dropdown", sourceFiles="index.ts,index.css,index.html",es5Template="toolbar" %}

```typescript

import { Grid, Toolbar } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
let rowIndex: any = [0, 1, 2, 3, 4, 5, 6, 8, 9, 10, 11, 12, 13, 14];
Grid.Inject(Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    toolbarTemplate: '#toolbar-template',
    dataBound: dataBound,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C2' },
        { field: 'OrderDate', headerText: 'Order Date', textAlign: 'Right', width: 140, format: 'yMd' }
    ],
    height: 200
});
grid.appendTo('#Grid');

function dataBound(): void {

    let dropDownListObject: DropDownList = new DropDownList({
        // set the data to dataSource property
        dataSource: rowIndex,
        change: change,
        popupHeight :200
    });
    dropDownListObject.appendTo('#ddlelement');
}

function change(args: ChangeEventArgs): void {
    grid.selectRow(<number>args.itemData);
}

```

{% endtab %}
