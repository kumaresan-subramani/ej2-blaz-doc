---
title: "Customizing filter menu operators list"
component: "Grid"
description: "Learn how to customize filter menu operators list."
---

# Customizing filter menu operators list

 You can customize the default filter operator list by defining the [`filterSettings.operators`](../../api/grid/filterSettings/#operators) property.
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
