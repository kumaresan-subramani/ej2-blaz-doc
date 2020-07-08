---
title: "Access Editor components"
component: "Grid"
description: "Learn how to access Editor components."
---

# Access Editor components

You can access the component instance from the component element using the `ej2_instances` property.

In the below demo, you can access the Editor component instance while adding or editing actions on the [`actionComplete`](../../api/grid/#actioncomplete) event.

{% tab template="grid/grid",es5Template="editor" %}

```typescript
import { Grid, Edit, Toolbar, EditEventArgs, EJ2Intance } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    actionComplete: (args: EditEventArgs) => {
        if (args.requestType === 'beginEdit' || args.requestType === 'add') {
            let tr: Element = args.row;
            let numericTextBox: Element = tr.querySelector('.e-numerictextbox'); // numeric TextBox component element
            if (numericTextBox) {
                console.log('NumericTextBox instance: ', (<EJ2Intance>numericTextBox).ej2_instances[0]); // numeric TextBox instance
            }
            let dropDownList: Element = tr.querySelector('.e-dropdownlist'); // dropDownList component element
            if (dropDownList) {
                console.log('DropDownList instance: ', (<EJ2Intance>dropDownList).ej2_instances[0]); // dropDownList instance
            }
        }
    },
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', editType: 'numericedit', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country', editType: 'dropdownedit', width: 150 }
    ],
    height: 265
});
grid.appendTo('#Grid');

```

{% endtab %}
