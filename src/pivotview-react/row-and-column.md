---
title: "Grid Customization"
component: "Pivot Table"
description: "Miscellaneous aspects of customizing the pivot table."
---

# Row and Column

## Width And Height

Allows end user to set the pivot table's height and width by using [`height`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#height) and [`width`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#width) properties respectively. The supported formats to set [`height`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#height) and [`width`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#width) properties are,

* Pixel: For example - 100, 200, "100px", "200px".
* Percentage: For example - "100%", "200%".
* Auto: It is applicable for [`height`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#height) property alone in-order to render the pivot table beyond its parent container height without vertical scrollbar. The parent container here would show its vertical scrollbar as soon as the component reaches beyond its dimension.

> The pivot table will not be displayed less than **400px**, since it's the minimum width of the component.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} width={'100%'}dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Row Height

Allows end user to set the height of each pivot table rows commonly using the [`rowHeight`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#rowheight) property in [`gridSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#gridsettings).

> By default, the [`rowHeight`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#rowheight) property is set as **36** pixels for desktop layout and **48** pixels for mobile layout.
> The height of the column headers alone may vary when grouping bar feature is enabled.

In the below code sample, the [`rowHeight`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#rowheight) property is set as **60** pixels.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    rowHeight: 60
  } as GridSettings;

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Column Width

Allows end user to set the width of each pivot table columns commonly using the [`columnWidth`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#columnwidth) property in [`gridSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#gridsettings).

> By default, the [`columnWidth`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#columnwidth) property is set as **110** pixels to each columns except the first column. For first column, **250** pixels and **200** pixels are set respectively with and without grouping bar.

In the below example, the [`columnWidth`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#columnwidth) property is set as **200** pixels.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    columnWidth: 120
  } as GridSettings;

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Reorder

Allows end user to reorder a particular column header from one index to another index within the pivot table through drag-and-drop option. It can be enabled by setting the [`allowReordering`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#allowreordering) property in [`gridSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#gridsettings) to **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    allowReordering: true
  } as GridSettings;

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Column Resizing

Allows end user to resize the columns by clicking and dragging the right edge of the column header. While dragging, the width of the respective column will be resized immediately. To enable column resizing option, set the [`allowResizing`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#allowresizing) property in [`gridSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#gridsettings) to **true**.

> By default, the column resizing option is enabled.
> In RTL mode, user can click and drag the left edge of the header cell to resize the column.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    allowResizing: true
  } as GridSettings;

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

> In RTL mode, you can click and drag the left edge of the header cell to resize the column.

## Text Wrap

Allows end user to wrap the cell content to the next line when it exceeds the boundary of the cell width. To enable text wrap, set the [`allowTextWrap`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#allowtextwrap) property in [`gridSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#gridsettings) to **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    allowTextWrap: true
  } as GridSettings;

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Grid Lines

Allows end user to display cell border for each cells using [`gridLines`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#gridlines) property in [`gridSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#gridsettings).

Available mode of grid lines are:

| Modes | Actions |
|-------|---------|
| Both | Displays both the horizontal and vertical grid lines.|
| None | No grid lines are displayed.|
| Horizontal | Displays the horizontal grid lines only.|
| Vertical | Displays the vertical grid lines only.|
| Default | Displays grid lines based on the theme.|

> By default, pivot table renders grid lines in **Both** mode.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    gridLines: 'Vertical'
  } as GridSettings;

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Selection

Selection provides an option to highlight a row or a column or a cell. It can be done through simple mouse down or arrow keys. To enable selection in the pivot table, set the [`allowSelection`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#allowselection) property in [`gridSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#gridsettings) to **true**.

The pivot table supports two types of selection that can be set using [`type`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSelectionSettings/#type) property in [`selectionSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#selectionsettings). The selection types are:

* **Single**: It is set by default, and it only allows selection of a single row or a column or a cell.
* **Multiple**: Allows you to select multiple rows or columns or cells.
To perform multi-selection, press and hold "CTRL" key and click the desired rows or cells. To select range of rows or cells, press and hold the "SHIFT" key and click the rows or columns or cells.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
      allowSelection: true,
      selectionSettings: { type: 'Multiple' }
  } as GridSettings;

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Selection Mode

The pivot table supports four types of selection mode that can be set using [`mode`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSelectionSettings/#mode) in  [`selectionSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#selectionsettings). The selection modes are:

* **Row**: It is set by default, and allows user to select only rows.
* **Column**: Allows user to select only columns.
* **Cell**: Allows user to select only cells.
* **Both**: Allows user to select rows and columns at the same time.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
      allowSelection: true,
      selectionSettings: { mode: 'Both' }
  } as GridSettings;

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Cell Selection Mode

The pivot table supports two types of cell selection mode that can be set using [`cellSelectionMode`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSelectionSettings/#cellselectionmode) in [`selectionSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#selectionsettings). The cell selection modes are:

* **Flow**: It is set by default. The range of cells are selected between the start index and end index that includes in-between cells of rows.
* **Box**: Range of cells are selected from the start and end column indexes that includes in-between cells of rows within the range.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    allowSelection: true,
    selectionSettings: { cellSelectionMode: 'Box', type: 'Multiple', mode: 'Cell' }
  } as GridSettings;

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

> Cell selection requires [`mode`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSelectionSettings/#mode) property in [`selectionSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#selectionsettings) to be **Cell** or **Both**, and [`type`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSelectionSettings/#type) property should be **Multiple**.

### Changing background color of the selected cell

The background-color of the selected cell can be changed using built-in CSS names. To do so, please refer to the code sample below, which shows that the selected cells are changed to a **green yellow** color.

{% tab template="pivot-table/selection-css", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

const SAMPLE_CSS = `
  .e-pivotview .e-cellselectionbackground,
  .e-pivotview .e-selectionbackground,
  .e-pivotview .e-grid .e-rowsheader. e-selectionbackground,
  .e-pivotview .e-grid .e-columnsheader.e-selectionbackground {
    background-color: greenYellow !important;
  }`;
  
class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    allowSelection: true,
    selectionSettings: { cellSelectionMode: 'Box', type: 'Multiple', mode: 'Cell' }
  } as GridSettings;

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
            <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
        </div>
    )
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Event

#### CellSelected

The event [`cellSelected`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#cellselected) is triggered when cell selection gets completed. It provides selected cells information with its corresponding column and row headers. It has following parameters - `selectedCellsInfo`, `currentCell` and `target`. This event allows user to view selected cells information and user can pass those selected cells information to any external component for data binding.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, GridSettings, PivotCellSelectedEventArgs } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public gridSettings: GridSettings = {
    allowSelection: true,
    selectionSettings: { mode: 'Both', type: 'Multiple' }
  } as GridSettings;

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C2', useGrouping: false, minimumSignificantDigits: 1, maximumSignificantDigits: 3 }],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
  }

  onCellSelected(args: PivotCellSelectedEventArgs): void {
    //args.selectedCellsInfo -> get selected cells information.
    //args.pivotValues -> get the pivot values of the pivot table.
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} gridSettings={this.gridSettings} cellSelected={this.onCellSelected}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

#### CellSelecting

The event `cellSelecting` triggers before cell gets selected gets completed. It provides selected cells information with its corresponding column and row headers. It has following parameters - `currentCell`, `data` and `cancel`.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, GridSettings, PivotCellSelectedEventArgs } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public gridSettings: GridSettings = {
    allowSelection: true,
    selectionSettings: { mode: 'Both', type: 'Multiple' }
  } as GridSettings;

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C2', useGrouping: false, minimumSignificantDigits: 1, maximumSignificantDigits: 3 }],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
  }

  onCellSelecting(args: PivotCellSelectedEventArgs): void {
    //args.selectedCellsInfo -> get selected cells information.
    //args.pivotValues -> get the pivot values of the pivot table.
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} gridSettings={this.gridSettings} cellSelecting={this.onCellSelecting}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Clip Mode

The clip mode provides options to display its overflow cell content in the pivot table. It can be configured using the [`clipMode`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#clipmode) property in [`gridSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#gridsettings). The pivot table supports three types of clip modes which are:

* **Clip**: Truncates the cell content when it overflows its area.
* **Ellipsis**: Displays ellipsis when the cell content overflows its area.
* **EllipsisWithTooltip**: Displays ellipsis when the cell content overflows its area, also it will display the tooltip while hover on ellipsis is applied.

> By default, [`clipMode`](https://ej2.syncfusion.com/react/documentation/api/pivotview/gridSettingsModel/#clipmode) value is set to **Ellipsis**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    clipMode: 'Clip'
  } as GridSettings;

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Cell Template

User can customize the pivot table cell element by using the [`cellTemplate`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#celltemplate) property. The [`cellTemplate`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#celltemplate) property accepts either an HTML string or the element's ID, which can be used to append additional HTML elements to showcase each cell with custom format.

In this demo, the revenue cost for each year is represented with trend icons.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { renewableEnergy } from './datasource';

class App extends React.Component<{}, {}>{

private cellTemplate(props): JSX.Element {
    return (<span className="tempwrap e-pivot-trend-neutral pv-icons"></span>);
}

  public dataSourceSettings: IDataOptions = {
    dataSource: renewableEnergy as IDataSet[],
    expandAll: true,
    enableSorting: true,
    drilledMembers: [{ name: 'Year', items: ['FY 2015', 'FY 2017', 'FY 2018'] }],
    formatSettings: [{ name: 'ProCost', format: 'C0' }],
    rows: [
        { name: 'Year', caption: 'Production Year' }
    ],
    columns: [
        { name: 'EnerType', caption: 'Energy Type' },
        { name: 'EneSource', caption: 'Energy Source' }
    ],
    values: [
        { name: 'ProCost', caption: 'Revenue Growth' }
    ],
    filters: []
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} cellTemplate={this.cellTemplate.bind(this)} dataBound={this.trend.bind(this)}></PivotViewComponent>
  }

    trend(): void {
        let cTable: HTMLElement[] = [].slice.call(document.getElementsByClassName("e-table"));
        let colLen: number = this.pivotObj.pivotValues[3].length;
        let cLen: number = cTable[3].children[0].children.length;
        let rLen: number = cTable[3].children[1].children.length;
        let rowIndx: number;

        for (let k: number = 0; k < rLen; k++) {
            if (this.pivotObj.pivotValues[k] && this.pivotObj.pivotValues[k][0] !== undefined) {
                rowIndx = ((this.pivotObj.pivotValues[k][0]) as IAxisSet).rowIndex;
                break;
            }
        }
        let rowHeaders: HTMLElement[] = [].slice.call(cTable[2].children[1].querySelectorAll('td'));
        let rows: IFieldOptions[] = this.pivotObj.dataSourceSettings.rows as IFieldOptions[];
        if (rowHeaders.length > 1) {
            for (let i: number = 0, Cnt = rows; i < Cnt.length; i++) {
                let fields: any = {};
                let fieldHeaders: any = [];
                for (let j: number = 0, Lnt = rowHeaders; j < Lnt.length; j++) {
                    let header: any = rowHeaders[j];
                    if (header.className.indexOf('e-gtot') === -1 && header.className.indexOf('e-rowsheader') > -1 && header.getAttribute('fieldname') === rows[i].name) {
                        var headerName = rowHeaders[j].getAttribute('fieldname') + '_' + rowHeaders[j].textContent;
                        fields[rowHeaders[j].textContent] = j;
                        fieldHeaders.push(rowHeaders[j].textContent);
                    }
                }
                if (i === 0) {
                    for (let rnt: number = 0, Lnt = fieldHeaders; rnt < Lnt.length; rnt++) {
                        if (rnt !== 0) {
                            let row: number = fields[fieldHeaders[rnt]];
                            let prevRow: number = fields[fieldHeaders[rnt - 1]];
                            for (let j: number = 0, ci = 1; j < cLen && ci < colLen; j++ , ci++) {
                                let node: HTMLElement = cTable[3].children[1].children[row].childNodes[j] as HTMLElement;
                                let prevNode: HTMLElement = cTable[3].children[1].children[prevRow].childNodes[j] as HTMLElement;
                                let ri: any = undefined;
                                let prevRi: any = undefined;
                                if (node) {
                                    ri = node.getAttribute("index");
                                }
                                if (prevNode) {
                                    prevRi = prevNode.getAttribute("index");
                                }
                                if (ri && ri < [].slice.call(this.pivotObj.pivotValues).length) {
                                    if ((this.pivotObj.pivotValues[prevRi][ci] as IAxisSet).value > (this.pivotObj.pivotValues[ri][ci]  as IAxisSet).value &&
                                     node.querySelector('.tempwrap')) {
                                        let trendElement: HTMLElement = node.querySelector('.tempwrap');
                                        trendElement.className = trendElement.className.replace('sb-icon-neutral', 'sb-icon-loss');
                                    } else if ((this.pivotObj.pivotValues[prevRi][ci]  as IAxisSet).value < (this.pivotObj.pivotValues[ri][ci]  as IAxisSet).value &&
                                     node.querySelector('.tempwrap')) {
                                        let trendElement: HTMLElement = node.querySelector('.tempwrap');
                                        trendElement.className = trendElement.className.replace('sb-icon-neutral', 'sb-icon-profit');
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Events

### QueryCellInfo

The event `queryCellInfo` triggers while rendering each row and value cells in the pivot table. It allows the user to customize the current cell like adding or removing styles, editing value, etc. It has the following parameters:

* `cell` - It holds the current cell information.
* `data` - It holds the entire row data besides the current cell.
* `column` - It holds the entire column data besides the current cell.
* `pivotview` - It holds pivot table instance.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    columnWidth: 140,
    queryCellInfo: this.queryCellInfo.bind(this)
  } as GridSettings;

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
  queryCellInfo(args: QueryCellInfoEventArgs): void {
    //triggers every time for value cell while rendering
  }
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

### HeaderCellInfo

The event `headerCellInfo` triggers while rendering each column header cell in the pivot table. It allows the user to customize the element of the current header cell like adding or removing styles, editing value, etc. It has the following parameters:

* `node` - It holds the current header cell information

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    columnWidth: 140,
    headerCellInfo: this.headerCellInfo.bind(this)
  } as GridSettings;

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
  headerCellInfo(args: HeaderCellInfoEventArgs): void {
    //triggers every time for header cell while rendering
  }
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

### CellClick

The event [`cellClick`](https://ej2.syncfusion.com/react/documentation/api/pivotview#cellclick) triggers while clicking a cell in the pivot table. For instance, using this event end-user can either add or remove styles, edit value and also perform any other DOM manipulations. It has the following parameters:

* `currentCell` - It holds the current cell information.
* `data` - It holds the clicked cell's data like axis, formatted text, actual text, row header, column header and value informations.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, CellClickEventArgs } from '@syncfusion/ej2-react-pivotview';
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
    formatSettings: [{ name: 'Amount', format: 'C2'}],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
  }
  public pivotObj: PivotViewComponent;

  cellClick(args: CellClickEventArgs): void {
      //triggers for every cell click in pivot table
      args.currentCell.setAttribute("style", "background-color: red;")
  }

  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} cellClick={this.cellClick.bind(this)} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## See Also

* [Show/hide tooltip](./how-to/show-hide-tool-tip)
* [Perform cell selection and get selected cells information](./how-to/perform-cell-selection-and-get-selected-cells-information)