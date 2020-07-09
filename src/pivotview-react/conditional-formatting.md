---
title: "Conditional Formatting"
component: "Pivot Table"
description: "Conditional formatting allowing the users to highlighting the value cells based on its value."
---

# Conditional Formatting

Allows end user to change the appearance of the pivot table value cells with its background color, font color, font family, and font size based on specific conditions.

The conditional formatting can be applied at runtime through the built-in dialog, invoked from the toolbar. To do so, set [`allowConditionalFormatting`](https://ej2.syncfusion.com/react/documentation/api/pivotview#allowconditionalformatting) and [`showToolbar`](https://ej2.syncfusion.com/react/documentation/api/pivotview#showtoolbar) properties to **true**. Also, include the item **ConditionalFormatting** within the [`toolbar`](https://ej2.syncfusion.com/react/documentation/api/pivotview#toolbar) property. End user can now see the "Conditional Formatting" icon in toolbar UI automatically, which on clicking will invoke the formatting dialog to perform necessary operations.

> To use the conditional formatting feature, You need to inject the `ConditionalFormatting` module in pivot table.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import {
    PivotViewComponent, IDataOptions, Inject, Toolbar, ConditionalFormatting
} from '@syncfusion/ej2-react-pivotview';
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
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  };
  public pivotObj: PivotViewComponent;
   public toolbarOptions: any = ['ConditionalFormatting'];

  render() {
    return <PivotViewComponent id='PivotView' ref={(scope) => { this.pivotObj = scope; }} dataSourceSettings={this.dataSourceSettings} width={'100%'} height={350} gridSettings={{ columnWidth: 140 }} allowConditionalFormatting={true} showToolbar={true} toolbar={this.toolbarOptions}><Inject services={[Toolbar, ConditionalFormatting]} /></PivotViewComponent>
  }
};
ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

