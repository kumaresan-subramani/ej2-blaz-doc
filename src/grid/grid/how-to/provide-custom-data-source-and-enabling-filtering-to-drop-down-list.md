---
title: "Provide custom data source and enabling filtering to DropDownList"
component: "Grid"
description: "Learn how to Provide custom data source and enabling filtering to DropDownList."
---

# Provide custom data source and enabling filtering to DropDownList

You can provide data source to the DropDownList by using the [`columns.edit.params`](../../api/grid/column/#edit) property.

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
