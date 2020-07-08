---
title: "Set complex column as Foreignkey column"
component: "Grid"
description: "Learn how to set complex column as Foreignkey column."
---

# Set complex column as Foreignkey column

The following example shows how to set the complex column as foreign key column.

In the following example, `Employee.EmployeeID` is a complex column and also declared as a foreign column which shows `FirstName` column from foreign data.

{% tab template="grid/foreign-key", sourceFiles="index.ts,datasource.ts", es5Template="complex-foreign-key" %}

```typescript
import { Grid, ForeignKey } from '@syncfusion/ej2-grids';
import { data, employeeData } from './datasource.ts';

Grid.Inject(ForeignKey);

let grid: Grid = new Grid(
    {
        dataSource: data.slice(0,5),
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
            {
                field: 'Employee.EmployeeID', foreignKeyField: 'EmployeeID', headerText: 'Employee Name', width: 150, foreignKeyValue: 'FirstName', dataSource: employeeData
            },
            { field: 'Freight', headerText: 'Freight', width: 100, textAlign: 'Right'},
            { field: 'ShipName', headerText: 'Ship Name', width: 180 }
        ],
        height: 315
    });
grid.appendTo('#Grid');

```

{% endtab %}