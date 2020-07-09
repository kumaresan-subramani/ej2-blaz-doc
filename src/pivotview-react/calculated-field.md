---
title: "Calculated Field"
component: "Pivot Table"
description: "Calculated field allows the user to add a new field (user-defined) dynamically based on a simple mathematical formula."
---

# Calculated Field

Allows end user to create a new calculated field in the pivot table, based on available fields from the bound data source or using simple formula with basic arithmetic operators. It can be added at runtime through the built-in dialog, invoked from Field List UI. To do so, set the [`allowCalculatedField`](https://ej2.syncfusion.com/react/documentation/api/pivotview#allowcalculatedfield) property to **true** in the pivot table. End user can now see a "CALCULATED FIELD" button enabled in Field List UI automatically, which on clicking will invoke the calculated field dialog and perform necessary operation.

Calculated field can also be included in the pivot table through code behind using the [`calculatedFieldsSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#calculatedfieldsettings). The required properties to create a new calculate field are:
* [`name`](https://ej2.syncfusion.com/react/documentation/api/pivotview/calculatedFieldSettingsModel/#name): It allows to indicate the calculated field with a unique name.
* [`formula`](https://ej2.syncfusion.com/react/documentation/api/pivotview/calculatedFieldSettingsModel/#formula): It allows to set the formula.
* [`formatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettings/): It helps to set the number format for the resultant value.

To use calculated field option, you need to inject the `CalculatedField` module in pivot table.

> The calculated field is applicable only for value fields. Also, calculated field created through code behind will be automatically listed in the UI dialog as well.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { CalculatedField, FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }, { name: 'Total', format: 'C2' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }, { name: 'Total', caption: 'Total Units', type: 'CalculatedField' }],
    calculatedFieldSettings: [{ name: 'Total', formula: '"Sum(Amount)"+"Sum(Sold)"' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true} showFieldList={true}><Inject services={[CalculatedField, FieldList]}/> </PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

Meanwhile, user can also view calculated field dialog in UI by invoking [`createCalculatedFieldDialog`](https://ej2.syncfusion.com/react/documentation/api/pivotview#createcalculatedfielddialog) method on an external button click which is shown in the below code sample.

> To use calculated field option, you need to inject the `CalculatedField` module in pivot table.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { CalculatedField, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }, { name: 'Total', format: 'C2' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }, { name: 'Total', caption: 'Total Units', type: 'CalculatedField' }],
    calculatedFieldSettings: [{ name: 'Total', formula: '"Sum(Amount)"+"Sum(Sold)"' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true}><Inject services={[CalculatedField]}/> </PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Calculated Field</ButtonComponent></div></div>
  }

  btnClick(): void {
    this.pivotObj.calculatedFieldModule.createCalculatedFieldDialog();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Editing through the field list and the grouping bar

User can also modify the existing calculated field using the built-in edit option available directly in the field list (or) grouping bar. To do so, click the "Edit" icon available in the calculated field button. Now the calculated field dialog is opened and the current calculated field name, formula and format can be changed at runtime.

![output](images/edit-button.png "Editing the calculated field")
<br/>
<br/>
![output](images/after-edit-button.png "Editing the calculated field formula")

## Renaming the existing calculated field

Existing calculated field can be renamed only through the UI at runtime. To do so, open the calculated field dialog, select the target field and click "Edit" icon. User can now see the existing name getting displayed in the text box at the top of the dialog. Now, change the name based on user requirement and click "OK".

<!-- markdownlint-disable MD012 -->
![output](images/before-edit.png "Editing the calculated field")
<br/>
<br/>
![output](images/after-edit.png "Renaming the calculated field")

## Editing the existing calculated field formula

Existing calculated field formula can be edited only through the UI at runtime. To do so, open the calculated field dialog, select the target field and click "Edit" icon. User can now see the existing formula getting displayed in a multiline text box at the bottom of the dialog. Now, change the formula based on user requirement and click "OK".

![output](images/before-edit.png "Editing the calculated field")
<br/>
<br/>
![output](images/after-change.png "Editing the calculated field formula")

## Reusing the existing formula in a new calculate field

While creating a new calculated field, if user wants to the add the formula of an existing calculated field, it can be done easily. To do so, simply drag-and-drop the existing calculated field to the "Formula" section.

![output](images/before-drag.png "Dragging the existing calculated field")
<br/>
<br/>
![output](images/while-drag.png "Drag field to formula")
<br/>
<br/>
![output](images/after-drag.png "Reusing the existing calculated field formula")

## Apply the format to the calculated field values

The values in the new or existing calculated field can be formatted through its UI and also through code behind. To format the calculated field values at runtime, the built-in textbox is available under the "Format" label where the user can set the desired format. Likewise, in code-behind, you can set the desired format using the [`formatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettings/) property as illustrated in the introduction section. For more information about the supported formats [`refer here`](https://ej2.syncfusion.com/react/documentation/pivotview/number-formatting/).

![output](images/calculatedfield-format.png "Applying format through calculated field dialog UI")

## Supported operators and functions for the calculated field formula

Below is a list of operators and functions that can be used in the formula to create the calculated fields.

* `+` – addition operator.

```typescript
 Syntax: X + Y
```

* `-` – subtraction operator.

```typescript
Syntax: X - Y
```

* `*` – multiplication operator.

```typescript
Syntax: X * Y
```

* `/` – division operator.

```typescript
Syntax: X / Y
```

* `^` – power operator.

```typescript
Syntax: X^2
```

* `<` - less than operator.

```typescript
Syntax: X < Y
```

* `<=` – less than or equal operator.

```typescript
Syntax: X <= Y
```

* `>` – greater than operator.

```typescript
Syntax: X > Y
```

* `>=` – greater than or equal operator.

```typescript
Syntax: X >= Y
```

* `==` – equal operator.

```typescript
Syntax: X == Y
```

* `!=` – not equal operator.

```typescript
Syntax: X != Y
```

* `|` – OR operator.

```typescript
Syntax: X | Y
```

* `&` – AND operator.

```typescript
Syntax: X & Y
```

* `?` – conditional operator.

```typescript
Syntax: condition ? then : else
```

* `isNaN` – function that checks if the value is not a number.

```typescript
Syntax: isNaN(value)
```

* `!isNaN` – function that checks if the value is a number.

```typescript
Syntax: isNaN(value)
```

* `abs` – function that returns the absolute value of a number.

```typescript
Syntax: abs(number)
```

* `min` – function that returns the minimum value.

```typescript
Syntax: min(number1, number2)
```

* `max` – function that returns the maximum value.

```typescript
Syntax: max(number1, number2)
```

 > Also, you can use JavaScript [Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math) object properties and methods directly to the formula.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { CalculatedField, FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }, { name: 'Total', caption: 'Total Units', type: 'CalculatedField' }],
    calculatedFieldSettings: [{ name: 'Total', formula: 'Math.round("Sum(Amount)") > abs("Sum(Sold)") ? min("Sum(Amount)", "Sum(Sold)") : Math.sqrt("Sum(Sold)")' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true} showFieldList={true}><Inject services={[CalculatedField, FieldList]}/> </PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Event

### CalculatedFieldCreate

The event [`calculatedFieldCreate`](https://ej2.syncfusion.com/react/documentation/api/pivotview#calculatedfieldcreate) fires while closing the dialog on "OK" button click. It allows to customize the new or existing calculated field information obtained from the dialog. It has the following parameters  

* `calculatedField`: It holds the new or existing calculated field information obtained from dialog.

* [`calculatedFieldSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#calculatedfieldsettings): It holds the [`calculatedFieldSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#calculatedfieldsettings) property of the pivot report.

* `cancel`: It is a boolean property and by setting this to true , the customization done in calculated field dialog won’t be applied to calculated field.

In the below sample, creating a calculated field without setting the format is restricted.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { CalculatedField, FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent, CalculatedFieldCreateEventArgs } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }, { name: 'Total', caption: 'Total Units', type: 'CalculatedField' }],
    calculatedFieldSettings: [{ name: 'Total', formula: 'Math.round("Sum(Amount)") > abs("Sum(Sold)") ? min("Sum(Amount)", "Sum(Sold)") : Math.sqrt("Sum(Sold)")' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true} showFieldList={true} calculatedFieldCreate={this.calculatedFieldCreate.bind(this)}><Inject services={[CalculatedField, FieldList]}/> </PivotViewComponent>
  }
  calculatedFieldCreate(args: CalculatedFieldCreateEventArgs) {
        if(args.calculatedField.formatString === '') {
            args.cancel = true;
        }
    }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}