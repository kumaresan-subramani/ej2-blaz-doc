---
title: "Hide the expand/collapse icon in parent row with no record in child grid"
component: "Grid"
description: "Learn how to Hide the expand/collapse icon in parent row with no record in child grid."
---

# Hide the expand/collapse icon in parent row with no record in child grid

By default, the expand/collapse icon will be visible even if the child grid is empty.

You can use [`rowDataBound`](../../api/grid/#rowdatabound) event to hide the icon when there is no record in child grid.

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

Add the CSS class to the Grid in the [`rowDataBound`](../../api/grid/#rowdatabound) event handler of Grid.

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
