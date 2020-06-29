---
title: "Selection"
component: "Gantt"
description: "Learn how to select the rows and custmize selection action in the Essential JS 2 Gantt component."
---

# Selection

Selection provides an option to highlight a row or a cell. It can be done using arrow keys or by scrolling down the mouse. To disable selection in the Gantt component, set the [`allowSelection`](../api/gantt/#allowselection) to `false`.

To select data, inject the [`Selection`](../api/gantt/#selectionmodule) module into the Gantt control.

The Gantt component supports two types of selection that can be set by using the [`selectionSettings.type`](../api/gantt/selectionSettings/#type) property. They are:

* `Single`: Sets a single value by default and allows only selection of a single row or a cell.
* `Multiple`: Allows you to select multiple rows or cells. To perform the multi-selection, press and hold the CTRL key and click the desired rows or cells.

## Selection mode

The Gantt component supports three types of selection modes that can be set by using the [`selectionSettings.mode`](../api/gantt/selectionSettings/#mode). They are:

* `Row`: Allows you to select only rows, and the row value is set by default.
* `Cell`: Allows you to select only cells.
* `Both`: Allows you to select rows and cells at the same time.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Selection, SelectionSettingsModel } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  public settings: SelectionSettingsModel = {
        mode: 'Both'
  };
    render() {
        return <GanttComponent dataSource={data} allowSelection={true} taskFields={this.taskFields}  selectionSettings={this.settings} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Row selection

The row selection in the Gantt component can be enabled or disabled using the [`allowSelection`](../api/gantt/#allowselection) property. You can get the selected row object using the [`getSelectedRecords`](../api/gantt/selection/#getselectedrecords) method. The following code example shows how to disable the row selection in Gantt.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Selection } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
    render() {
        return <GanttComponent dataSource={data} allowSelection={false} taskFields={this.taskFields}  height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> `Row` selection is the default type of Gantt selection mode.

### Selecting a row on initial load

You can select a row at the time of loading by setting the index of the row to the [`selectedRowIndex`](../api/gantt/#selectedrowindex) property. Find the following code example for details.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Selection } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
    render() {
        return <GanttComponent dataSource={data} selectedRowIndex={3} allowSelection={true} taskFields={this.taskFields} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Selecting a row dynamically

You can also select a row dynamically using the [`selectRow`](../api/gantt/selection/#selectrow) method. The following code demonstrates how to select a row dynamically by clicking the custom button.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent, Inject, Selection } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    dependency: 'Predecessor',
    child: 'subtasks',
  };
  private ganttInstance:any;
  public clickHandler(){
     this.ganttInstance.selectionModule.selectRow(2); // passing the record index to select the row
}
    render() {
        return (<div>
        <ButtonComponent onClick= { this.clickHandler.bind(this)}>Select Row</ButtonComponent>
        <GanttComponent dataSource={data} allowSelection={true}  ref={gantt => this.ganttInstance = gantt}  taskFields={this.taskFields} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Multiple row selection

You can select multiple rows by setting the [`selectionSettings.type`](../api/gantt/selectionSettings/#type) property to `multiple`. You can select more than one row by holding down the CTRL key while selecting multiple rows. The following code example explains how to enable multiple selection in Gantt.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Selection, SelectionSettingsModel } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  public settings: SelectionSettingsModel = {
        mode: 'Row',
        type: 'Multiple'
  };
    render() {
        return <GanttComponent dataSource={data} allowSelection={true} taskFields={this.taskFields}
        selectionSettings={this.settings} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Selecting multiple rows dynamically

You can also select rows dynamically using the [`selectRows`](../api/gantt/selection/#selectrows) method. The following code demonstrates how to select rows dynamically by clicking the custom button.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent, Inject, Selection, SelectionSettingsModel } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  private ganttInstance:any;
  public settings: SelectionSettingsModel = {
        mode: 'Row',
        type: 'Multiple'
  };
  public clickHandler(){
    this.ganttInstance.selectionModule.selectRows([1, 2, 3]); // passing the record index as array collection
}
    render() {
        return (<div>
        <ButtonComponent  onClick= { this.clickHandler.bind(this)}>Select Multiple Rows</ButtonComponent>
        <GanttComponent dataSource={data} ref={gantt => this.ganttInstance = gantt}  allowSelection={true} taskFields={this.taskFields}
        selectionSettings={this.settings} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Customize row selection action

While selecting a row in Gantt, the [`rowSelecting`](../api/gantt/#rowselecting) and [`rowSelected`](../api/gantt/#rowselected) events will be triggered. The the [`rowSelecting`](../api/gantt/#rowselecting) event will be triggered on initialization of row selection, and you can get the previously selected row and current selecting row’s information, which is used to prevent selection of a particular row. The [`rowSelected`](../api/gantt/#rowselected) event will be triggered on completion of row selection action, and you can get the current selected row’s information through this event. The following code example demonstrates how to prevent the selection of a row using the [`rowSelecting`](../api/gantt/#rowselecting) event.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Selection, SelectionSettingsModel } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  public settings: SelectionSettingsModel = {
        mode: 'Row'
  };
  public rowSelecting(args: any) {
        if (args.data.TaskID == 4) {
            args.cancel = true;
        }
    }
    render() {
        return <GanttComponent dataSource={data} allowSelection={true} taskFields={this.taskFields}
        selectionSettings={this.settings} rowSelecting={this.rowSelecting.bind(this)} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

In the Gantt component, when you click an already selected row, selection will be cleared. While deselecting a row in Gantt, the [`rowDeselecting`](../api/gantt/#rowdeselecting) and [`rowDeselected`](../api/gantt/#rowselected) events will occur. The [`rowDeselecting`](../api/gantt/#rowdeselecting) event will occur on initialization of deselecting row, and you can get the current deselecting row’s information to prevent the deselection of particular row. The [`rowDeselected`](../api/gantt/#rowselected) event will occur on completion of row deselection action, and you can get the current deselected row’s information.

## Cell selection

You can select a cell in the Gantt component by setting the [`selectionSettings.mode`](../api/gantt/selectionSettings/#mode) property to cell. You can get the selected cell information using the [`getSelectedRowCellIndexes`](../api/gantt/selection/#getselectedrowcellindexes) method. This method returns the result as an object collection, which has `cellIndexes` and `rowIndex` information of the selected cells.

Find the code example below to enable the cell selection in Gantt.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Selection, SelectionSettingsModel } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  public settings: SelectionSettingsModel = {
        mode: 'Cell'
  };
    render() {
        return <GanttComponent dataSource={data} allowSelection={true} taskFields={this.taskFields}
        selectionSettings={this.settings} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Selecting multiple cells

You can select multiple cells by setting the [`selectionSettings.type`](../api/gantt/selectionSettings/#type) property to multiple and the [`selectionSettings.mode`](../api/gantt/selectionSettings/#mode) property to cell. Multiple cells can be selected by holding the CTRL key and selecting the cells. The following code example demonstrates how to select multiple cells.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Selection, SelectionSettingsModel } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  public settings: SelectionSettingsModel = {
        mode: 'Cell',
        type: 'Multiple'
  };
    render() {
        return <GanttComponent dataSource={data} allowSelection={true} taskFields={this.taskFields}
        selectionSettings={this.settings} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Selecting a cell dynamically

You can select a cell dynamically using the [`selectCell`](../api/gantt/selection/#selectcell) method. Refer to the following code example for details.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent, Inject, Selection, SelectionSettingsModel } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  public settings: SelectionSettingsModel = {
        mode: 'Cell'
  };
  private ganttInstance:any;
  public clickHandler(){
    this.ganttInstance.selectionModule.selectCell({ cellIndex: 1, rowIndex: 1 });
}
    render() {
        return (<div>
        <ButtonComponent onClick= { this.clickHandler.bind(this)}>Select Cell</ButtonComponent>
        <GanttComponent dataSource={data}  ref={gantt => this.ganttInstance = gantt}  allowSelection={true} taskFields={this.taskFields}
        selectionSettings={this.settings} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Customize cell selection action

While selecting a cell in Gantt, the [`cellSelecting`](../api/gantt/#cellselecting) and [`cellSelected`](../api/gantt/#cellselected) event will be triggered. The [`cellSelecting`](../api/gantt/#cellselecting) event will be triggered on initialization of cell selection action, and you can get the current selecting cell information to prevent the selection of a particular cell in a particular row. The [`cellSelected`](../api/gantt/#cellselected) event will be triggered on completion of cell selection action, and you can get the current selected cell’s information. The following code example demonstrates how to prevent the selection of the cell using the [`cellSelecting`](../api/gantt/#cellselecting) event.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Selection, SelectionSettingsModel } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  public settings: SelectionSettingsModel = {
        mode: 'Cell'
  };
  public cellSelecting(args: any) {
        if (args.data.TaskID == 4 && args.cellIndex.cellIndex == 1) {
            args.cancel = true;
        }
    }
    render() {
        return <GanttComponent dataSource={data} allowSelection={true} taskFields={this.taskFields}
        selectionSettings={this.settings} cellSelecting={this.cellSelecting.bind(this)} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Toggle selection

The toggle selection allows you to select and deselect a specific row or cell. To enable toggle selection, set the `enableToggle` property of the selectionSettings to `true`. If you click the selected row or cell, then it will be deselected and vice versa.
By default, the `enableToggle` property is set to `false`.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent, Inject, Selection, SelectionSettingsModel } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
  };
  private ganttInstance:any;
  public settings: SelectionSettingsModel = {
        mode: 'Row',
        type: 'Multiple',
        enableToggle: true
  };
public clickHandler(){
    this.ganttInstance.selectionSettings.enableToggle = false;
}
    render() {
        return (<div>
        <ButtonComponent  onClick= { this.clickHandler.bind(this)}>Disable Toggle</ButtonComponent>
        <GanttComponent dataSource={data} ref={gantt => this.ganttInstance = gantt}  allowSelection={true} taskFields={this.taskFields}
        selectionSettings={this.settings} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent> </div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Clear selection

You can clear the selected cells and selected rows by using a method called [`clearSelection`](../api/gantt/#clearselection). The following code example demonstrates how to clear the selected rows in Gantt Chart.

{% tab template="gantt/selection", compileJsx=true%}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent, Inject, Selection, SelectionSettingsModel } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  private ganttInstance:any;
  public settings: SelectionSettingsModel = {
        mode: 'Row',
        type: 'Multiple'
  };
public clickHandler(){
    this.ganttInstance.selectionModule.selectRows([1, 3, 5]); // passing the record index as array collection
}
public clickHandler1(){
    this.ganttInstance.clearSelection(); // Clear the selected rows
}
    render() {
        return (<div>
        <ButtonComponent  onClick= { this.clickHandler.bind(this)}>Select Multiple Rows</ButtonComponent>
        <ButtonComponent  onClick= { this.clickHandler1.bind(this)}>Clear Selection</ButtonComponent>
        <GanttComponent dataSource={data} ref={gantt => this.ganttInstance = gantt}  allowSelection={true} taskFields={this.taskFields}
        selectionSettings={this.settings} height = '450px'>
        <Inject services={[Selection]} />
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}