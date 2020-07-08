---
title: "Paging"
component: "Grid"
description: "Learn how to add custom elements in Pager using pager template and customize the pager in the Essential JS 2 DataGrid control."
---

# Paging

Paging provides an option to display Grid data in page segments. To enable paging, set the [`allowPaging`](../api/grid/#allowpaging-boolean) to true. When paging is enabled, pager component renders at the bottom of the grid.
Paging options can be configured through the [`pageSettings`](../api/grid/pageSettings).

In the below sample, `pageSize` is calculated based on the grid height by using the `load` event.

To use paging, inject the [`Page`](../api/grid/page) module in the grid.

{% tab template="grid/grid",es5Template="paging" %}

```typescript
import { Grid, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 130 },
        { field: 'ShipCity', headerText: 'Ship City', width: 140 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    height: 325,
    load: () => {
        let rowHeight: number = grid.getRowHeight();  //height of the each row
        let gridHeight: number = grid.height;  //grid height
        let pageSize: number = grid.pageSettings.pageSize;   //initial page size
        let pageResize: any = (gridHeight - (pageSize * rowHeight)) / rowHeight; //new page size is obtained here
        grid.pageSettings.pageSize = pageSize + Math.round(pageResize);
    }
});
grid.appendTo('#Grid');

```

{% endtab %}

> You can achieve better performance by using grid paging to fetch only a pre-defined number of records from the data source.

## Template

You can use custom elements inside the pager instead of default elements.
The custom elements can be defined by using the [`template`](../api/grid/pageSettings/#template) property.
Inside this template, you can access the [`CurrentPage`](../api/grid/pageSettings/#currentpage), [`pageSize`](../api/grid/pageSettings/#pagesize), [`pageCount`](../api/grid/pageSettings/#pagecount), `totalPage` and `totalRecordCount` values.

{% tab template="grid/pager-template", sourceFiles="index.ts,index.html,index.css",es5Template="template" %}

```typescript
import { Grid, Page, PageEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { NumericTextBox } from '@syncfusion/ej2-inputs';

Grid.Inject(Page);
let updateTemplate: Function = () => {
    let numeric: NumericTextBox;
    this.numeric = new NumericTextBox({
        min: 1,
        max: 3,
        step: 1,
        format: '###.##',
        change: (args) => {
            let value: number = args.value;
            grid.goToPage(value);
        }
    });
    this.numeric.appendTo('#currentPage');
};
let flag: boolean = true;
let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    pageSettings: { template: '#template', pageSize: 7 },
    dataBound: () => {
        if (flag) {
            flag = false;
            updateTemplate();
        }
    },
    actionComplete: (args: PageEventArgs) => {
        if (args.requestType === 'paging') {
            updateTemplate();
        }
    }
});
grid.appendTo('#Grid');

```

{% endtab %}

## Pager with Page Size Dropdown

The pager Dropdown allows you to change the number of records in the Grid dynamically. It can be enabled by defining the `pageSettings.pageSizes` property as true.

{% tab template="grid/grid",es5Template="pagerdropdown" %}

```typescript
import { Grid, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    pageSettings: { pageSizes: true, pageSize: 8 }
});
grid.appendTo('#Grid');

```

{% endtab %}

## How to render Pager at the Top of the Grid

By default, Pager will be rendered at the bottom of the Grid. You can also render the Pager at the top of the Grid by using the `dataBound` event.

{% tab template="grid/grid",es5Template="pagerattop" %}

```typescript
import { Grid, Page, Toolbar } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page, Toolbar);

let initialGridLoad: boolean = true;
let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    pageSettings: { pageSizes: true, pageSize: 9 }
});
grid.appendTo('#Grid');

grid.dataBound = () =>{
    if (initialGridLoad) {
        initialGridLoad = false;
        var pager = document.getElementsByClassName('e-gridpager');
        var topElement;
        if (grid.allowGrouping || grid.toolbar) {
            topElement = grid.allowGrouping ? document.getElementsByClassName('e-groupdroparea') :
                        document.getElementsByClassName('e-toolbar');
        } else {
            topElement = document.getElementsByClassName('e-gridheader');
        }
        grid.element.insertBefore(pager[0], topElement[0]);
    }
};

```

{% endtab %}

> During the paging action, the pager component triggers the below three events.
> * The `created` event triggers when Pager is created.
> * The `click` event triggers when the numeric items in the pager is clicked.
> * The `dropDownChanged` event triggers when pageSize DropDownList value is selected.

## See Also

* [Group with Paging](./grouping##group-with-paging)
