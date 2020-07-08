---
title: "Use Edit Template in Foreign Key Column"
component: "Grid"
description: "Learn how to Use Edit Template in Foreign Key Column."
---

# Use Edit Template in Foreign Key Column

By default, the foreign key column uses the drop-down component for editing. You can render other than the drop-down component by using the [`column.edit`](../../api/grid/column/#edit) property. The following example demonstrates the way of using edit template in the foreign column.

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
