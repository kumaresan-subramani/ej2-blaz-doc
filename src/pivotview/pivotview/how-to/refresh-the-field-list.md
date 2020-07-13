# Refresh the field list while change the data source

You can refresh pivot table and field list with new data source dynamically.

{% tab template="pivot-table/refresh-field-list", es5Template="refresh-field-list", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, FieldList } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';

PivotView.Inject(FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: [
            { 'Sold': 31, 'Amount': 52824, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q1' },
            { 'Sold': 51, 'Amount': 86904, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q2' },
            { 'Sold': 90, 'Amount': 153360, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q3' },
            { 'Sold': 25, 'Amount': 42600, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q4' },
            { 'Sold': 27, 'Amount': 46008, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2016', 'Quarter': 'Q1' }],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

let btn: Button = new Button({ isPrimary: true });
btn.appendTo('#Refresh');

document.getElementById('Refresh').addEventListener('click', () => {
    pivotTableObj.engineModule.fieldList = {};
      pivotTableObj.dataSourceSettings.dataSource = [
            { 'Sold': 31, 'Amount': 52824, 'Country': 'France', 'Year': 'FY 2015' },
            { 'Sold': 51, 'Amount': 86904, 'Country': 'France', 'Year': 'FY 2015' },
            { 'Sold': 90, 'Amount': 153360, 'Country': 'France', 'Year': 'FY 2015' },
            { 'Sold': 25, 'Amount': 42600, 'Country': 'France', 'Year': 'FY 2015' },
            { 'Sold': 27, 'Amount': 46008, 'Country': 'France', 'Year': 'FY 2016' }];
});

```

{% endtab %}
