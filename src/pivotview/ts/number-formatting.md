---
title: "Number Formatting"
component: "Pivot Table"
description: "Number Formatting allows user to formatting numeric values in pivot table."
---

# Number Formatting

Allows you to specify the required display format that should be used in values of the pivot table. Supported display formats are:

* Number
* Currency
* Percentage
* Custom

You can apply format for the numeric values using the following properties in the [`formatSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#formatsettings).

* [`name`](https://ej2.syncfusion.com/documentation/api/pivotview/formatSettingsModel/#name): It allows to specify the field name.
* [`format`](https://ej2.syncfusion.com/documentation/api/pivotview/formatSettingsModel/#format): It allows to specify the format of the respective field.

Possible formatting values are:

1. N - denotes numeric type.
2. C - denotes currency type.
3. P - denotes percentage type.

> If no format is specified it takes number as default format type.

Other properties include:

* [`useGrouping`](https://ej2.syncfusion.com/documentation/api/pivotview/formatSettingsModel/#usegrouping): It allows to enable or disable the separator, for example, $100,000,000 or $100000000 respectively. By default, it will be set as **true**.
* [`currency`](https://ej2.syncfusion.com/documentation/api/pivotview/formatSettingsModel/#currency): It allows to set the currency code which needs to considered for the currency formatting.

{% tab template="pivot-table/pivot-table", es5Template="number-format-code", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        formatSettings: [{ name: 'Amount', format: 'C2', useGrouping: false, currency: 'EUR' }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    gridSettings: {
        columnWidth: 140
    },
    height: 450
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

You can also format the values at runtime using the formatting dialog. This option can be enabled by setting the [`allowNumberFormatting`](https://ej2.syncfusion.com/documentation/api/pivotview/#allownumberformatting) property to **true**. The same has been discussed in some of the upcoming topics.

> To use the formatting dialog, inject the `NumberFormatting` module into the pivot table.

## Custom format

You can add any custom format directly to the [`format`](https://ej2.syncfusion.com/documentation/api/pivotview/formatSettingsModel/#format) property in the [`formatSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#formatsettings). Custom format can be achieved by using one or more format specifiers listed in the below table.

| Specifier | Description | Input | Format Output |
| ------- |--------------- | ---------------- | --------------- |
| 0 | Replaces the zero with the corresponding digit if it is present. Otherwise, zero will appear in the result string. | { format: '0000' } | '0123' |
| # | Replaces the ' # ' symbol with the corresponding digit if it is present. Otherwise, no digits will appear in the result string.| { format: '####' } | '1234' |
| . | Denotes the number of digits permitted after the decimal point. | { format: '###0.##0#' } | '546321.000' |
| % | Percent specifier denotes the percentage type format. | { format: '0000 %' } | '0100 %' |
| $ | Denotes the currency type format that is based on the global currency code specified. | { format: '$ ###.00' } | '$ 13.00' |
| ; | Denotes separate formats for positive, negative and zero values. | { format: '###.##;(###.00);-0' } | '(120.00)'    |
| 'String' (single Quotes) | Denotes the characters that are enclosed in the single quote (') to be replaced in the resulting string. | { format: "####.00 '@'" } | "123.00 @"    |

>NOTE: If custom format is defined, certain properties such as [`useGrouping`](https://ej2.syncfusion.com/documentation/api/pivotview/formatSettingsModel/#usegrouping) and [`currency`](https://ej2.syncfusion.com/documentation/api/pivotview/formatSettingsModel/#currency) will not be considered.

{% tab template="pivot-table/pivot-table", es5Template="number-format-custom", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        formatSettings: [{ name: 'Sold', format: "####.00 'Nos'" }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    gridSettings: {
        columnWidth: 140
    },
    height: 450
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Toolbar

You can enable formatting dialog option in the toolbar by adding `NumberFormatting` in the [`toolbar`](../../api/pivotview/#toolbar). After that, you can see the option to invoke the formatting dialog in the toolbar.

{% tab template="pivot-table/pivot-table", es5Template="number-format-toolbar", sourceFiles="index.ts,index.html" %}

```typescript
import { pivotData } from './datasource.ts';
import {
    PivotView, FieldList, CalculatedField, Toolbar, RemoveReportArgs, NumberFormatting,
    ConditionalFormatting, IDataSet, RenameReportArgs, SaveReportArgs, FetchReportArgs, LoadReportArgs
} from '@syncfusion/ej2-pivotview';

PivotView.Inject(FieldList, CalculatedField, Toolbar, ConditionalFormatting, NumberFormatting);

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        formatSettings: [{ name: 'Amount', format: 'C2', useGrouping: false, currency: 'EUR' }],
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 450,
    toolbar: ['Grid', 'Chart', 'Export', 'SubTotal', 'GrandTotal', 'NumberFormatting', 'FieldList'],
    allowExcelExport: true,
    allowNumberFormatting: true,
    allowConditionalFormatting: true,
    allowPdfExport: true,
    showToolbar: true,
    allowCalculatedField: true,
    displayOption:{ view:'Both' },
    showFieldList: true,
    gridSettings: { columnWidth: 140 }
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Invoking formatting dialog through external button

You can invoke the formatting dialog by clicking an external button using the `ShowNumberFormattingDialog` method.

{% tab template="pivot-table/number-formatting", es5Template="number-formatting", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, NumberFormatting, FieldList, IDataSet } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(NumberFormatting, FieldList);
let pivotTableObj: PivotView = new PivotView({
           dataSourceSettings: {
            dataSource: pivotData,
            expandAll: false,
            enableSorting: true,
            formatSettings: [{ name: 'Amount', format: 'C2', useGrouping: false, currency: 'EUR' }],
            drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
            columns: [{ name: 'Year' }],
            rows: [{ name: 'Country' }, { name: 'Products' }],
            values: [{ name: 'Amount', caption: 'Sold Amount' },
            { name: 'Sold', caption: 'Units Sold' }],
            filters: []
        },
        showFieldList: true,
        allowNumberFormatting: true,
        height: 420
});

pivotTableObj.appendTo('#PivotTable');

let btn: Button = new Button({ isPrimary: true });
btn.appendTo('#Formatting');

document.getElementById('Formatting').addEventListener('click', () => {
    pivotTableObj.numberFormattingModule.showNumberFormattingDialog();
});

```

{% endtab %}

## Events

### NumberFormatting

The event [`numberFormatting`](https://ej2.syncfusion.com/documentation/api/pivotview#numberformatting) fires while closing the number formatting dialog on "OK" button click. It allows the user to restrict the customization settings done by the user. It has the following parameters

* `formatName`: It holds the name of the field.

* [`formatSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#formatsettings): It holds the [`formatSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#formatsettings) property of the pivot report.

* `cancel`: It is a boolean property and by setting this to true , the customization done in number formatting dialog won’t be applied.

In the below sample, the customization done in number formatting dialog for the field "Amount" won’t be applied.

{% tab template="pivot-table/number-formatting", es5Template="numberFormatting-event", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, NumberFormatting, FieldList, IDataSet } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(NumberFormatting, FieldList);
let pivotTableObj: PivotView = new PivotView({
           dataSourceSettings: {
            dataSource: pivotData,
            expandAll: false,
            enableSorting: true,
            formatSettings: [{ name: 'Amount', format: 'C2', useGrouping: false, currency: 'EUR' }],
            drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
            columns: [{ name: 'Year' }],
            rows: [{ name: 'Country' }, { name: 'Products' }],
            values: [{ name: 'Amount', caption: 'Sold Amount' },
            { name: 'Sold', caption: 'Units Sold' }],
            filters: []
        },
        showFieldList: true,
        allowNumberFormatting: true,
        height: 420,
        numberFormatting: function (args: NumberFormattingEventArgs) {
        if(args.formatName === 'Amount') {
            args.cancel = true;
        }
    },
});

pivotTableObj.appendTo('#PivotTable');

let btn: Button = new Button({ isPrimary: true });
btn.appendTo('#Formatting');

document.getElementById('Formatting').addEventListener('click', () => {
    pivotTableObj.numberFormattingModule.showNumberFormattingDialog();
});

```

{% endtab %}

## See Also

* [Customize number, date, and time values](./how-to/customize-number-date-and-time-values)
* [NumberFormatOptions](https://ej2.syncfusion.com/documentation/common/intl.html?lang=typescript#manipulating-numbers)
* [Toolbar](./tool-bar)