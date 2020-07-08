---
title: "Customizing Filter Dialog by using additional Parameter"
component: "Grid"
description: "Learn how to customize the filter dialog in Grid by using an additional Parameter."
---

# Customizing Filter Dialog by using an additional Parameter

You can customize the default settings of the components which are used in Menu filter by using params of filter property in column definition.
In the below sample, OrderID and Freight Columns are numeric columns, while open the filter dialog then you can see that NumericTextBox with spin button is displayed to change/set the filter value. Now using the params option we hide the spin button in NumericTextBox for OrderID Column.

{% tab template="grid/grid", es5Template="add-params"  %}

```typescript
import { Grid, Filter } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Filter);

    let grid: Grid = new Grid(
        {
            dataSource: data,
            allowFiltering: true,
            filterSettings: { type: 'Menu'},
            columns: [
                { field: 'OrderID', headerText: 'Order ID', width: 120, textAlign: 'Right', filter: { params: {showSpinButton: false}}},
                { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
                { field: 'OrderDate', headerText: 'Order Date', width: 130, format: 'yMd', textAlign: 'Right' },
                { field: 'Freight', width: 120, format: 'C2', textAlign: 'Right'}
            ],
            height: 315
        });
    grid.appendTo('#Grid');

```

{% endtab %}