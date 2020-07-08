---
title: "How To"
component: "Grid"
description: "Learn how to refresh the datasource, exporting filtered data, enable and disable grid actions, customize the pager dropdown in Essential JS 2 DataGrid."
---

# How To

## Refresh the data source

You can add/delete the data source records through an external button. To reflect the data source changes in the grid, invoke the [`refresh`](../api/grid/#refresh) method.

To refresh the data source:

**Step 1**:

Add/delete the data source record by using the following code.

```typescript
    grid.dataSource.unshift(data); // add a new record.

    grid.dataSource.splice(selectedRow, 1); // delete a record.

```

**Step 2**:

Refresh the grid after the data source change by using the [`refresh`](../api/grid/#refresh) method.

```typescript
    grid.refresh(); // refresh the Grid.

```

{% tab template="grid/refresh-grid", sourceFiles="index.ts,index.css,index.html",es5Template="refresh" %}

```typescript

import { Grid } from '@syncfusion/ej2-grids';
import { Button } from '@syncfusion/ej2-buttons';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C2' },
        { field: 'OrderDate', headerText: 'Order Date', textAlign: 'Right', width: 140, format: 'yMd' }
    ],
    height: 280
});
grid.appendTo('#Grid');

let add: Button = new Button({}, '#add');
let dele: Button = new Button({}, '#delete');

document.getElementById('add').onclick = () => {
    let data: Object = { OrderID: 10247, CustomerID: "ASDFG", Freight: 40.4, OrderDate: new Date(8367642e5) };
    (<Object[]>grid.dataSource).unshift(data); // add new record.
    grid.refresh(); // refresh the Grid.
};

document.getElementById('delete').onclick = () => {
    if (grid.getSelectedRowIndexes().length) {
        let selectedRow: number = grid.getSelectedRowIndexes()[0];
        (<Object[]>grid.dataSource).splice(selectedRow, 1); // delete the selected record.
    } else {
        alert("No records selected for delete operation");
    }
    grid.refresh(); // refresh the Grid.
};

```

{% endtab %}

## Toolbar

### Create custom toolbar with drop-down list

You can create your own ToolBar items in the Grid. It can be added by defining the [`toolbar`](../api/grid/#toolbar) as HTML element ID. Actions for this ToolBar template items are defined in the [`toolbarClick`](../api/grid/#toolbarclick).

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

To render the DropDownList component, use the [`dataBound`](../api/grid/#databound) event of the Grid.

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

## Enable/Disable Grid and its actions

You can enable/disable the Grid and its actions by applying/removing corresponding CSS styles.

To enable/disable the grid and its actions, follow the given steps:

**Step 1**:

Create CSS class with custom style to override the default style of Grid.

```css
    .disablegrid {
        pointer-events: none;
        opacity: 0.4;
    }
    .wrapper {
        cursor: not-allowed;
    }

```

**Step 2**:

Add/Remove the CSS class to the Grid in the click event handler of Button.

```typescript
    document.getElementById('primarybtn').addEventListener('click', () => {
        if (grid.element.classList.contains('disablegrid')) {
            grid.element.classList.remove('disablegrid');
            document.getElementById("GridParent").classList.remove('wrapper');
        }
        else {
            grid.element.classList.add('disablegrid');
            document.getElementById("GridParent").classList.add('wrapper');
        }
    });

```

In the below demo, the button click will enable/disable the Grid and its actions.

{% tab template="grid/disablegrid",es5Template="disablegrid" %}

```typescript
import { Grid, Edit, Toolbar, EditEventArgs, EJ2Intance } from '@syncfusion/ej2-grids';
import { Button } from '@syncfusion/ej2-buttons';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);
let button: Button = new Button();
button.appendTo('#primarybtn');
let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowAdding:true, allowEditing: true, allowDeleting:true },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', editType: 'numericedit', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country', editType: 'dropdownedit', width: 150 }
    ],
    height: 265
});
grid.appendTo('#Grid');
document.getElementById('primarybtn').addEventListener('click', () => {
    if (grid.element.classList.contains('disablegrid')) {
        grid.element.classList.remove('disablegrid');
        document.getElementById("GridParent").classList.remove('wrapper');
    }
    else {
        grid.element.classList.add('disablegrid');
        document.getElementById("GridParent").classList.add('wrapper');
    }
});
```

{% endtab %}

## Columns

### Change column header text dynamically

You can change the column [`headerText`](../api/grid/column/#headertext) dynamically through an external button.

Follow the given steps to change the header text dynamically:

**Step 1**:

Get the column object corresponding to the field name by using the [`getColumnByField`](../api/grid/#getcolumnbyfield) method.
Then, change the header text value.

```typescript
let column = grid.getColumnByField("ShipCity"); // Get column object.
column.headerText = 'Changed Text';

```

**Step 2**:

To reflect the changes in the grid header, invoke the [`refreshHeader`](../api/grid/#refreshheader) method.

```typescript
grid.refreshHeader();

```

{% tab template="grid/change-header-text", sourceFiles="index.ts,index.css,index.html",es5Template="dynamic" %}

```typescript
import { Grid, Column } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 120 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 280
});
grid.appendTo('#Grid');

let btn: Button = new Button({ cssClass: 'e-flat' }, '#change-text');

document.getElementById('change-text').addEventListener('click', () => { // changing the header text for ShipCity column.
    let column: Column = grid.getColumnByField("ShipCity"); // get the JSON object of the column corresponding to the field name.
    column.headerText = "Changed Text"; // assign a new header text to the column.
    grid.refreshHeader();
});

```

{% endtab %}

### Customize column styles

You can customise the appearance of the header and content of a particular column using the [`customAttributes`](../api/grid/column/#customattributes) property.

To customize the grid column, follow the given steps:

**Step 1**:

Create a CSS class with custom style to override the default style for rowcell and headercell.

```css
.e-grid .e-rowcell.customcss{
    background-color: #ecedee;
    color: 'red';
    font-family: 'Bell MT';
    font-size: 20px;
}

.e-grid .e-headercell.customcss{
    background-color: #2382c3;
    color: white;
    font-family: 'Bell MT';
    font-size: 20px;
}

```

**Step 2**:

Add the custom CSS class to the specified column by using the [`customAttributes`](../api/grid/column/#customattributes) property.

```typescript
{ field: 'ShipCity', headerText: 'Ship City', customAttributes: {class: 'customcss'}, width: 100 },

```

{% tab template="grid/custom-column", sourceFiles="index.ts,index.css",es5Template="styles" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    enableHover: false,
    allowSelection: false,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', customAttributes: { class: 'customcss' }, width: 100 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 315
});
grid.appendTo('#Grid');


```

{% endtab %}

### Display custom tooltip for columns in grid

To display custom ToolTip ([`EJ2 Tooltip`](../../tooltip/getting-started)),  use the
[`queryCellInfo`](../api/grid/#querycellinfo) event.

Render the ToolTip component for the grid cells by using the following code in the [`queryCellInfo`](../api/grid/#querycellinfo) event.

```typescript
function tooltip (args: QueryCellInfoEventArgs) {
    let tooltip: Tooltip = new Tooltip({
        content: args.data[args.column.field].toString();
    }, args.cell);
}

```

{% tab template="grid/custom-tooltip",es5Template="tooltip" %}

```typescript
import { Grid, QueryCellInfoEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Tooltip } from '@syncfusion/ej2-popups';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipName', headerText: 'Ship Name', width: 140 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
    ],
    queryCellInfo: tooltip,
    height: 315
});
grid.appendTo('#Grid');

function tooltip(args: QueryCellInfoEventArgs): void { // event triggers on every cell render.
    let tooltip: Tooltip = new Tooltip({
        content: args.data[args.column.field].toString() // add Essential JS2 tooltip for every cell.
    }, <HTMLElement>args.cell);
}

```

{% endtab %}

### Render other components in a column

You can render any component in a grid column using the [`template`](../api/grid/column/#template) property.

To render other components in the grid, ensure the following steps:

**Step 1**:

Initialize the column template for your custom component.

```typescript
template:`<div>
            <select class="e-control e-dropdownlist">
                <option value="1" selected="selected">Order Placed</option>
                <option value="2">Processing</option>
                <option value="3">Delivered</option>
            </select>
        </div>`

```

**Step 2**:

Using the [`queryCellInfo`](../api/grid/#querycellinfo) event, you can render the DropDown component with the following code.

```typescript
    function dropdown(args: QueryCellInfoEventArgs) {
        let ele=args.cell.querySelector('select');
        let drop = new DropDownList({popupHeight: 150, popupWidth: 150});
        drop.appendTo(ele);
    }

```

{% tab template="grid/column-sync-comp",es5Template="othercomp" %}

```typescript
import { Grid, QueryCellInfoEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { DropDownList } from '@syncfusion/ej2-dropdowns';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        {
            headerText: 'Order Status',
            template:
            `<div>
                <select class="e-control e-dropdownlist">
                    <option value="1" selected="selected">Order Placed</option>
                    <option value="2">Processing</option>
                    <option value="3">Delivered</option>
                </select>
            </div>`, width: 140
        },
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'OrderDate', headerText: 'Order Date', width: 100, format: 'yMd' },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
    ],
    height: 315,
    queryCellInfo: dropdown
});
grid.appendTo('#Grid');

function dropdown(args: QueryCellInfoEventArgs): void {
    let ele: HTMLSelectElement = args.cell.querySelector('select');
    let drop: DropDownList = new DropDownList({ popupHeight: 150, popupWidth: 150 });
    drop.appendTo(ele);
}

```

{% endtab %}

### Change the orientation of the header text

You can change the orientation of the header text by using the [`customAttributes`](../api/grid/column/#customattributes) property.

Ensure the following steps:

**Step 1**:

Create a CSS class with orientation style for the grid header cell.

```css
.orientationcss .e-headercelldiv {
    transform: rotate(90deg);
}

```

**Step 2**:

Add the custom CSS class to a particular column by using the [`customAttributes`](../api/grid/column/#customattributes) property.

```typescript
    { field: 'ShipCity', headerText: 'Ship City', textAlign: 'Center', customAttributes: {class: 'orientationcss'}, width: 80 },

```

**Step 3**:

Resize the header cell height by using the following code.

```typescript
function setHeaderHeight(args) {
    let textWidth: number = document.querySelector(".orientationcss > div").scrollWidth;//Obtain the width of the headerText content.
    let headerCell: NodeList = document.querySelectorAll(".e-headercell");
    for(let i: number = 0; i < headerCell.length; i++) {
        (<HTMLElement>headerCell.item(i)).style.height = textWidth + 'px'; //Assign the obtained textWidth as the height of the headerCell.
    }
}

```

{% tab template="grid/orientation", sourceFiles="index.ts,index.css",es5Template="headertext" %}

```typescript
import { Grid, ActionEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', textAlign: 'Center', customAttributes: { class: 'orientationcss' }, width: 80 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    created: setHeaderHeight,
    height: 240
});
grid.appendTo('#Grid');

function setHeaderHeight(args: ActionEventArgs): void {
    let textWidth: number = document.querySelector(".orientationcss > div").scrollWidth; // obtain the width of the headerText content.
    let headerCell: NodeList = document.querySelectorAll(".e-headercell");
    for (let i: number = 0; i < headerCell.length; i++) {
        (<HTMLElement>headerCell.item(i)).style.height = textWidth + 'px'; // assign the obtained textWidth as the height of the headerCell.
    }
}

```

{% endtab %}

### Customize the icon for column menu

You can customize the column menu icon by overriding the default grid class `.e-icons.e-columnmenu` with a custom property `content` as mentioned below.

```css
.e-grid .e-columnheader .e-icons.e-columnmenu::before {
              content: "\e941";
      }
```

In the below sample, grid is rendered with a customized column menu icon.

{% tab template="grid/custom-column-menu-icon",es5Template="column-icon" %}

```typescript
import { Grid, ColumnMenu } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(ColumnMenu);

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipName', headerText: 'Ship Name', width: 140 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
    ],
    showColumnMenu: true,
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Editing

