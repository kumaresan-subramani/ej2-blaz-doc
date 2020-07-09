---
title: "Globalization"
component: "Pivot Table"
description: "Learn about how to globalize the pivot table and how to localize the culture related content."
---

# Globalization

Globalization is the combination of Internationalization and localization. You can adapt the component to various languages by parsing and formatting the date or number ([`Internationalization`](https://ej2.syncfusion.com/react/documentation/base/internationalization.html)) & adding culture specific customization and translation to the text ([`Localization`](https://ej2.syncfusion.com/react/documentation/base/localization.html)).

## Load CLDR-Data to the application

* Open command prompt in your machine.

* Run the following command in command prompt.

```cmd
cd /d 'Folder path of your react application'

For example: cd /d  E:\react\WebApplication
```

* Make sure that you have installed `Node and NPM` in your machine before installing the `CLDR-Data`.

* To check if you have `Node`, run this command in command prompt.

```cmd
node -v
```

* If `Node` is not installed, then you can download and install the `Node` from this [location](https://nodejs.org/en/).

* To confirm if you have `NPM`, run this command in command prompt.

```cmd
npm -v
```

* Now, install the `CLDR-Data` package by using the following command (it installs the CLDR JSON data). To
learn more about CLDR-Data, refer to
[CLDR-Data](http://cldr.unicode.org/index/cldr-spec/json).

```cmd
npm install cldr-data --save
```

* After installing the package, you can find the culture specific JSON data under the location `\node_modules\cldr-data`. Then, copy the `cldr-data` folder into your react application.

* Download the required locale packages to render the react Pivot Table component with specified locale. To download the locale definition of react components, use this [link](https://github.com/syncfusion/ej2-locale).

* After downloading the ej2-locale package, copy the ej2-locale folder with required local definition file into your react application. By default, the ej2-locale package contains the localized text for static text present in components like grid, chart, pivot table, tools, and more.

The locale JSON file will look like:

![output](images/locale.png)

## Internationalization

The Internationalization library is used to globalize number, date, and time values in pivot table component using the `dataSourceSettings.formatSettings` option. In the below code sample, we set the culture and currency using the `load`, `setCulture` and `setCurrencyCode` methods. By default, pivot table component is displayed in english culture.

* Set the culture by using the `locale` property.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent, GroupingBar, CalculatedField } from '@syncfusion/ej2-react-pivotview';
import { L10n, setCulture, setCurrencyCode } from '@syncfusion/ej2-base';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

setCulture('de');
setCurrencyCode('EUR');

L10n.load({
    'de-DE': {
        'pivotview': {
            'grandTotal': 'Gesamtsumme',
            'total': 'Insgesamt',
            'value': 'Wert',
            'noValue': 'Kein Wert',
            'row': 'Zeile',
            'column': 'Spalte',
            'collapse': 'Zusammenbruch',
            'expand': 'Erweitern'
        },
        "pivotfieldlist": {
            'fieldList': 'Feld Liste',
            'dropRowPrompt': 'Drop Reihe hier',
            'dropColPrompt': 'Drop column Hier',
            'dropValPrompt': 'Drop wert hier',
            'dropFilterPrompt': 'Drop Filter Hier',
            'addPrompt': 'Feld hinzufügen',
            'centerHeader': 'Ziehen Sie die Felder zwischen den Bereichen unten:',
            'add': 'Hinzufügen',
            'drag': 'Ziehen',
            'filters': 'Filter',
            'rows': 'Zeilen',
            'columns': 'Spalten',
            'values': 'Werte',
            'error': 'Fehler',
            'dropAction': 'Berechnetes Feld nicht in jeder anderen Region außer Wert Achse sein.',
            'search': 'Suche',
            'close': 'Schließen',
            'cancel': 'Abbrechen',
            'delete': 'Löschen',
            'alert': 'Warnung',
            'warning': 'Warnung',
            'ok': 'OK',
            'allFields': 'Alle Felder',
            'noMatches': 'Keine Treffer'
        }
    }
});
class App extends React.Component<{}, {}>{
  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C2', useGrouping: false,
                minimumSignificantDigits: 1, maximumSignificantDigits: 3, currency: 'EUR' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} locale='de-DE' dataSourceSettings={this.dataSourceSettings} showFieldList={true} showGroupingBar={true} allowCalculatedField={true}><Inject services={[FieldList, GroupingBar, CalculatedField]} /></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

> * In the above sample, `Amount` field is formatted by [`NumberFormatOptions`](https://ej2.syncfusion.com/react/documentation/base/internationalization.html#number-formatter-and-parser). For date formats, the value strings are formatted by [`DateFormatOptions`](https://ej2.syncfusion.com/react/documentation/base/internationalization.html#date-formatter-and-parser).
> * By default, `locale` value is `en-US`. If you want to change the `en-US` culture to a different culture, you have to change  the `locale` accordingly.
> * Also, you will find more details about support format string for number formats and data formats [`here`](https://ej2.syncfusion.com/documentation/common/intl.html?lang=typescript#supported-format-string).

<!-- markdownlint-disable MD009 -->

### Decimal separators 

The decimal separators of pivot table values varies based on the culture applied to the component. The culture can be set by calling the method [`setCulture`](https://ej2.syncfusion.com/react/documentation/common/localization/#changing-current-locale) with appropriate culture string as its parameter.

The following example demonstrates the decimal separators in `Deutsch` culture.

{% tab template="pivot-table/locale", sourceFiles="app/index.tsx",compileJsx=true %}

```typescript
import { FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent, GroupingBar, CalculatedField } from '@syncfusion/ej2-react-pivotview';
import { loadCldr, L10n, setCulture, setCurrencyCode, Ajax } from '@syncfusion/ej2-base';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import * as currencies from './currencies.json';
import * as cagregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';
import * as numberingSystems from './numberingSystems.json';

loadCldr(currencies, cagregorian, numbers, timeZoneNames, numberingSystems);
setCulture('de');
setCurrencyCode('EUR');

L10n.load({
    'de-DE': {
        'pivotview': {
            'grandTotal': 'Gesamtsumme',
            'total': 'Insgesamt',
            'value': 'Wert',
            'noValue': 'Kein Wert',
            'row': 'Zeile',
            'column': 'Spalte',
            'collapse': 'Zusammenbruch',
            'expand': 'Erweitern'
        },
        "pivotfieldlist": {
            'fieldList': 'Feld Liste',
            'dropRowPrompt': 'Drop Reihe hier',
            'dropColPrompt': 'Drop column Hier',
            'dropValPrompt': 'Drop wert hier',
            'dropFilterPrompt': 'Drop Filter Hier',
            'addPrompt': 'Feld hinzufügen',
            'centerHeader': 'Ziehen Sie die Felder zwischen den Bereichen unten:',
            'add': 'Hinzufügen',
            'drag': 'Ziehen',
            'filters': 'Filter',
            'rows': 'Zeilen',
            'columns': 'Spalten',
            'values': 'Werte',
            'error': 'Fehler',
            'dropAction': 'Berechnetes Feld nicht in jeder anderen Region außer Wert Achse sein.',
            'search': 'Suche',
            'close': 'Schließen',
            'cancel': 'Abbrechen',
            'delete': 'Löschen',
            'alert': 'Warnung',
            'warning': 'Warnung',
            'ok': 'OK',
            'allFields': 'Alle Felder',
            'noMatches': 'Keine Treffer'
        }
    }
});
class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    formatSettings: [{ name: 'Amount', format: 'C2', currency: 'EUR' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} locale='de-DE' dataSourceSettings={this.dataSourceSettings} showFieldList={true} showGroupingBar={true} allowCalculatedField={true}><Inject services={[FieldList, GroupingBar, CalculatedField]} /></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Localization

The [`Localization`](https://ej2.syncfusion.com/documentation/common/api-l10n.html) library allows you to localize default text content of the pivot table. The pivot table component has static text on some features (like drop area text, pivot field list title, etc...) that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
`locale` value and translation object.

The following list of properties and its values are used in the pivot table.

Locale keywords |Text
-----|-----
grandTotal | Grand Total
total | Total
value | Value
noValue | No value
row | Row
column | Column
collapse | Collapse
expand | Expand
rowAxisPrompt | Drop row here
columnAxisPrompt | Drop column here
valueAxisPrompt | Drop value here
filterAxisPrompt | Drop filter here
filter | Filter
filtered | Filtered
sort | Sort
filters | Filters
rows | Rows
columns | Columns
values | Values
close | Close
cancel | Cancel
delete | Delete
calculatedField | Calculated Field
createCalculatedField | Create Calculated Field
fieldName | Enter the field name
error | Error
invalidFormula | Invalid formula.
dropText | Example: ("Sum(Order_Count)" + "Sum(In_Stock)") * 250
dropTextMobile | Add fields and edit formula here.
dropAction | Calculated field cannot be place in any other region except value axis.
alert | Alert
warning | Warning
ok | OK
search | Search
drag | Drag
remove | Remove
sum | Sum
average | Average
count | Count
min | Min
max | Max
allFields | All Fields
formula | Formula
addToRow | Add to Row
addToColumn | Add to Column
addToValue | Add to Value
addToFilter | Add to Filter
emptyData | No records to display
fieldExist | A field already exists in this name. Please enter a different name.
confirmText | A calculation field already exists in this name. Do you want to replace it?
noMatches | No matches
format | Summaries values by
edit | Edit
clear | Clear
formulaField | Drag and drop fields to formula
dragField | Drag field to formula

The following list of properties and its values are used in the pivot field list.

Locale keywords |Text
-----|-----
staticFieldList | Pivot Field List
fieldList | Field List
dropFilterPrompt | Drop filter here
dropColPrompt | Drop column here
dropRowPrompt | Drop row here
dropValPrompt | Drop value here
addPrompt | Add field here
adaptiveFieldHeader | Choose field
centerHeader | Drag fields between axes below:
add | add
drag | Drag
filter | Filter
filtered | Filtered
sort | Sort
remove | Remove
filters | Filters
rows | Rows
columns | Columns
values | Values
calculatedField | Calculated Field
createCalculatedField | Create Calculated Field
fieldName | Enter the field name
error | Error
invalidFormula | Invalid formula.
dropText | Example: ("Sum(Order_Count)" + "Sum(In_Stock)") * 250
dropTextMobile | Add fields and edit formula here.
dropAction | Calculated field cannot be place in any other region except value axis.
search | Search
close | Close
cancel | Cancel
delete | Delete
alert | Alert
warning | Warning
ok | OK
sum | Sum
average | Average
count | Count
min | Min
max | Max
allFields | All Fields
formula | Formula
fieldExist | A field already exists in this name. Please enter a different name.
confirmText | A calculation field already exists in this name. Do you want to replace it?
noMatches | No matches
format | Summaries values by
edit | Edit
clear | Clear
formulaField | Drag and drop fields to formula
dragField | Drag field to formula

### Loading Translations

To load translation object in an application, use [`load`](https://ej2.syncfusion.com/documentation/common/api-l10n.html#load) function of the [`L10n`](https://ej2.syncfusion.com/documentation/common/api-l10n.html) class.

The following example demonstrates the pivot table in `Deutsch` culture.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent, GroupingBar, CalculatedField } from '@syncfusion/ej2-react-pivotview';
import { L10n } from '@syncfusion/ej2-base';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

L10n.load({
    'de-DE': {
        'pivotview': {
            'grandTotal': 'Gesamtsumme',
            'total': 'Insgesamt',
            'value': 'Wert',
            'noValue': 'Kein Wert',
            'row': 'Zeile',
            'column': 'Spalte',
            'collapse': 'Zusammenbruch',
            'expand': 'Erweitern'
        },
        "pivotfieldlist": {
            'fieldList': 'Feld Liste',
            'dropRowPrompt': 'Drop Reihe hier',
            'dropColPrompt': 'Drop column Hier',
            'dropValPrompt': 'Drop wert hier',
            'dropFilterPrompt': 'Drop Filter Hier',
            'addPrompt': 'Feld hinzufügen',
            'centerHeader': 'Ziehen Sie die Felder zwischen den Bereichen unten:',
            'add': 'Hinzufügen',
            'drag': 'Ziehen',
            'filters': 'Filter',
            'rows': 'Zeilen',
            'columns': 'Spalten',
            'values': 'Werte',
            'error': 'Fehler',
            'dropAction': 'Berechnetes Feld nicht in jeder anderen Region außer Wert Achse sein.',
            'search': 'Suche',
            'close': 'Schließen',
            'cancel': 'Abbrechen',
            'delete': 'Löschen',
            'alert': 'Warnung',
            'warning': 'Warnung',
            'ok': 'OK',
            'allFields': 'Alle Felder',
            'noMatches': 'Keine Treffer'
        }
    }
});
class App extends React.Component<{}, {}>{
  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} locale='de-DE' dataSourceSettings={this.dataSourceSettings} showFieldList={true} showGroupingBar={true} allowCalculatedField={true}><Inject services={[FieldList, GroupingBar, CalculatedField]} /></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Right-to-left (RTL)

Right-to-left (RTL) provides an option to switch the text direction and layout of the pivot table component from right to left. It improves the user experiences and accessibility for users who use right-to-left languages (Arabic, Farsi, Urdu, etc...). To enable RTL pivot table, set the `enableRtl` property to **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent, GroupingBar, CalculatedField } from '@syncfusion/ej2-react-pivotview';
import { L10n } from '@syncfusion/ej2-base';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

L10n.load({
  'ar-AE': {
      'pivotview': {
          'grandTotal': 'المجموع الكلى',
          'total': 'المجموع',
          'value': 'القيمة',
          'noValue': 'لا قيمة لها',
          'row': 'صف',
          'column': 'العمود',
          'collapse': 'الانهيار',
          'expand': 'توسيع'
      },
      'pivotfieldlist': {
          'fieldList': 'قائمة الحقول',
          'dropRowPrompt': 'تراجع الخلاف هنا',
          'dropColPrompt': 'انخفاض العمود هنا',
          'dropValPrompt': 'انخفاض قيمة هنا',
          'dropFilterPrompt': 'انخفاض هنا عامل التصفية',
          'addPrompt': 'اضافة حقل هنا',
          'adaptiveFieldHeader': 'اختر الحقل',
          'centerHeader': 'اسحب المجالات بين المناطق الموضحة ادناه:',
          'add': 'اضافة',
          'drag': 'اسحب',
          'filters': 'عوامل التصفية',
          'rows': 'الصفوف',
          'columns': 'الاعمدة',
          'values': 'قيم',
          'search': 'البحث',
          'close': 'قريب',
          'cancel': 'الغاء',
          'delete': 'احذف',
          'alert': 'حالة تاهب قصوى',
          'warning': 'تحذير',
          'ok': 'موافق',
          'allFields': 'جميع الحقول',
          'noMatches': 'لا مباريات'
      }
  }
});
class App extends React.Component<{}, {}>{
  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} enableRtl={true} locale='ar-AE' dataSourceSettings={this.dataSourceSettings} showFieldList={true} showGroupingBar={true} allowCalculatedField={true}><Inject services={[FieldList, GroupingBar, CalculatedField]} /></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## See Also

* [Internationalization](https://ej2.syncfusion.com/react/documentation/base/internationalization.html)
* [Localization](https://ej2.syncfusion.com/react/documentation/base/localization.html)