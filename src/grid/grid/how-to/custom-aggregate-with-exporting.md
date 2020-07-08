---
title: "Custom Aggregate with Exporting"
component: "Grid"
description: "Learn how to Export the custom aggregate"
---

# Custom Aggregate with Exporting

The following example shows how to export the grid with custom aggregate.

{% tab template="grid/grid", es5Template="aggregate-exporting" %}

```typescript
import { Grid, Aggregate, Toolbar, ExcelExport, PdfExport } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';

Grid.Inject(Toolbar, ExcelExport, PdfExport, Aggregate);

function customAggregateFn (data: any) {
if(data.result)
return data.result.filter(item => item['ShipCountry'] === 'Brazil').length;
 else {
  return data.filter(item => item['ShipCountry'] === 'Brazil').length;
 }
}

let grid: Grid = new Grid({
  dataSource: data
  allowExcelExport: true,
  allowPdfExport: true,
  toolbar: ['ExcelExport', 'PdfExport', 'CsvExport'],
  columns: [
    { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
    { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
    { field: 'Freight', headerText: 'Freight', width: 150, format: 'C2' },
    { field: 'ShipCountry', headerText: 'Ship Name', width: 150 }
  ],
  height: 268,
  aggregates: [{
    columns: [{
      type: 'Custom',
      customAggregate: customAggregateFn,
      columnName: 'ShipCountry',
      footerTemplate: 'Brazil Count: ${Custom}'
    }]
  }]
});
grid.appendTo('#Grid');

grid.toolbarClick = (args: ClickEventArgs) => {
  if (args.item.id === 'Grid_pdfexport') {
    grid.pdfExport();
  }
  if (args.item.id === 'Grid_excelexport') {
    grid.excelExport();
  }
  if (args.item.id === 'Grid_csvexport') {
    grid.csvExport();
  }
}

```

{% endtab %}
