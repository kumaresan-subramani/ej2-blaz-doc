---
title: "Getting Started"
component: "Pivot Table"
description: "Getting started section briefly explains on how to create and add a pivot table in an application."
---

# Getting started

This section explain steps to create a simple **Pivot Table** with OLAP data source in React environment.

## Dependencies

The following list of dependencies are required to use the pivot table component in your application.

```javascript
|-- @syncfusion/ej2-react-pivotview
    |-- @syncfusion/ej2-pivotview
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-excel-export
        |-- @syncfusion/ej2-file-utils
        |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-pdf-export
        |-- @syncfusion/ej2-file-utils
        |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-calendars
    |-- @syncfusion/ej2-charts
        |-- @syncfusion/ej2-svg-base
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-dropdowns
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-grids
|-- @syncfusion/ej2-react-base
```

## Setup for Local Development

You can use [create-react-app](https://github.com/facebookincubator/create-react-app) to setup the application. To install **create-react-app** run the following command.

```sh
npm install -g create-react-app
```

To create basic **React** application use following commands.

<div class='tsx'>

```sh
create-react-app quickstart --scripts-version=react-scripts-ts
```

Now, the application is created in the **quickstart** demo folder. Run the following command one-by-one to navigate to the **quickstart** demo folder, and install the required **npm** dependent packages.

```sh
cd quickstart

npm install
```

</div>

<div class='jsx'>

```sh
create-react-app quickstart
```

Now, the application is cloned in the **quickstart** demo folder. Run the following command one-by-one to navigate to the **quickstart** demo folder, and install the required **npm** dependent packages.

```sh
cd quickstart

npm install
```

</div>

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [npmjs.com](https://www.npmjs.com/~syncfusionorg) public registry. To install pivot table component, use the following command.

```sh
npm install @syncfusion/ej2-react-pivotview --save
```

> The **--save** will instruct NPM to include the pivot table package inside the `dependencies` section of the `package.json`.

## Adding CSS reference

Add pivot table and its [dependent](#dependencies) components styles as given below in **src/App.css** file. In this illustration, we have referred **material** theme.

```css
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-grids/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-calendars/styles/material.css';
@import '../node_modules/@syncfusion/ej2-react-pivotview/styles/material.css';
```

> You can also refer other themes like bootstrap, fabric, high-contrast etc. To know about individual component CSS, please refer [here](../../appearance/theme).

Next we need to refer **App.css** in the application by importing it in the **src/App.tsx** file as follows.

```typescript
import './App.css';
```

## Browser compatibility

Polyfills are required to use the Pivot Table in Internet Explorer 11 browser. Refer the [documentation](https://ej2.syncfusion.com/react/documentation/browser/?no-cache=1#browser-support) for more details.

## Adding pivot table component

You can initialize pivot table component in the application using following steps.

* Import the **PivotViewComponent** (aka, PivotTable) component from the **@syncfusion/ej2-react-pivotview** package in **app.ts** file.
* Then you can initialize pivot table component using `<PivotViewComponent/>` in **render()** method.

```typescript
import { IDataOptions, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import './App.css';

class App extends React.Component<{}, {}>{
  public render() {
    return <PivotViewComponent/>
  };
};

export default App;

```

After initialization, add the the following code in **src/App.tsx** file to populate pivot table with a sample relational data source. Refer [here](./data-binding) to know the more details about relational data binding.

{% tab compileJsx=true%}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';

let pivotData = [
  { 'Sold': 31, 'Amount': 52824, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q1' },
  { 'Sold': 51, 'Amount': 86904, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q2' },
  { 'Sold': 90, 'Amount': 153360, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q3' },
  { 'Sold': 25, 'Amount': 42600, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q4' },
  { 'Sold': 27, 'Amount': 46008, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2016', 'Quarter': 'Q1' }];

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

export default App;

```

{% endtab %}

## Adding fields to row, column, value and filter axes

Now that pivot table is initialized and assigned with sample data, will further move to showcase the component by organizing appropriate fields in row, column, value and filter axes.

In [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/), four major axes -  [`rows`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#rows), [`columns`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#columns), [`values`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#values) and [`filters`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#filters) plays a vital role in defining and organizing fields from the bound data source, to render the entire pivot table component in a desired format.

[`rows`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#rows) – Collection of fields that needs to be displayed in row axis of the pivot table.

[`columns`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#columns) – Collection of fields that needs to be displayed in column axis of the pivot table.

[`values`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#values) – Collection of fields that needs to be displayed as aggregated numeric values in the pivot table.

[`filters`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#filters) - Collection of fields that would act as master filter over the data bound in row, column and value axes of the pivot table.

In-order to define each field in the respective axis, the following basic properties should be set.

* [`name`](https://ej2.syncfusion.com/react/documentation/api/pivotview/fieldOptionsModel/#name): It allows to set the field name from the bound data source. It’s casing should match exactly like in the data source and if not set properly, the pivot table will not be rendered.
* [`caption`](https://ej2.syncfusion.com/react/documentation/api/pivotview/fieldOptions/#caption): It allows to set the field caption, which is the alias name of the field that needs to be displayed in the pivot table.
* [`type`](https://ej2.syncfusion.com/react/documentation/api/pivotview/fieldOptionsModel/#type): It allows to set the summary type of the field. By default, **Sum** is applied.

In this illustration, "Year" and "Quarter" are added in column, "Country" and "Products" in row, and "Sold" and "Amount" in value section respectively.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
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
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}>
    </PivotViewComponent>
  }
};
ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Applying formatting to a value field

Formatting defines a way in which values should be displayed. For example, format **"C"** denotes the values should be displayed in currency pattern. To do so, define the [`formatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettings/) with its [`name`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettings/#name) and [`format`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettings/#format) properties and add it to [`formatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettings/#formatsettings). In this illustration, the [`name`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettings/#name) property is set as **Amount**, a field from value section and its format is set as currency. Likewise, we can set format for other value fields as well and add it to [`formatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettings/#formatsettings).

> Only fields from value section, which is in the form of numeric data values are applicable for formatting.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
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
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}>
    </PivotViewComponent>
  }
};
ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Module Injection

To create pivot table with additional features, inject the required modules. The modules that are available with basic functionality are as follows.

* `GroupingBar` - Inject this module to access grouping bar.
* `FieldList` - Inject this module to access pivot field list.
* `CalculatedField` - Inject this module to access calculated field.

These modules should be injected into the PivotView using the `Inject` method within the `app.tsx` file as shown below. On doing so, only the injected views will be loaded and displayed along with pivot table.

```typescript
<Inject services={[GroupingBar]} />
```

## Enable Field List

The field list allows to add or remove fields and also rearrange the fields between different axes, including column, row, value, and filter along with filter and sort options dynamically at runtime. It can be enabled by setting the [`showFieldList`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotViewModel/?no-cache=1#showfieldlist) property to **true** and by injecting the **FieldList** module as follows. To know more about field list, [`refer`](./field-list) here.

> If the **FieldList** module is not injected, the Field List will not be rendered with the pivot table component.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
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
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showFieldList={true}><Inject services={[FieldList]} />
    </PivotViewComponent>
  }
};
ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Enable Grouping Bar

The grouping bar feature automatically populates fields from the bound data source and allows end users to drag fields between different axes such as columns, rows, values, and filters, and alter pivot table at runtime. It also provides option to sort, filter and remove fields. It can be enabled by setting the [`showGroupingBar`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotViewModel/?no-cache=1#showgroupingbar) property to **true** and by injecting the **GroupingBar** module as follows. To know more about grouping bar, [`refer`](./grouping-bar) here.

> If the **GroupingBar** module is not injected, the grouping bar will not be rendered with the pivot table component.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { IDataOptions, IDataSet, Inject, PivotViewComponent, GroupingBar } from '@syncfusion/ej2-react-pivotview';
import { pivotData } from './datasource';
class App extends React.Component<{}, {}>{
  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  };
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showGroupingBar={true}><Inject services={[GroupingBar]} />
    </PivotViewComponent>
  }
};
ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Exploring Filter Axis

The filter axis contains collection of fields that would act as master filter over the data bound in [`rows`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#rows), [`columns`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#columns) and [`values`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#values) axes of the pivot table. The fields along with filter members could be set to filter axis either through report via code behind or by dragging and dropping fields from other axes to filter axis via grouping bar or field list at runtime.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { CalculatedField, FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import { pivotData } from './datasource';
class App extends React.Component<{}, {}>{
  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [{ name: 'Quarter' }],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  };
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true} showFieldList={true}><Inject services={[CalculatedField, FieldList]}/>
    </PivotViewComponent>
  }
};
ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Calculated Field

The calculated field feature allows user to insert or add a new calculated field based on the available fields from the bound data source using basic arithmetic operators. The calculated field can be included in pivot table using the [`CalculatedFieldSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/calculatedFieldSettings/)  from code behind. Or else, calculated fields can be added at run time through the built-in dialog by just setting the [`allowCalculatedField`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotViewModel/?no-cache=1#allowcalculatedfield) property to **true** and by injecting the **CalculatedField** module as follows in pivot table. You will see a button enabled in the Field List UI automatically to invoke the calculated field dialog and perform necessary operation. To know more about calculated field, [`refer`](./calculated-field) here.

> If the **CalculatedField** module is not injected, the calculated field dialog will not be rendered with the pivot table component. Moreover calculated measure can be added only in value axis.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { CalculatedField, FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
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
    calculatedFieldSettings: [{ name: 'Total', formula: '"Sum(Amount)"+"Sum(Sold)"' }]
  };
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true} showFieldList={true}><Inject services={[CalculatedField, FieldList]}/>
    </PivotViewComponent>
  }
};
ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Run the application

The quickstart project is configured to compile and run the application in the browser. Use the following command to run the application.

```sh
npm start
```

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { CalculatedField, FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
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
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true} showFieldList={true}><Inject services={[CalculatedField, FieldList]}/>
    </PivotViewComponent>
  }
};
ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}