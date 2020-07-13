---
title: "Switching to older themes style"
component: "Pivot Table"
description: "This section allows the user to switch the older theme"
---

<!-- markdownlint-disable MD009 -->

# Switching to older themes style

From Volume 1, 2020 onwards Syncfusion has revised the theming and layout of the Pivot Table. So, to inherit the older theme style and layout please do the necessary changes in CSS and pivot table height.

## CSS Selectors

In current theme, the cells can be differentiated by their background colors. To avoid it, you need to override its background colors via simple CSS coding within your application. The below CSS selectors allow to achieve the same for material, fabric, bootstrap and bootstrap v4 themes.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>       
       <!-- Codes here... -->
            <style>
                .e-pivotview .e-rowsheader, 
                .e-pivotview .e-columnsheader,
                .e-pivotview .e-gtot,
                .e-pivotview .e-content,
                .e-pivotview .e-gridheader,
                .e-pivotview .e-headercell {
                    background-color:#fff !important;
                }
            </style>
       </head>
       <body>
       </body>
  </html>

```

Meanwhile for high contrast theme, we need to set the following CSS.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>       
       <!-- Codes here... -->
            <style>
                .e-pivotview .e-rowsheader, 
                .e-pivotview .e-columnsheader,
                .e-pivotview .e-gtot,
                .e-pivotview .e-content,
                .e-pivotview .e-gridheader,
                .e-pivotview .e-headercell {
                    background-color:#000 !important;
                }
            </style>
       </head>
       <body>
       </body>
  </html>

```

## Adjusting Row Height

In current theme, to make the component compact we have reduced the height of each pivot table rows. But user can reset the height of the pivot table using the [`rowHeight`](https://ej2.syncfusion.com/documentation/api/pivotview/gridSettings/#rowheight) property in [`gridSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/gridSettings/). In older theme, the property was set to 36 pixels for desktop layout and 48 pixels for mobile layout. So reset the [`rowHeight`](https://ej2.syncfusion.com/documentation/api/pivotview/gridSettings/#rowheight) accordingly to visualize the older theme style.

In the below code sample, we replicate the older theme style.

{% tab template="pivot-table/theme-switch", es5Template="theme-switch", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    height: 350,
    gridSettings: {
        rowHeight: 36
    }
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}
