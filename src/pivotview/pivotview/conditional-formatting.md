---
title: "Conditional Formatting"
component: "Pivot Table"
description: "Conditional formatting allowing the users to highlighting the value cells based on its value."
---

# Conditional Formatting

Allows end user to change the appearance of the pivot table value cells with its background color, font color, font family, and font size based on specific conditions.

The conditional formatting can be applied at runtime through the built-in dialog, invoked from the toolbar. To do so, set [`allowConditionalFormatting`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/#allowconditionalformatting) and [`showToolbar`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/#showToolbar) properties in pivot table to **true**. Also, include the item **ConditionalFormatting** in the [`toolbar`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/#toolbar). End user can now see the "Conditional Formatting" icon in toolbar UI automatically, which on clicking will invoke the formatting dialog to perform necessary operations.

To use conditional formatting, you need to inject the `ConditionalFormatting` module in pivot table.

{% tab template="pivot-table/conditional-formatting", es5Template="conditional-toolbar", sourceFiles="index.ts,icode-behindndex.html" %}

```typescript
import { PivotView, ConditionalFormatting, IDataSet } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(ConditionalFormatting);
let pivotTableObj: PivotView = new PivotView({
           dataSourceSettings: {
            dataSource: pivotData,
            expandAll: false,
            enableSorting: true,
            drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
            columns: [{ name: 'Year' }],
            rows: [{ name: 'Country' }, { name: 'Products' }],
            values: [{ name: 'Amount', caption: 'Sold Amount' },
            { name: 'Sold', caption: 'Units Sold' }],
            filters: []
        },
        showToolbar:true,
        toolbar:['ConditionalFormatting'],
        allowConditionalFormatting: true,
        height: 350
});

pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

Conditional formatting can also be included in the pivot table through code-behind using the [`conditionalFormatSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/conditionalFormatSettingsModel/). The required properties to apply a new conditional formatting are,

* [`measure`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/conditionalFormatSettingsModel/#measure): Specifies the value field name for which style will be applied.
* [`conditions`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/conditionalFormatSettingsModel/#conditions): Specifies the operator type such as equals, greater than, less than, etc.
* [`value1`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/conditionalFormatSettingsModel/#value1): Specifies the start value.
* [`value2`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/conditionalFormatSettingsModel/#value2.html): Specifies the end value.
* [`style`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/conditionalFormatSettingsModel/#style): Specifies the style for the cell.

The available style properties in [`style`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/style/), to set in value cells are:

* [`backgroundColor`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/style/#backgroundcolor): Specifies the background color.
* [`color`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/style/#color): Specifies the font color.
* [`fontFamily`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/style/#fontfamily): Specifies the font family.
* [`fontSize`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/style/#fontsize): Specifies the font size.

To use the conditional formatting feature, You need to inject the `ConditionalFormatting` module in pivot table.

{% tab template="pivot-table/pivot-table", es5Template="conditional-formatting", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, ConditionalFormatting, IDataSet } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(ConditionalFormatting);
let pivotTableObj: PivotView = new PivotView({
           dataSourceSettings: {
            dataSource: pivotData,
            expandAll: false,
            enableSorting: true,
            drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
            columns: [{ name: 'Year' }],
            rows: [{ name: 'Country' }, { name: 'Products' }],
            values: [{ name: 'Amount', caption: 'Sold Amount' },
            { name: 'Sold', caption: 'Units Sold' }],
            filters: [],
            conditionalFormatSettings: [
                {
                    measure: 'Amount',
                    value1: 350000,
                    conditions: 'LessThan',
                    style: {
                        backgroundColor: '#80cbc4',
                        color: 'black',
                        fontFamily: 'Tahoma',
                        fontSize: '12px'
                    }
                }
            ]
        },
        allowConditionalFormatting: true,
        height: 350
});

pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

Meanwhile, user can also view conditional formatting dialog in UI by invoking [`showConditionalFormattingDialog`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/#showconditionalformattingdialog) method on an external button click which is shown in the below code sample.

{% tab template="pivot-table/conditional-formatting", es5Template="conditional-formatting", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, ConditionalFormatting, IDataSet } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(ConditionalFormatting);
let pivotTableObj: PivotView = new PivotView({
           dataSourceSettings: {
            dataSource: pivotData,
            expandAll: false,
            enableSorting: true,
            drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
            columns: [{ name: 'Year' }],
            rows: [{ name: 'Country' }, { name: 'Products' }],
            values: [{ name: 'Amount', caption: 'Sold Amount' },
            { name: 'Sold', caption: 'Units Sold' }],
            filters: [],
            conditionalFormatSettings: [
                {
                    measure: 'Amount',
                    value1: 350000,
                    conditions: 'LessThan',
                    style: {
                        backgroundColor: '#80cbc4',
                        color: 'black',
                        fontFamily: 'Tahoma',
                        fontSize: '12px'
                    }
                }
            ]
        },
        allowConditionalFormatting: true,
        height: 320
});

pivotTableObj.appendTo('#PivotTable');

let btn: Button = new Button({ isPrimary: true });
btn.appendTo('#Formatting');

document.getElementById('Formatting').addEventListener('click', () => {
    pivotTableObj.conditionalFormattingModule.showConditionalFormattingDialog();
});

```

{% endtab %}

## Conditional formatting for all fields

Allows end user to apply conditional formatting commonly for all value fields just by ignoring the [`Measure`](https://help.syncfusion.com/cr/blazor/Syncfusion.EJ2.Blazor~Syncfusion.EJ2.Blazor.PivotView.PivotViewConditionalFormatSetting~Measure.html) property and setting rest of the properties in [`PivotViewConditionalFormatSetting`](https://help.syncfusion.com/cr/blazor/Syncfusion.EJ2.Blazor~Syncfusion.EJ2.Blazor.PivotView.PivotViewConditionalFormatSetting_properties.html).

{% tab template="pivot-table/conditional-formatting", es5Template="conditional-fields", sourceFiles="index.ts,code-behind.html" %}

```typescript
import { PivotView, ConditionalFormatting, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(ConditionalFormatting);
let pivotTableObj: PivotView = new PivotView({
           dataSourceSettings: {
            dataSource: pivotData,
            expandAll: false,
            enableSorting: true,
            drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
            columns: [{ name: 'Year' }],
            rows: [{ name: 'Country' }, { name: 'Products' }],
            values: [{ name: 'Amount', caption: 'Sold Amount' },
            { name: 'Sold', caption: 'Units Sold' }],
            filters: [],
            conditionalFormatSettings: [
                {
                    value1: 500,
                    conditions: 'GreaterThan',
                    style: {
                        backgroundColor: '#80cbc4',
                        color: 'black',
                        fontFamily: 'Tahoma',
                        fontSize: '12px'
                    }
                }
            ]
        },
        allowConditionalFormatting: true,
        height: 320
});

pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## See Also

* [Apply conditional formatting for specific row or column](./how-to/apply-conditional-formatting-for-specific-row-or-column)