### Editing with template column

You can edit the template column value by defining the `field` for that particular column.

In the below demo, the `ShipCountry` column is rendered with the template.

{% tab template="grid/edit-column-template",es5Template="template" %}

```typescript
import { Grid, Edit, Toolbar } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', editType: 'numericedit', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country', template: '#template', editType: 'dropdownedit', width: 150 }
    ],
    height: 265
});
grid.appendTo('#Grid');

```

{% endtab %}

### Customize the edit dialog

You can customize the appearance of the edit dialog in the [`actionComplete`](../api/grid/#actioncomplete) event based on `requestType` as `beginEdit` or `add`.

In the following example, the dialog's header text has been changed for editing and adding the records.

{% tab template="grid/customizedialog", sourceFiles="index.ts,index.css,index.html",es5Template="customizedialog" %}

```typescript
import { Grid, Edit, Toolbar, DialogEditEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120, },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
    ],
    height: 265,
    actionComplete: (args: DialogEditEventArgs) => {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            let dialog: Dialog = args.dialog;
            dialog.height = 400;
            // change the header of the dialog
            dialog.header = args.requestType === 'beginEdit' ? 'Edit Record of ' + args.rowData['CustomerID'] : 'New Customer';
        }
    }
});
grid.appendTo('#Grid');

```

{% endtab %}

### Show or Hide columns in Dialog editing

You can show hidden columns or hide visible column's editor in the dialog while editing the grid record using [`actionBegin`](../api/grid/#actionbegin) and [`actionComplete`](../api/grid/#actioncomplete) events.

In the `actionBegin` event, based on `requestType` as `beginEdit` or  `add`. We can show or hide the editor by using `column.visible` property.

In the `actionComplete` event, based on `requestType` as `save`. We can reset the properties back to the column state.

In the below example, we have rendered the grid columns `CustomerID` as hidden column and `ShipCountry` as visible column. In the edit mode, we have changed the `CustomerID` column to visible state and `ShipCountry` column to hidden state.

{% tab template="grid/grid",es5Template="show-hide-columns" %}

```typescript
import { Grid, Edit, Toolbar, DialogEditEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120, visible: false },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', editType: 'numericedit', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
    ],
    height: 265,
    actionBegin: function(args: DialogEditEventArgs) {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            for (var i = 0; i < this.columns.length; i++) {
                if (this.columns[i].field == "CustomerID") {
                    this.columns[i].visible = true;
                }
                else if (this.columns[i].field == "ShipCountry") {
                    this.columns[i].visible = false;
                }
            }
        }
    },
    actionComplete: function(args: DialogEditEventArgs) {
        if (args.requestType === 'save') {
            for (var i = 0; i < this.columns.length; i++) {
                if (this.columns[i].field == "CustomerID") {
                    this.columns[i].visible = false;
                }
                else if (this.grid.columns[i].field == "ShipCountry") {
                    this.columns[i].visible = true;
                }
            }
        }
    }
});
grid.appendTo('#Grid');

```

{% endtab %}

### Cascading drop-down list with grid editing

You can achieve the Cascading DropDownList with grid Editing by using the Cell Edit Template feature.

In the below demo, Cascading DropDownList is rendered for the `ShipCountry` and `ShipState` column.

{% tab template="grid/grid",es5Template="cascading" %}

```typescript
import { Grid, Edit, Toolbar } from '@syncfusion/ej2-grids';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { Query } from '@syncfusion/ej2-data';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let countryElem: HTMLElement;
let countryObj: DropDownList;

let stateElem: HTMLElement;
let stateObj: DropDownList;

let country: { [key: string]: Object }[] = [
    { countryName: 'United States', countryId: '1' },
    { countryName: 'Australia', countryId: '2' }
];
let state: { [key: string]: Object }[] = [
    { stateName: 'New York', countryId: '1', stateId: '101' },
    { stateName: 'Virginia ', countryId: '1', stateId: '102' },
    { stateName: 'Washington', countryId: '1', stateId: '103' },
    { stateName: 'Queensland', countryId: '2', stateId: '104' },
    { stateName: 'Tasmania ', countryId: '2', stateId: '105' },
    { stateName: 'Victoria', countryId: '2', stateId: '106' }
];

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true, validationRules: { required: true } },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120, validationRules: { required: true, minLength: 3 } },
        {
            field: 'ShipCountry', headerText: 'Ship Country', width: 120, edit: {
                create: () => {
                    countryElem = document.createElement('input');
                    return countryElem;
                },
                read: () => {
                    return countryObj.text;
                },
                destroy: () => {
                    countryObj.destroy();
                },
                write: () => {
                    countryObj = new DropDownList({
                        dataSource: country,
                        fields: { value: 'countryId', text: 'countryName' },
                        change: () => {
                            stateObj.enabled = true;
                            let tempQuery: Query = new Query().where('countryId', 'equal', countryObj.value);
                            stateObj.query = tempQuery;
                            stateObj.text = null;
                            stateObj.dataBind();
                        },
                        placeholder: 'Select a country',
                        floatLabelType: 'Never'
                    });
                    countryObj.appendTo(countryElem);
                }
            }
        },
        {
            field: 'ShipState', headerText: 'Ship State', width: 150, edit: {
                create: () => {
                    stateElem = document.createElement('input');
                    return stateElem;
                },
                read: () => {
                    return stateObj.text;
                },
                destroy: () => {
                    stateObj.destroy();
                },
                write: () => {
                    stateObj = new DropDownList({
                        dataSource: state,
                        fields: { value: 'stateId', text: 'stateName' },
                        enabled: false,
                        placeholder: 'Select a state',
                        floatLabelType: 'Never'
                    });
                    stateObj.appendTo(stateElem);
                }
            }
        }
    ],
    height: 265
});
grid.appendTo('#Grid');

```

{% endtab %}

### Provide custom data source and enabling filtering to DropDownList

You can provide data source to the DropDownList by using the [`columns.edit.params`](../api/grid/column/#edit) property.

While setting new data source using edit params, you must specify a new `query` property too for the dropdownlist as follows,

```typescript
{
    params: {
        query: new Query(),
        dataSource: country,
        fields: { value: 'ShipCountry', text: 'ShipCountry' },
        allowFiltering: true
        }
}
```

You can also enable filtering for the dropdownlist by passing the `allowFiltering` as `true` to the edit params.

In the below demo, DropDownList is rendered with custom Datasource for the `ShipCountry` column and enabled filtering to search dropdownlist items.

{% tab template="grid/grid",es5Template="filteringDropdownlist" %}

```typescript
import { Grid, Edit, Toolbar } from '@syncfusion/ej2-grids';
import { Query } from '@syncfusion/ej2-data';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let country: { [key: string]: Object }[] = [
    { ShipCountry: 'United States', countryId: '1' },
    { ShipCountry: 'Australia', countryId: '2' },
    { ShipCountry: 'India', countryId: '2' }
];

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true, validationRules: { required: true } },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120, validationRules: { required: true, minLength: 3 } },
        {
            field: 'ShipCountry', headerText: 'Ship Country', width: 120, editType: 'dropdownedit', edit: {
                params: {
                    query: new Query(),
                    dataSource: country,
                    fields: { value: 'ShipCountry', text: 'ShipCountry' },
                    allowFiltering: true
                }
            }
        }
    ],
    height: 265
});
grid.appendTo('#Grid');

```

{% endtab %}

### Access Editor components

You can access the component instance from the component element using the `ej2_instances` property.

In the below demo, you can access the Editor component instance while adding or editing actions on the [`actionComplete`](../api/grid/#actioncomplete) event.

{% tab template="grid/grid",es5Template="editor" %}

```typescript
import { Grid, Edit, Toolbar, EditEventArgs, EJ2Intance } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    actionComplete: (args: EditEventArgs) => {
        if (args.requestType === 'beginEdit' || args.requestType === 'add') {
            let tr: Element = args.row;
            let numericTextBox: Element = tr.querySelector('.e-numerictextbox'); // numeric TextBox component element
            if (numericTextBox) {
                console.log('NumericTextBox instance: ', (<EJ2Intance>numericTextBox).ej2_instances[0]); // numeric TextBox instance
            }
            let dropDownList: Element = tr.querySelector('.e-dropdownlist'); // dropDownList component element
            if (dropDownList) {
                console.log('DropDownList instance: ', (<EJ2Intance>dropDownList).ej2_instances[0]); // dropDownList instance
            }
        }
    },
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', editType: 'numericedit', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country', editType: 'dropdownedit', width: 150 }
    ],
    height: 265
});
grid.appendTo('#Grid');

```

{% endtab %}

### Use Wizard like Dialog Editing

Wizard helps you to create intuitive step-by-step forms to fill. You can achieve the wizard-like editing by using the dialog template feature. It supports your own editing template by defining the [`editSettings.mode`](../api/grid/editSettings/#mode) as `Dialog` and [`editSetting.template`](../api/grid/editSettings/#template) as SCRIPT element ID or HTML string which holds the template.

The following example demonstrates the wizard-like editing in the grid with obtrusive validation.

{% tab template="grid/wizardtemplate", sourceFiles="index.ts,index.css,index.html",es5Template="wizardtemplate" %}

```typescript
import { Grid, Edit, Toolbar, DialogEditEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { DataUtil } from '@syncfusion/ej2-data';
import { CheckBox } from '@syncfusion/ej2-buttons';

Grid.Inject(Edit, Toolbar);

let countryData: {}[] = DataUtil.distinct(data, 'ShipCountry', true);

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog', template: '#dialogtemplate' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true, validationRules: { required: true }},
        { field: 'CustomerID', headerText: 'Customer ID', width: 120, validationRules: { required: true }},
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
    ],
    height: 265,
    actionComplete: (args: DialogEditEventArgs) => {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            new DropDownList({value: args.rowData.ShipCountry, popupHeight: '300px', floatLabelType: 'Always',
                dataSource: countryData, fields: {text: 'ShipCountry', value: 'ShipCountry'}, placeholder: 'Ship Country'}, args.form.elements.namedItem('ShipCountry') as HTMLInputElement);
            new CheckBox({ label: 'Verified', checked: args.rowData.Verified }, args.form.elements.namedItem('Verified'));
            // Set initail Focus
            if (args.requestType === 'beginEdit') {
                (args.form.elements.namedItem('CustomerID')as HTMLInputElement).focus();
            }
            initializeWizard();
        }
    }
});
grid.appendTo('#Grid');

function initializeWizard() {
    let currentTab = 0;

    document.getElementById('nextBtn').onclick = function () {
        if (validate()) {
            if (this.innerHTML !== 'SUBMIT'){
                currentTab++;
                nextpre(currentTab);
            } else {
                grid.endEdit();
            }
        }
    }
    function validate(tab) {
        let valid: boolean = true;
            [].slice.call(document.getElementById('tab' + currentTab).querySelectorAll('[name]')).forEach(element => {
            element.form.ej2_instances[0].validate(element.name);
            if (element.getAttribute('aria-invalid') === 'true'){
                valid = false;
            }
        });
        if (!valid) {
        return false;
        }
        return true;
    }
    document.getElementById('prevBtn').onclick = function () {
        if (validate()) {
            currentTab--;
            nextpre(currentTab);
        }
    }
}


function nextpre(current) {
    let tabs: HTMLElement[] = [].slice.call(document.getElementsByClassName('tab'))
    tabs.forEach(element => element.style.display = 'none');
    tabs[current].style.display = '';
    if(current) {
        document.getElementById('prevBtn').style.display = '';
        document.getElementById('nextBtn').innerHTML = 'SUBMIT';
    } else {
        document.getElementById('prevBtn').style.display = 'none';
        document.getElementById('nextBtn').innerHTML = 'NEXT';
    }
}

```

{% endtab %}

### Using the tab inside the dialog template

You can use the [`tab`](../../tab/index.html) component inside the dialog edit UI using the dialog template feature. The dialog template feature can be enabled by defining the [`editSettings.mode`](../api/grid/editSettings/#mode) as `Dialog` and [`editSetting.template`](../api/grid/editSettings/#template) as SCRIPT element ID or HTML string which holds the template.

To include the tab components in the dialog, follow the given steps:

**Step 1**:

Initialize the template for your tab component.

```html
        <div>
        <div id="edittab"></div>
            <div id="tab1">
                <div class="form-row" >
                    <div class="form-group col-md-6">
                        <div class="e-float-input e-control-wrapper">
                            <input id="OrderID" name="OrderID" type="text" value=${if(isAdd)} '' ${else} ${OrderID} ${/if} ${if(isAdd)} '' ${else} disabled ${/if} />
                            <span class="e-float-line"></span>
                            <label class="e-float-text e-label-top" for="OrderID">Order ID</label>
                        </div>
                    </div>
                </div>
                <div class="form-row" >
                    <div class="form-group col-md-6">
                        <div class="e-float-input e-control-wrapper">
                            <input id="CustomerID" name="CustomerID" type="text" value=${if(isAdd)} '' ${else} ${CustomerID} ${/if} />
                            <span class="e-float-line"></span>
                            <label class="e-float-text e-label-top" for="CustomerID">Customer ID</label>
                        </div>
                    </div>
                </div>
                <button id='next' class='e-info e-btn' style="float: right" type='button'> next</button>
            </div>

            <div id="tab2" style='display: none'>
                <div class="form-row" >
                    <div class="form-group col-md-6">
                        <input type="text" name="ShipCountry" id="ShipCountry" value=${if(isAdd)} '' ${else} ${ShipCountry} ${/if} />
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group col-md-6">
                        <input type="checkbox" name="Verified" id="Verified" ${if(isAdd)} '' ${else} checked ${/if} />
                    </div>
                </div>
                <button id='submit' class='e-info e-btn' style="float: right" type='button'> submit</button>
            </div>
        </div>

```

**Step 2**:

To render the tab component, use the [`actionComplete`](../api/grid/#databound) event of the grid.

```typescript

    let tabObj: Tab = new Tab({
        showCloseButton: false,
        selecting:  (e) => {if(e.isSwiped) {e.cancel = true;} if(e.selectingIndex === 1) {e.cancel = !validate(1)}},
        items: [
            { header: { 'text': 'Details' }, content: '#tab1' },
            { header: { 'text': 'Verify' }, content: '#tab2' },
        ]
    });
    tabObj.appendTo('#edittab');

```

The following example demonstrates rendering the tab control inside the edit dialog. The tab control contains two tabs. You can fill the first tab and then navigate to the second tab. The validation for first tab will be done before navigating to the second tab.

{% tab template="grid/tabtemplate", sourceFiles="index.ts,index.css,index.html",es5Template="tabtemplate" %}

```typescript
import { Grid, Edit, Toolbar, DialogEditEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { DataUtil } from '@syncfusion/ej2-data';
import { Tab } from '@syncfusion/ej2-navigations';
import { CheckBox } from '@syncfusion/ej2-buttons';

Grid.Inject(Edit, Toolbar);

let countryData: {}[] = DataUtil.distinct(data, 'ShipCountry', true);

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog', template: '#dialogtemplate' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true, validationRules: { required: true } },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120, validationRules: { required: true } },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
    ],
    height: 265,
    actionComplete: (args: DialogEditEventArgs) => {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {

            let tabObj: Tab = new Tab({
                showCloseButton: false,
                selecting:  (e) => {if(e.isSwiped) {e.cancel = true;} if(e.selectingIndex === 1) {e.cancel = !validate(1)}},
                items: [
                    { header: { 'text': 'Details' }, content: '#tab1' },
                    { header: { 'text': 'Verify' }, content: '#tab2' },
                ]
            });
            tabObj.appendTo('#edittab');

            new DropDownList({value: args.rowData.ShipCountry, popupHeight: '200px', floatLabelType: 'Always',
                dataSource: countryData, fields: {text: 'ShipCountry', value: 'ShipCountry'}, placeholder: 'Ship Country'}, args.form.elements.namedItem('ShipCountry') as HTMLInputElement);

            new CheckBox({ label: 'Verified', checked: args.rowData.Verified }, args.form.elements.namedItem('Verified'));
            // Set initail Focus
            if (args.requestType === 'beginEdit') {
                (args.form.elements.namedItem('CustomerID')as HTMLInputElement).focus();
            }

            document.getElementById('next').onclick = () => {
                moveNext();
            }

            function validate(tab) {
                let valid: boolean = true;
                 [].slice.call(document.getElementById('tab' + tab).querySelectorAll('[name]')).forEach(element => {
                    element.form.ej2_instances[0].validate(element.name);
                    if (element.getAttribute('aria-invalid') === 'true'){
                        valid = false;
                    }
                });
                if (!valid) {
                return false;
                }
                return true;
            }

            function moveNext() {
                if (validate(1)) {
                    tabObj.select(1);
                }
            }
            document.getElementById('submit').onclick = () => {
                if (validate(2)) {
                    grid.endEdit();
                }
            }
        }
    }
});
grid.appendTo('#Grid');

```

{% endtab %}

### Disable editing for a particular row/cell

You can disable the editing for a particular row by using the [`actionBegin`](../api/grid/#actionbegin) event of Grid based on `requestType` as `beginEdit`.

In the below demo, the rows which are having the value for `ShipCountry` column as "France" is prevented from editing.

{% tab template="grid/grid",es5Template="editor" %}

```typescript
import { Grid, Edit, Toolbar, EditEventArgs, EJ2Intance } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    actionBegin: (args: EditEventArgs) => {
        if (args.requestType === 'beginEdit') {
            if (args.rowData.ShipCountry == "France") {
                args.cancel = true;
            }
        }
    },
    toolbar: ['Edit', 'Update', 'Cancel'],
    editSettings: { allowEditing: true },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', editType: 'numericedit', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country', editType: 'dropdownedit', width: 150 }
    ],
    height: 265
});
grid.appendTo('#Grid');

```

{% endtab %}

For batch mode of editing, you can use [`cellEdit`](../api/grid/#celledit) event of Grid. In the below demo, the cells which are having the value as "France" is prevented from editing.

{% tab template="grid/grid",es5Template="editor" %}

```typescript
import { Grid, Edit, Toolbar, EditEventArgs, EJ2Intance } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    cellEdit: (args: EditEventArgs) => {
        if (args.value == "France") {
            args.cancel = true;
        }
    },
    toolbar: ['Edit', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, mode: 'Batch' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', editType: 'numericedit', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country', editType: 'dropdownedit', width: 150 }
    ],
    height: 265
});
grid.appendTo('#Grid');

```

{% endtab %}

### Perform Grid actions by keyboard shortcut keys

Using keyboard shortcuts, Grid performs navigation and actions.

In addition, You can also perform grid actions with custom keyboard shortcuts. This operation has to be achieved outside of the grid with the help of `keydown` event.

The following example demonstrates on `Adding` a new row when `Enter` key is pressed in the grid.

{% tab template="grid/grid",es5Template="keyboard-actions" %}

```typescript
import { Grid, Edit, Toolbar } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true},
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true, validationRules: { required: true }},
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
    ],
    height: 265
});
grid.appendTo('#Grid');

grid.element.addEventListener("keydown", keyDownHandler);

function keyDownHandler(e: any): void {
    if(e.keyCode === 13 ) {
        let gridIns: any = document.getElementById("Grid").ej2_instances[0];
        gridIns.addRecord();
    }
}

```

{% endtab %}

### Make a cell editable on a single click with batch editing

You can make a cell editable on a single click with `batch` mode of editing in Grid, by using the [`editCell`](../api/grid/edit/#editcell) method.

Bind the click event for Grid and in the click event handler call the [`editCell`](../api/grid/edit/#editcell) method, based on the clicked target element.

{% tab template="grid/grid",es5Template="singleclickedit" %}

```typescript
import { Grid, Edit, Toolbar, EditEventArgs, EJ2Intance } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

document.getElementById("Grid").addEventListener("click", (e) => {
    if((event.target as Element).classList.contains("e-rowcell")){
        let gridObj: Grid = (document.getElementsByClassName("e-grid")[0] as Element).ej2_instances[0];
        let index: number = parseInt((event.target as Element).getAttribute("Index"));
        let colindex:number = parseInt((event.target as Element).getAttribute("aria-colindex"));
        let field:string = gridObj.getColumns()[colindex].field;
        gridObj.editModule.editCell(index, field);
    }
});

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', editType: 'numericedit', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country', editType: 'dropdownedit', width: 150 }
    ],
    height: 265
});
grid.appendTo('#Grid');

```

{% endtab %}

## Filter

### Customizing filter menu operators list

 You can customize the default filter operator list by defining the [`filterSettings.operators`](../api/grid/filterSettings/#operators) property.
The available options are:
* `stringOperator`- Defines the customized string operator list.
* `numberOperator` - Defines the customized number operator list.
* `dateOperator` - Defines the customized date operator list.
* `booleanOperator` - Defines the customized Boolean operator list.

The following sample illustrates customizing the string filter operators.

{% tab template="grid/grid",es5Template="customfilter" %}

```typescript
import { Grid, Filter } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Filter);

let grid: Grid = new Grid({
    dataSource: data,
    allowFiltering: true,
    filterSettings: {type:'Menu',
        operators: {
            stringOperator: [
                    { value: 'startsWith', text: 'starts with' },
                    { value: 'endsWith', text: 'ends with' },
                    { value: 'contains', text: 'contains' }],
            }
    },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 273
});
grid.appendTo('#Grid');

```

{% endtab %}

## Sort

### Perform single/multi sorting dynamically

You can perform single-column or multi-column sorting dynamically through an external button.

To perform single-column sorting, use the [`sortColumn`](../api/grid/sort/#sortcolumn) method of Grid.

```typescript
    document.getElementById('SingleSort').addEventListener('click', () => {
        grid.sortColumn("OrderID","Descending")
    });
```

To perform multi-column sorting, you need to push the columns to be sorted into the [`sortSettings.columns`](../api/grid/sortSettings/#columns).

```typescript
    document.getElementById('MultiSort').addEventListener('click', () => {
        grid.sortModule.sortSettings.columns.push({ field: 'ShipCity',  direction: 'Ascending' },{ field: 'ShipName', direction: 'Descending' });
        grid.refresh();
    });
```

In the below demo, click on the corresponding button to perform single-column or multi-column sorting.

{% tab template="grid/sort-how-to", sourceFiles="index.ts,index.html",es5Template="sortdynamically" %}

```typescript
import { Grid, Column, Sort } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

Grid.Inject(Sort)

let grid: Grid = new Grid({
    dataSource: data,
    allowSorting: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 120 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 280
});
grid.appendTo('#Grid');

let singlesort: Button = new Button({ cssClass: 'e-flat' }, '#SingleSort');
let multisort: Button = new Button({ cssClass: 'e-flat' }, '#MultiSort');

document.getElementById('SingleSort').addEventListener('click', () => {
    grid.sortColumn("OrderID","Descending")
});

document.getElementById('MultiSort').addEventListener('click', () => {
    grid.sortModule.sortSettings.columns.push({ field: 'ShipCity',  direction: 'Ascending' },{ field: 'ShipName', direction: 'Descending' });
    grid.refresh();
});

```

{% endtab %}

### Dynamically clear sort for particular/entire sorted columns in Grid

You can clear the sorting for a particular column or the entire sorted columns in Grid dynamically through an external button.

To clear sort for a particular column, you need to splice the particular column from the [`sortSettings.columns`](../api/grid/sortSettings/#columns).

```typescript
    document.getElementById('SingleClearSort').addEventListener('click', () => {
        let column: Column = grid.sortModule.sortSettings.columns;
        for(let i=0;i < column.length;i++){
            if(column[i].field === "OrderID") {
                column.splice(i,1);
                grid.refresh();
            }
        }
    });
```

To clear sorting for all the sorted columns, use the [`clearSorting`](../api/grid/sort/#clearsorting) method of Grid.

```typescript
    document.getElementById('MultiClearSort').addEventListener('click', () => {
        grid.clearSorting();
    });
```

In the below demo, click on the corresponding button to clear sort for particular or entire sorted columns in Grid.

{% tab template="grid/clear-sort-how-to", sourceFiles="index.ts,index.html",es5Template="clearsortdynamic" %}

```typescript
import { Grid, Column, Sort } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

Grid.Inject(Sort)

let grid: Grid = new Grid({
    dataSource: data,
    allowSorting:true,
    sortSettings: { columns: [{ field: 'OrderID', direction: 'Ascending' }, { field: 'CustomerID', direction: 'Descending' },{ field: 'ShipCity', direction: 'Ascending' },{ field: 'ShipName', direction: 'Descending' }] },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 120 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 280
});
grid.appendTo('#Grid');

let singleclear: Button = new Button({ cssClass: 'e-flat' }, '#SingleClearSort');
let multiclear: Button = new Button({ cssClass: 'e-flat' }, '#MultiClearSort');

document.getElementById('SingleClearSort').addEventListener('click', () => {
    let column: Column = grid.sortModule.sortSettings.columns;
    for(let i=0;i < column.length;i++){
        if(column[i].field === "OrderID") {
            column.splice(i,1);
            grid.refresh();
        }
    }
});

document.getElementById('MultiClearSort').addEventListener('click', () => {
    grid.clearSorting();
});

```

{% endtab %}

## Foreign Key

### Use Edit Template in Foreign Key Column

By default, the foreign key column uses the drop-down component for editing. You can render other than the drop-down component by using the [`column.edit`](../api/grid/column/#edit) property. The following example demonstrates the way of using edit template in the foreign column.

In the following code example, the `Employee Name` is a foreign key column. When editing, the AutoComplete component is rendered instead of drop-down list.

{% tab template="grid/foreign-key", es5Template="foreign-edit" %}

```typescript
import { createElement } from '@syncfusion/ej2-base';
import { Grid, ForeignKey, Edit, Toolbar } from '@syncfusion/ej2-grids';
import { AutoComplete } from '@syncfusion/ej2-dropdowns';
import { DataManager, Query } from '@syncfusion/ej2-data';
import { data, employeeData } from './datasource.ts';

Grid.Inject(ForeignKey, Edit, Toolbar);

let autoComplete: AutoComplete;

let grid: Grid = new Grid(
        {
            dataSource: data,
            editSettings: { allowEditing: true },
            toolbar: ['Edit', 'Update', 'Cancel'],
            columns: [
                { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
                // Foreign column
                {
                    field: 'EmployeeID', headerText: 'Employee Name', width: 150, foreignKeyValue: 'LastName', dataSource: employeeData,
                    edit: {
                            create: () => { // to create input element
                                return createElement('input');
                            },
                            read: () => { // return edited value to update data source
                                let value: Object[] = new DataManager(employeeData).executeLocal(new Query().where('LastName', 'equal', autoComplete.value));
                                return value.length && value[0]['EmployeeID']; // to convert foreign key value to local value.
                            },
                            destroy: () => { // to destroy the custom component.
                                autoComplete.destroy();
                            },
                            write: (args: { rowData: Object, column: Column, foreignKeyData: Object }) => { // to show the value for custom component
                                autoComplete = new AutoComplete({
                                    dataSource: employeeData,
                                    fields: { value: args.column.foreignKeyValue },
                                    value: args.foreignKeyData[0][args.column.foreignKeyValue]
                                });
                                autoComplete.appendTo(args.element);
                            }
                        }
                },
                { field: 'Freight', headerText: 'Freight', width: 100, textAlign: 'Right'},
                { field: 'ShipName', headerText: 'Ship Name', width: 180 }
            ],
            height: 265
        });
    grid.appendTo('#Grid');

```

{% endtab %}

### Customize filter UI in foreign key column

You can create your own filtering UI by using [`column.filter`](../api/grid/column/#filter) property. The following example demonstrates the way to create a custom filtering UI in the foreign column.

In the following example, The `Employee Name` is a foreign key column. DropDownList is rendered using Filter UI.

{% tab template="grid/foreign-key", es5Template="foreign-fui" %}

```typescript
import { createElement } from '@syncfusion/ej2-base';
import { DataManager } from '@syncfusion/ej2-data';
import { Grid, ForeignKey, Filter } from '@syncfusion/ej2-grids';
import { data, fEmployeeData } from './datasource.ts';
import { DropDownList } from '@syncfusion/ej2-dropdowns';

Grid.Inject(ForeignKey, Filter);

let grid: Grid = new Grid(
    {
        dataSource: data,
        allowFiltering: true,
        filterSettings: {type: 'Menu'},
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
            // Foreign column
            {
                field: 'EmployeeID', headerText: 'Employee Name', width: 150, foreignKeyValue: 'FirstName', dataSource: fEmployeeData,
                filter: {
                        ui: {
                            create: (args: { target: Element, column: Object }) => {
                                let flValInput: HTMLElement = createElement('input', { className: 'flm-input' });
                                args.target.appendChild(flValInput);
                                this.dropInstance = new DropDownList({
                                    dataSource: new DataManager(fEmployeeData),
                                    fields: { text: 'FirstName', value: 'EmployeeID' },
                                    placeholder: 'Select a value',
                                    popupHeight: '200px'
                                });
                                this.dropInstance.appendTo(flValInput);
                            },
                            write: (args: {
                                column: Object, target: Element, parent: any,
                                filteredValue: number | string
                            }) => {
                                this.dropInstance.text = args.filteredValue || '';
                            },
                            read: (args: { target: Element, column: any, operator: string, fltrObj: Filter }) => {
                                args.fltrObj.filterByColumn(args.column.field, args.operator, this.dropInstance.text);
                            }
                        }
                    }
            },
            { field: 'Freight', headerText: 'Freight', width: 100, textAlign: 'Right'},
            { field: 'ShipName', headerText: 'Ship Name', width: 180 }
        ],
        height: 315
    });
    grid.appendTo('#Grid');

```

{% endtab %}

### Use filter bar template in foreign key column

You can use the filter bar template in foreign key column by defining the [`column.filterBarTemplate`](../api/grid/column/#filterbartemplate) property. The following example demonstrates the way to use filter bar template in foreign column.

In the following example, The `Employee Name` is a foreign key column. This column header shows the custom filter bar template and you can select filter value by using the `DropDown` options.

{% tab template="grid/foreign-key", es5Template="foreign-ftemp" %}

```typescript
import { Grid, ForeignKey, Filter } from '@syncfusion/ej2-grids';
import { data, fEmployeeData } from './datasource.ts';
import { createElement } from '@syncfusion/ej2-base';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { DataManager } from '@syncfusion/ej2-data';

Grid.Inject(ForeignKey, Filter);

let grid: Grid = new Grid(
    {
        dataSource: data,
        allowFiltering: true,
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
            // Foreign column
            {
                field: 'EmployeeID', headerText: 'Employee Name', width: 150, foreignKeyValue: 'FirstName', dataSource: fEmployeeData,
                filterBarTemplate: {
                    create: (args: { element: Element, column: Column }) =>
                        return createElement('input', { className: 'flm-input' });;
                    },
                    write: (args: { element: Element, column: Column }) => {
                        fEmployeeData.splice(0, 0, {'FirstName': 'All'}); // for clear filtering
                        let dropInstance: DropDownList = new DropDownList({
                            dataSource: new DataManager(fEmployeeData),
                            fields: { text: 'FirstName' },
                            placeholder: 'Select a value',
                            popupHeight: '200px',
                            index: 0,
                            change: (args) => {
                                if (args.value !== 'All') {
                                    grid.filterByColumn('EmployeeID', 'equal', args.value);
                                }
                                else {
                                    grid.removeFilteredColsByField('EmployeeID');
                                }
                            }
                        });
                        dropInstance.appendTo(args.element);
                    }
                }
            },
            { field: 'Freight', headerText: 'Freight', width: 100, textAlign: 'Right'},
            { field: 'ShipName', headerText: 'Ship Name', width: 180 }
        ],
        height: 260
    });
    grid.appendTo('#Grid');

```

{% endtab %}

### Perform aggregation in Foreign Key Column

Default aggregations are not supported in a foreign key column. You can achieve aggregation for the foreign key column by using the custom aggregates. The following example demonstrates the way to achieve aggregation in foreign key column.

In the following example, The `Employee Name` is a foreign key column and the aggregation for the foreign column was calculated in customAggregateFn.

{% tab template="grid/foreign-key", es5Template="foreign-aggregate" %}

```typescript
import { Grid, ForeignKey, Aggregate, getForeignData, CustomSummaryType, AggregateColumnModel } from '@syncfusion/ej2-grids';
import { data, employeeData } from './datasource.ts';
import { getValue } from '@syncfusion/ej2-base';

Grid.Inject(ForeignKey, Aggregate);

// Custom Aggregate function for foreign column
let customAggregateFn: CustomSummaryType = (data: Object, column: AggregateColumnModel) => {
    return data.result.filter((dObj: Object) => {
        return getValue('FirstName' , getForeignData(grid.getColumnByField(column.columnName), dObj)[0]) === 'Margaret';
    }).length;
};

let grid: Grid = new Grid(
    {
        dataSource: data,
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
            // Foreign column
            {
                field: 'EmployeeID', headerText: 'Employee Name', width: 150, foreignKeyValue: 'FirstName', dataSource: employeeData,
            },
            { field: 'Freight', headerText: 'Freight', width: 100, textAlign: 'Right'},
            { field: 'ShipName', headerText: 'Ship Name', width: 180 }
        ],
        height: 280,
        aggregates: [
            {
                columns: [
                    {
                        type: 'Custom',
                        customAggregate: customAggregateFn,
                        field: 'EmployeeID',
                        footerTemplate: 'Count of Margaret: ${Custom}'
                    }
                ]
            }
        ]
    });
    grid.appendTo('#Grid');

```

{% endtab %}

### Bind foreign key dataSource on dropdown edit

When editing, you can bind foreign key datasource to a dropdown list by using [`column.dataSource`](../api/grid/column/#datasource) property.

{% tab template="grid/grid", es5Template="foreignkeydatadropdown" %}

```typescript
import { Grid, ForeignKey, Edit, Toolbar } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { employeeData } from './employeeData.ts'

Grid.Inject(ForeignKey, Edit, Toolbar);

let grid: Grid = new Grid(
    {
        dataSource: data.slice(0,10),
        toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
        editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
            {
                field: 'EmployeeID', headerText: 'Employee Name', width: 150, foreignKeyValue: 'FirstName', dataSource: employeeData
            },
            { field: 'Freight', headerText: 'Freight', width: 100, textAlign: 'Right'},
            { field: 'ShipName', headerText: 'Ship Name', width: 180 }
        ],
        height: 315
    });
grid.appendTo('#Grid');

```

{% endtab %}

> * By default, the foreign key column's `editType` will be set as `dropdownedit`.

## Exporting

### Exporting Grid in Cordova application

Cordova application does not support direct file download. So we have to use the Blob stream to export the Grid.
You can use corresponding exporting methods and exportComplete events to get the Blob stream.

{% tab template="grid/exporting-blob-data", es5Template="export-blob-data" %}

```typescript
import { EmitType } from '@syncfusion/ej2-base'
import { Grid, Page, Toolbar, ExcelExport, ExcelExportCompleteArgs, PdfExport, PdfExportCompleteArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page, Toolbar, ExcelExport, PdfExport);
/**
 * Exporting Blob data
 */

let excelExpComplete: EmitType<ExcelExportCompleteArgs> = (args: ExcelExportCompleteArgs) => {
        //This event will be triggered when excel exporting.
            args.promise.then((e: { blobData: Blob }) => {
        //In this `then` function, we can get blob data through the arguments after promise resolved.
                exportBlob(e.blobData);
    });
};
let pdfExpComplete: EmitType<PdfExportCompleteArgs> = (args: PdfExportCompleteArgs) => {
    //This event will be triggered when pdf exporting.
        args.promise.then((e: { blobData: Blob }) => {
        //In this `then` function, we can get blob data through the arguments after promise resolved.
        exportBlob(e.blobData);
    });
};


let exportBlob: Function = (blob: Blob) => {
    let a: HTMLAnchorElement = document.createElement('a');
    document.body.appendChild(a);
    a.style.display = 'none';
    let url: string = window.URL.createObjectURL(blob);
    a.href = url;
    a.download = 'Export';
    a.click();
    window.URL.revokeObjectURL(url);
    document.body.removeChild(a);
}

let grid: Grid = new Grid(
    {
        dataSource: data,
        allowExcelExport: true,
        allowPdfExport: true,
        excelExportComplete: excelExpComplete,
        pdfExportComplete: pdfExpComplete,
        toolbar: ['PdfExport','ExcelExport'],
        columns: [
            {
                field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 90
            },
            {
                field: 'CustomerID', headerText: 'Customer ID', width: 90
            },
            { field: 'ShipCountry', headerText: 'ShipCountry', width: 90 },
        ]
    });
grid.appendTo('#Grid');
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_pdfexport') {
        grid.pdfExport(null, null, null, true);
    }
    if (args['item'].id === 'Grid_excelexport') {
        grid.excelExport(null, null, null, true);
    }

}

```

{% endtab %}

### Exporting Filtered Data Only

You can export the filtered data by defining the resulted data in `exportProperties.dataSource` before export.

In the below Pdf exporting demo, We have gotten the filtered data by applying filter query to the grid data and then defines the resulted data in `exportProperties.dataSource` and pass it to `pdfExport` method.

{% tab template="grid/exporting-filtered-data", es5Template="export-filtered-data" %}

```typescript
import { Grid, Page, Toolbar, PdfExport, Filter } from '@syncfusion/ej2-grids';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { data } from './datasource.ts';
import {DataManager} from '@syncfusion/ej2-data';

Grid.Inject(Page, Toolbar, PdfExport, Filter);
let grid: Grid = new Grid(
    {
        dataSource: data,
        allowPdfExport: true,
        allowPaging: true,
        allowFiltering: true,
        toolbar: ['PdfExport'],
        pageSettings: { pageCount: 5, pageSize: 5 },
        columns: [
            { field: 'OrderID', headerText: 'Order ID', width: 120, textAlign: 'Right' },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'OrderDate', headerText: 'Order Date', width: 130, format: 'yMd', textAlign: 'Right' },
            { field: 'Freight', width: 120, format: 'C2', textAlign: 'Right' },
            { field: 'ShipCountry', visible: false, headerText: 'Ship Country', width: 150 }
        ],
    });
grid.appendTo('#Grid');
grid.toolbarClick = (args: ClickEventArgs) => {
    if (args.item.id === 'Grid_pdfexport') {
        let pdfdata;
        let query = grid.renderModule.data.generateQuery(); // get grid corresponding query
        for (var i = 0; i < query.queries.length; i++) {
            if (query.queries[i].fn == 'onPage') {
                query.queries.splice(i, 1);    // remove page query to get all records
                break;
            }
        }
        let fdata = new DataManager({ json: data }).executeQuery(query).then((e: any) => {
            pdfdata = <Object[]>e.result;   // get all filtered records
            let exportProperties = {
                dataSource: pdfdata,
            };
            grid.pdfExport(exportProperties);
        }).catch((e) => true);
    }
}

```

{% endtab %}

## Pager

### Customize pager drop-down

To customize the default values of pager drop-down, you need to define the [`pageSizes`](../api/grid/pageSettingsModel/#pagesizes) as array of strings.

{% tab template="grid/pagerdropdown",es5Template="pagerdropdown" %}

```typescript
import { Grid, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    pageSettings:{pageSizes: ["5", "10", "All"]},
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
});
grid.appendTo('#Grid');

```

{% endtab %}

## Hide the expand/collapse icon in parent row with no record in child grid

By default, the expand/collapse icon will be visible even if the child grid is empty.

You can use [`rowDataBound`](../api/grid/#rowdatabound) event to hide the icon when there is no record in child grid.

To hide the expand/collapse icon in parent row with no record in child grid, follow the given steps:

**Step 1**:

Create CSS class with custom style to override the default style of Grid.

```css
    .e-row[aria-selected="true"] .e-customizedExpandcell {
        background-color: #e0e0e0;
    }

    .e-grid.e-gridhover tr[role='row']:hover {
        background-color: #eee;
    }

```

**Step 2**:

Add the CSS class to the Grid in the [`rowDataBound`](../api/grid/#rowdatabound) event handler of Grid.

```typescript
    function rowDataBound(args:any):void{
        var filter = args.data.EmployeeID;
        var data = new DataManager(this.childGrid.dataSource).executeLocal(new Query().where("EmployeeID", "equal", parseInt(filter), true));
        if(data.length == 0) {
            //here hide which parent row has no child records
            args.row.querySelector('td').innerHTML=" ";
            args.row.querySelector('td').className = "e-customizedExpandcell";
        }
    }

```

In the below demo, the expand/collapse icon in the row with `EmployeeID` as `1` is hidden as it does not have record in child Grid.

{% tab template="grid/grid", es5Template="hide-expand-collapse" %}

```typescript
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
import { Grid, Page, Selection, DetailRow } from '@syncfusion/ej2-grids';
import { DataManager, Query } from '@syncfusion/ej2-data';
import { employeeData } from './employeeData.ts';

Grid.Inject(Page, Selection, DetailRow);

    let dataManger: Object = [{Order:100, ShipName:'Berlin', EmployeeID:2},
    {Order:101, ShipName:'Capte', EmployeeID:3},
    {Order:102, ShipName:'Marlon', EmployeeID:4},
    {Order:103, ShipName:'Black pearl', EmployeeID:5},
    {Order:104, ShipName:'Pearl', EmployeeID:6},
    {Order:105, ShipName:'Noth bay', EmployeeID:7},
    {Order:106, ShipName:'baratna', EmployeeID:8},
    {Order:107, ShipName:'Charge', EmployeeID:9},
    ];
    let grid: Grid = new Grid({
        dataSource: employeeData,
        allowSorting: true,
        rowDataBound:rowDataBound,
        columns: [
            { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 125 },
            { field: 'FirstName', headerText: 'Name', width: 125 },
            { field: 'Title', headerText: 'Title', width: 180 },
            { field: 'City', headerText: 'City', width: 110 },
            { field: 'Country', headerText: 'Country', width: 110 }
        ],
        childGrid: {
            dataSource: dataManger,
            queryString: 'EmployeeID',
            allowPaging: true,
            columns: [
                { field: 'Order', headerText: 'Order ID', textAlign: 'Right', width: 120 },
                { field: 'EmployeeID', headerText: 'Employee ID', width: 120 },
                { field: 'ShipName', headerText: 'Ship Name', width: 150 }
            ],
        },
    });
    grid.appendTo('#Grid');
    function rowDataBound(args:any):void{
        var filter = args.data.EmployeeID;
        var data = new DataManager(this.childGrid.dataSource).executeLocal(new Query().where("EmployeeID", "equal", parseInt(filter), true));
        if(data.length == 0) {
            //here hide which parent row has no child records
            args.row.querySelector('td').innerHTML=" ";
            args.row.querySelector('td').className = "e-customizedExpandcell";
        }
    }
```

{% endtab %}