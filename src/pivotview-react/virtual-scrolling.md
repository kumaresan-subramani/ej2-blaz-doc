---
title: "Virtual Scrolling"
component: "Pivot Table"
description: "Virtual Scrolling allows user to load large amount of data without performance degradation."
---

<!-- markdownlint-disable MD036 -->

# Virtual Scrolling

Allows to load the large amounts of data without any performance degradation by rendering rows and columns only in the current content viewport. Rest of the aggregated data will be brought into viewport dynamically based on vertical or horizontal scroll position. This feature can be enabled by setting the [`enableVirtualization`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#enablevirtualization) property to **true**.

To use the virtual scrolling feature, inject the `VirtualScroll` module in to the pivot table.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, VirtualScroll, Inject } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
let date1: number;
let date2: number;
function data(count: number) {
    let result: Object[] = [];
    let dt: number = 0;
    for (let i: number = 1; i < (count + 1); i++) {
        dt++;
        let round: string;
        let toString: string = i.toString();
        if (toString.length === 1) {
            round = '0000' + (i);
        }
        else if (toString.length === 2) {
            round = '000' + i;
        }
        else if (toString.length === 3) {
            round = '00' + i;
        } else if (toString.length === 4) {
            round = '0' + i;
        } else {
            round = toString;
        }
        result.push({
            ProductID: 'PRO-' + round,
            Year: "FY " + (dt + 2013),
            Price: Math.round(Math.random() * 5000) + 5000,
            Sold: Math.round(Math.random() * 80) + 10,
        });
        if (dt / 4 == 1) {
            dt = 0;
        }
    }
    return result;
};
class App extends React.Component<{}, {}>{
      public dataSourceSettings: IDataOptions = {
        dataSource: data(1000),
        enableSorting: false,
        expandAll: true,
        formatSettings: [{ name: 'Price', format: 'C0' }],
        rows: [{ name: 'ProductID' }],
        columns: [{ name: 'Year' }],
        values: [{ name: 'Price', caption: 'Unit Price' }, { name: 'Sold', caption: 'Unit Sold' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} enableVirtualization={true} dataSourceSettings={this.dataSourceSettings}><Inject services={[VirtualScroll]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

> The `height` and `width` properties should be set for virtual scrolling. If it is not defined then the pivot table will consider its value as `300px` and `800px` respectively.

**Limitations for virtual scrolling**

* In virtual scrolling, the [`columnWidth`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#columnwidth) property in [`gridSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#gridsettings) should be in pixel and percentage values are not accepted.
* Resizing columns, setting width to individual columns which affects the calculation used to pick the correct page on scrolling.
* Grouping, which takes additional time to splitting the raw items into the provided format.
* Date Formatting, which takes additional time to convert date format.
* Date Formatting with sorting, here additionally full date time format should be framed to perform sorting along with the provided date format which lags the performance.

## Data Compression

> This property is applicable only for relational data source.

When we bind one million raw data, the pivot table will process all raw data to generate aggregated data during initial rendering and report manipulation. But in data compression, the data will be compressed based on the uniqueness of the raw data, and unique records will be provided as input for the Pivot Table. The compressed data will be used for further operations at all times, reducing the looping complexity and improving the performance of the pivot table. For example, if the pivot table  is connected to one million raw data aggregated to 1,000 unique data means, it will be rendered within 3 seconds rather than 10 seconds. You can enable this option by using the [`allowDataCompression`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#allowdatacompression) property along with [`enableVirtualization`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#enablevirtualization) property.

> This options will only function when the virtual scrolling is enabled.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, VirtualScroll, Inject } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
let date1: number;
let date2: number;
function data(count: number) {
    let result: Object[] = [];
    let dt: number = 0;
    for (let i: number = 1; i < (count + 1); i++) {
        dt++;
        let round: string;
        let toString: string = i.toString();
        if (toString.length === 1) {
            round = '0000' + (i);
        }
        else if (toString.length === 2) {
            round = '000' + i;
        }
        else if (toString.length === 3) {
            round = '00' + i;
        } else if (toString.length === 4) {
            round = '0' + i;
        } else {
            round = toString;
        }
        result.push({
            ProductID: 'PRO-' + (i % 1000),
            Year: "FY " + (dt + 2013),
            Price: Math.round(Math.random() * 5000) + 5000,
            Sold: Math.round(Math.random() * 80) + 10,
        });
        if (dt / 4 == 1) {
            dt = 0;
        }
    }
    return result;
};
class App extends React.Component<{}, {}>{
      public dataSourceSettings: IDataOptions = {
        dataSource: data(1000),
        enableSorting: false,
        expandAll: true,
        formatSettings: [{ name: 'Price', format: 'C0' }],
        rows: [{ name: 'ProductID' }],
        columns: [{ name: 'Year' }],
        values: [{ name: 'Price', caption: 'Unit Price' }, { name: 'Sold', caption: 'Unit Sold' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} enableVirtualization={true} allowDataCompression={true} dataSourceSettings={this.dataSourceSettings}><Inject services={[VirtualScroll]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

**Limitations during data compression**

* The following aggregation types will not be supported.
    * Average
    * Populationstdev
    * Samplestdev
    * Populationvar
    * Samplevar
* If you use any of the aggregations above, it will result in an aggregation type **"Sum"**.
* Distinctcount will act as **"Count"** aggregation type.
* In the calculated field, an existing field can be inserted without altering its default aggregation type Even if we change it, it would use the default aggregation type back for calculation.