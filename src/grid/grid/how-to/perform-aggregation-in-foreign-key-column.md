---
title: "Perform aggregation in Foreign Key Column"
component: "Grid"
description: "Learn how to Perform aggregation in Foreign Key Column."
---

# Perform aggregation in Foreign Key Column

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
