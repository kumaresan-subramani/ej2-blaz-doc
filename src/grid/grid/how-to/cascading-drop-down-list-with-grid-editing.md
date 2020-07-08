---
title: "Cascading DropDownList with Grid editing"
component: "Grid"
description: "Learn how to Cascading DropDownList with Grid editing."
---

# Cascading DropDownList with Grid editing

You can achieve the Cascading DropDownList with grid Editing by using the Cell Edit Template feature.

In the below demo, Cascading DropDownList is rendered for the `ShipCountry` and `ShipState` column.

{% tab template="grid/grid",es5Template="cascading" %}

```typescript
import { Grid, Edit, Toolbar } from '@syncfusion/ej2-grids';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { Query } from '@syncfusion/ej2-data';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let countryElem: HTMLElement;
let countryObj: DropDownList;

let stateElem: HTMLElement;
let stateObj: DropDownList;

let country: { [key: string]: Object }[] = [
    { countryName: 'United States', countryId: '1' },
    { countryName: 'Australia', countryId: '2' }
];
let state: { [key: string]: Object }[] = [
    { stateName: 'New York', countryId: '1', stateId: '101' },
    { stateName: 'Virginia ', countryId: '1', stateId: '102' },
    { stateName: 'Washington', countryId: '1', stateId: '103' },
    { stateName: 'Queensland', countryId: '2', stateId: '104' },
    { stateName: 'Tasmania ', countryId: '2', stateId: '105' },
    { stateName: 'Victoria', countryId: '2', stateId: '106' }
];

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true, validationRules: { required: true } },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120, validationRules: { required: true, minLength: 3 } },
        {
            field: 'ShipCountry', headerText: 'Ship Country', width: 120, edit: {
                create: () => {
                    countryElem = document.createElement('input');
                    return countryElem;
                },
                read: () => {
                    return countryObj.text;
                },
                destroy: () => {
                    countryObj.destroy();
                },
                write: () => {
                    countryObj = new DropDownList({
                        dataSource: country,
                        fields: { value: 'countryId', text: 'countryName' },
                        change: () => {
                            stateObj.enabled = true;
                            let tempQuery: Query = new Query().where('countryId', 'equal', countryObj.value);
                            stateObj.query = tempQuery;
                            stateObj.text = null;
                            stateObj.dataBind();
                        },
                        placeholder: 'Select a country',
                        floatLabelType: 'Never'
                    });
                    countryObj.appendTo(countryElem);
                }
            }
        },
        {
            field: 'ShipState', headerText: 'Ship State', width: 150, edit: {
                create: () => {
                    stateElem = document.createElement('input');
                    return stateElem;
                },
                read: () => {
                    return stateObj.text;
                },
                destroy: () => {
                    stateObj.destroy();
                },
                write: () => {
                    stateObj = new DropDownList({
                        dataSource: state,
                        fields: { value: 'stateId', text: 'stateName' },
                        enabled: false,
                        placeholder: 'Select a state',
                        floatLabelType: 'Never'
                    });
                    stateObj.appendTo(stateElem);
                }
            }
        }
    ],
    height: 265
});
grid.appendTo('#Grid');

```

{% endtab %}
