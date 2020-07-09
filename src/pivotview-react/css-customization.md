---
title: "CSS Customization "
component: "Pivot Table"
description: "CSS Customization for Pivot Table."
---

# CSS Customization

## Hiding Axis

The visibility of row, column, value and filter axis in Field List and Grouping Bar can be changed using custom CSS setting. To do so, please refer the code sample below:

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { CalculatedField, FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent, GroupingBar } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

const SAMPLE_CSS = `
/* Hiding column axis in grouping bar */
    #PivotView .e-group-columns {
        display: none;
    }
    /* Increasing filter axis height to fill column axis portion */
    #PivotView .e-group-filters {
        min-height: 74.67px !important;
    }

    /* Hiding column axis in field list */
    .e-pivotfieldlist-wrapper .e-field-list-columns {
        display: none;
    }
    /* Increasing value axis height to fill column axis portion */
    .e-pivotfieldlist-wrapper .e-field-list-values {
        margin-top: 0px !important;
        min-height: 338px !important;
    }
    .e-pivotfieldlist-wrapper .e-values {
        height: 310px !important;
    }

    /* Hiding row axis in grouping bar */
    // #PivotView .e-group-rows {
    //     display: none;
    // }

    /* Hiding row axis in field list */
    // .e-pivotfieldlist-wrapper .e-field-list-rows {
    //     display: none;
    // }

    /* Hiding value axis in grouping bar */
    // #PivotView .e-group-values {
    //     display: none;
    // }

    /* Hiding value axis in field list */
    // .e-pivotfieldlist-wrapper .e-field-list-values {
    //     display: none;
    // }

    /* Hiding filter axis in grouping bar */
    // #PivotView .e-group-filters {
    //     display: none;
    // }

    /* Hiding filter axis in field list */
    //.e-pivotfieldlist-wrapper .e-field-list-filters {
    //    display: none;
    //}`;


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
  }
  public pivotObj: PivotViewComponent;
  render() {
    return (
        <div>
            <style>{SAMPLE_CSS}</style>
            <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true} showFieldList={true} showGroupingBar={true}><Inject services={[CalculatedField, FieldList, GroupingBar]}/> </PivotViewComponent>
        </div>
    )
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Text Alignment

The alignment of text inside row headers, column headers, value cells and summary cells can be changed using custom CSS setting. To do so, please refer the code sample below:

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { CalculatedField, FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent, GroupingBar } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

const SAMPLE_CSS = `
//Value Cells
    .e-pivotview .e-valuescontent {
         text-align: center !important;
    }

    //Columns Headers
    /*.e-pivotview .e-columnsheader {
         text-align: center !important;
    }

    //Rows Headers
    .e-pivotview .e-rowsheader {
         text-align: center !important;
    }*/

    //Summary Cells
    /* .e-pivotview .e-summary {
         text-align: center !important;
    }*/`;


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
  }
  public pivotObj: PivotViewComponent;
  render() {
    return (
        <div>
            <style>{SAMPLE_CSS}</style>
            <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true} showFieldList={true} showGroupingBar={true}><Inject services={[CalculatedField, FieldList, GroupingBar]}/> </PivotViewComponent>
        </div>
    )
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Customize header, value and summary cell style

The elements in pivot table like header cell, value cell and summary cell style can be customized using built-in CSS names. To do so, please refer the code sample below:

{% tab template="pivot-table/background-css", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { CalculatedField, FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent, GroupingBar } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

const SAMPLE_CSS = `
  //Value Cells
    .e-pivotview .e-summary:not(.e-gtot) {
         background-color: pink !important;
    }

    //Columns Headers
    /*.e-pivotview .e-headercell {
      background-color: thistle !important;
    }

    //Rows Headers
    .e-pivotview .e-rowsheader {
      background-color: skyblue !important;
    }*/

    //Summary Cells
    /* .e-pivotview .e-gtot  {
    background-color: greenYellow !important;
  }*/`;

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return (
        <div>
            <style>{SAMPLE_CSS}</style>
            <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true} showFieldList={true} showGroupingBar={true}><Inject services={[CalculatedField, FieldList, GroupingBar]}/> </PivotViewComponent>
        </div>
    )
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}