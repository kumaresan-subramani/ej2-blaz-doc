---
title: "Defer Layout Update"
component: "Pivot Table"
description: "Defer update allows users to update the pivot table only on demand."
---

# Defer Layout Update

Defer layout update support allows to update the pivot table component only on demand. On enabling this feature, end user can drag-and-drop fields between row, column, value and filter axes, apply sorting and filtering inside the Field List, resulting in change of pivot report alone but not the pivot table values. Once all operations are performed and on clicking the "Apply" button in the Field List, pivot table will start to update with the last modified report. This also helps in bringing better performance in pivot table component rendering.

The field list can be displayed in two different formats to interact with pivot table. They are:

* **In-built Field List (Popup)**: To display the field list icon in pivot table UI to invoke the built-in dialog.
* **Stand-alone Field List (Fixed)**: To display the field list in a static position within a web page.

## In-built Field List (Popup)

To enable deferred updates in the pivot table, set the property [`allowDeferLayoutUpdate`](https://ej2.syncfusion.com/react/documentation/api/pivotview#allowdeferlayoutupdate) as **true** in [`PivotView`](https://ej2.syncfusion.com/react/documentation/api/pivotview). To make a note, the defer update option can be controlled only via Field List during runtime.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    allowLabelFilter: true,
    allowValueFilter: true,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showFieldList={true} allowDeferLayoutUpdate={true}><Inject services={[FieldList]} /></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Stand-alone Field List (Fixed)

The field list can be rendered in a static position, anywhere in web page layout, like a separate component. To do so, you need to set [`renderMode`](https://ej2.syncfusion.com/react/documentation/api/pivotfieldlist/pivotFieldListModel/#rendermode) property to **Fixed** in PivotFieldList.

To enable deferred updates in the static fieldlist, set the property [`allowDeferLayoutUpdate`](https://ej2.syncfusion.com/react/documentation/api/pivotfieldlist/pivotFieldListModel/#allowdeferlayoutupdate) in [`PivotFieldlist`](https://ej2.syncfusion.com/react/documentation/api/pivotfieldlist) as **true**. To make a note, the defer update option can be controlled only via Field List during runtime.

> To make field list interact with pivot table, you need to use the **UpdateView** and **Update** methods for data source update in both field list and pivot table simultaneously.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { CalculatedField, PivotFieldListComponent, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

const SAMPLE_CSS = `
.e-pivotview {
    width: 58%;
    height: 100%;
    float: left;
}
.e-pivotfieldlist {
    width: 42%;
    height: 100%;
    float: right;
}
.e-pivotfieldlist .e-static {
    width: 100% !important;
}`;

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
  public fieldlistObj: PivotFieldListComponent;
  render() {
    return <div className="control-section">
    <style>{SAMPLE_CSS}</style>
    <PivotViewComponent id='PivotViewFieldList' ref={d => this.pivotObj = d!} enginePopulated={this.afterPivotPopulate.bind(this)} allowDeferLayoutUpdate={true} width={'99%'} height={'530'} gridSettings={{columnWidth: 140}}></PivotViewComponent>
    <PivotFieldListComponent id='PivotFieldList' ref={d => this.fieldlistObj = d!} enginePopulated={this.afterPopulate.bind(this)} dataSourceSettings={this.dataSourceSettings} renderMode={"Fixed"} allowDeferLayoutUpdate={true} allowCalculatedField={true}><Inject services={[CalculatedField]} /></PivotFieldListComponent></div>
  }

  afterPopulate(): void {
    if (this.fieldlistObj.isRequiredUpdate) {
            this.fieldlistObj.updateView(this.pivotObj);
      }
      this.pivotObj.notify('ui-update', this.pivotObj);
      this.fieldlistObj.notify('tree-view-update', this.fieldlistObj);
  }
  afterPivotPopulate(): void {
      if (this.fieldlistObj && this.pivotObj) {
          this.fieldlistObj.update(this.pivotObj);
      }
  }
  rendereComplete(): void {
      this.fieldlistObj.updateView(this.pivotObj);
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}