Conditional formatting can also be included in the pivot table through code-behind using the [`conditionalFormatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#conditionalformatsettings). The required properties to apply a new conditional formatting are,

* [`measure`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalFormatSettings/#measure): Specifies the value field name for which style will be applied.
* [`conditions`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalFormatSettings/#conditions): Specifies the operator type such as equals, greater than, less than, etc.
* [`value1`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalFormatSettings/#value1): Specifies the start value.
* [`value2`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalFormatSettings/#value2): Specifies the end value.
* [`style`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalFormatSettings/#style): Specifies the style for the cell.

The available style properties in [`style`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalFormatSettings/#style), to set in value cells are:

* [`backgroundColor`](https://ej2.syncfusion.com/react/documentation/api/pivotview/style/#backgroundcolor): Specifies the background color.
* [`color`](https://ej2.syncfusion.com/react/documentation/api/pivotview/style/#color): Specifies the font color.
* [`fontFamily`](https://ej2.syncfusion.com/react/documentation/api/pivotview/style/#fontfamily): Specifies the font family.
* [`fontSize`](https://ej2.syncfusion.com/react/documentation/api/pivotview/style/#fontsize): Specifies the font size.

Meanwhile, user can also view conditional formatting dialog in UI by invoking [`showConditionalFormattingDialog`](https://ej2.syncfusion.com/react/documentation/api/pivotview#showconditionalformattingdialog) method on an external button click which is shown in the below code sample.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { ConditionalFormatting, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
        columns: [{ name: 'Year' }, { name: 'Order_Source', caption: 'Order Source' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        values: [{ name: 'In_Stock', caption: 'In Stock' },
        { name: 'Sold', caption: 'Units Sold' }],
        filters: [{ name: 'Product_Categories', caption: 'Product Categories' }],
        conditionalFormatSettings: [
            {
                measure: 'In_Stock',
                value1: 5000,
                conditions: 'LessThan',
                style: {
                    backgroundColor: '#80cbc4',
                    color: 'black',
                    fontFamily: 'Tahoma',
                    fontSize: '12px'
                }
            },
            {
                value1: 3400,
                value2: 40000,
                measure: 'Sold',
                conditions: 'Between',
                style: {
                    backgroundColor: '#f48fb1',
                    color: 'black',
                    fontFamily: 'Tahoma',
                    fontSize: '12px'
                }
            }
        ]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Apply Formatting</ButtonComponent></div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowConditionalFormatting={true}><Inject services={[ConditionalFormatting]}/> </PivotViewComponent></div>
    </div>
  }
    btnClick(): void {
    this.pivotObj.conditionalFormattingModule.showConditionalFormattingDialog();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Conditional formatting for all fields

Allows end user to apply conditional formatting commonly for all value fields just by ignoring the [`measure`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalFormatSettings/#measure) property and setting rest of the properties in [`conditionalFormatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#conditionalformatsettings).

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ConditionalFormatting, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
        columns: [{ name: 'Year' }, { name: 'Order_Source', caption: 'Order Source' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        values: [{ name: 'In_Stock', caption: 'In Stock' },
        { name: 'Sold', caption: 'Units Sold' }],
        filters: [{ name: 'Product_Categories', caption: 'Product Categories' }],
        conditionalFormatSettings: [
            {
                value1: 5000,
                conditions: 'LessThan',
                style: {
                    backgroundColor: '#80cbc4',
                    color: 'black',
                    fontFamily: 'Tahoma',
                    fontSize: '12px'
                }
            },
            {
                value1: 3400,
                value2: 40000,
                conditions: 'Between',
                style: {
                    backgroundColor: '#f48fb1',
                    color: 'black',
                    fontFamily: 'Tahoma',
                    fontSize: '12px'
                }
            }
        ]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowConditionalFormatting={true}><Inject services={[ConditionalFormatting]}/> </PivotViewComponent></div>
    </div>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Conditional formatting for specific value field

Allows end user to apply conditional formatting to a specific value field by setting the [`measure`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalFormatSettings/#measure) property with specific value field name in [`conditionalFormatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#conditionalformatsettings).

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { ConditionalFormatting, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
        columns: [{ name: 'Year' }, { name: 'Order_Source', caption: 'Order Source' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        values: [{ name: 'In_Stock', caption: 'In Stock' },
        { name: 'Sold', caption: 'Units Sold' }],
        filters: [{ name: 'Product_Categories', caption: 'Product Categories' }],
        conditionalFormatSettings: [
            {
                measure: 'In_Stock',
                value1: 5000,
                conditions: 'LessThan',
                style: {
                    backgroundColor: '#80cbc4',
                    color: 'black',
                    fontFamily: 'Tahoma',
                    fontSize: '12px'
                }
            },
            {
                value1: 3400,
                value2: 40000,
                measure: 'Sold',
                conditions: 'Between',
                style: {
                    backgroundColor: '#f48fb1',
                    color: 'black',
                    fontFamily: 'Tahoma',
                    fontSize: '12px'
                }
            }
        ]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowConditionalFormatting={true}><Inject services={[ConditionalFormatting]}/> </PivotViewComponent></div>
    </div>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Editing and removing existing conditional format

Editing and removing existing conditional format can be done through the UI at runtime. To do so, open the conditional formatting dialog and edit the "Value", "Condition" and "Format" options based on user requirement and click "OK". To remove a conditional format, click the "Delete" icon besides the respective condition.  

![output](images/cformatting_remove.png)

## Event

### ConditionalFormatting

The event [`conditionalFormatting`](https://ej2.syncfusion.com/react/documentation/api/pivotview#conditionalformatting) is triggered initially while clicking the “ADD CONDITION” button inside the conditional formatting dialog in-order to fill user specific condition instead of default condition at runtime. To use this event, [`allowConditionalFormatting`](https://ej2.syncfusion.com/react/documentation/api/pivotview#allowconditionalformatting) property in PivotView must be set to **true**. It has following parameters -

* `applyGrandTotals` - boolean property, by setting this to true user can enable formatting to grand totals.
* `conditions` - condition to be filled in conditional formatting dialog.
* `label` - Label value for conditional formatting dialog.
* `measure` - measure value for the conditional formatting dialog.
* `style` - style property of the conditional formatting dialog.
* `value1` - value 1 for conditional formatting dialog.
* `value2` - value 2 for conditional formatting dialog, this is applicable only for selected conditions like **Between** and **NotBetween**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { ConditionalFormatting, IDataOptions, IDataSet, Inject, PivotViewComponent, IConditionalFormatSettings } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
        columns: [{ name: 'Year' }, { name: 'Order_Source', caption: 'Order Source' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        values: [{ name: 'In_Stock', caption: 'In Stock' },
        { name: 'Sold', caption: 'Units Sold' }],
        filters: [{ name: 'Product_Categories', caption: 'Product Categories' }],
        conditionalFormatSettings: [
            {
                measure: 'In_Stock',
                value1: 5000,
                conditions: 'LessThan',
                style: {
                    backgroundColor: '#80cbc4',
                    color: 'black',
                    fontFamily: 'Tahoma',
                    fontSize: '12px'
                }
            }
        ]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Apply Formatting</ButtonComponent></div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowConditionalFormatting={true} conditionalFormatting={this.conditionalFormatting.bind(this)}><Inject services={[ConditionalFormatting]}/> </PivotViewComponent></div>
    </div>
  }
    btnClick(): void {
    this.pivotObj.conditionalFormattingModule.showConditionalFormattingDialog();
  }
  conditionalFormatting(args: IConditionalFormatSettings): void {
      args.skipFormatting = true;
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## See Also

* [Apply conditional formatting for specific row or column](./how-to/apply-conditional-formatting-for-specific-row-or-column)