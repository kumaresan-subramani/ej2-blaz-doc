---
title: "Use filter bar template in foreign key column"
component: "Grid"
description: "Learn how to use filter bar template in foreign key column."
---

# Use filter bar template in foreign key column

You can use the filter bar template in foreign key column by defining the [`column.filterBarTemplate`](../../api/grid/column/#filterbartemplate) property. The following example demonstrates the way to use filter bar template in foreign column.

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
