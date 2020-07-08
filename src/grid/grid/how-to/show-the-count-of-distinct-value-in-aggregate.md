---
title: "How to show the count of distinct values in aggregate row"
component: "Grid"
description: "Learn how to show the count of distinct values by using aggregate in the Essential JS 2 DataGrid control."
---

# Show the count of distinct values in aggregate row

You can calculate the aggregate value with your own aggregate functions. To use custom aggregation, specify the [`type`](../api/grid/aggregateColumn/#type) as `Custom`, and provide the custom aggregate function in the [`customAggregate`](../api/grid/aggregateColumn/#customaggregate) property.

In this below demo, we have show the count of distinct value for `ShipCountry` column by using custom aggregate.

{% tab template="grid/custom-agg", es5Template="agg" %}

```typescript
import { Grid, Page, Aggregate  } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { DataManager, Query, DataUtil } from '@syncfusion/ej2-data';

Grid.Inject(Page, Aggregate );


let customAggregateFn = function() {
let results = new DataManager(this.currentViewData).executeLocal(new Query().select(['ShipCountry']));
let distinct = DataUtil.distinct(results, 'ShipCountry', true);
return distinct.length;
}

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C2' },
        { field: "ShipCountry", headerText: "Ship Country", width: 150 }
    ],
    height: 220,
     aggregates: [{
        columns: [{
            type: 'Custom',
            customAggregate: customAggregateFn,
            columnName: 'ShipCountry',
            footerTemplate: 'Distinct Count: ${Custom}'
        }]
    }]
});
grid.appendTo('#Grid');

```

{% endtab %}