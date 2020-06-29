---
title: "Sorting"
component: "Gantt"
description: "Learn how to order the records in the Essential JS 2 Gantt component."
---

# Sorting

Sorting enables you to sort data in the ascending or descending order. To sort a column, click the column header.

To sort multiple columns, press and hold the CTRL key and click the column header. You can clear sorting of any one of the multi-sorted columns by pressing and holding the SHIFT key and clicking the specific column header.

To enable sorting in the Gantt component, set the [`allowSorting`](../api/gantt/#allowsorting) property to `true`. Sorting options can be configured through the [`sortSettings`](../api/gantt/sortSettings/) property.

To sort, inject the [`Sort`](../api/gantt/#sortmodule) module into the Gantt component.

{% tab template="gantt/sorting", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Sort } from '@syncfusion/ej2-react-gantt';
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
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
          allowSorting={true} height='450px'>
         <Inject services={[Sort]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> * Gantt columns are sorted in the ascending order. If you click the already sorted column, the sort direction toggles.
> * To disable sorting for a particular column, set the [`columns.allowSorting`](../api/gantt/column/#allowsorting) property to `false`.

## Sorting column on Gantt initialization

The Gantt component can be rendered with sorted columns initially, and this can be achieved by using the [`sortSettings`](../api/gantt/sortSettings/) property. You can add columns that are sorted initially in the [`sortSettings.columns`](../api/gantt/sortSettings/#columns) collection defined with [`field`](../api/gantt/sortDescriptorModel/#field) and [`direction`](../api/gantt/sortDescriptorModel/#direction) properties. The following code example shows how to add the sorted column to Gantt initialization.

{% tab template="gantt/sorting", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Sort, SortSettingsModel } from '@syncfusion/ej2-react-gantt';
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
  public sortingOptions: SortSettingsModel = { columns: [{ field: 'TaskID', direction: 'Descending' }] };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} sortSettings={this.sortingOptions} allowSorting={true} height='450px'>
          <Inject services={[Sort]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Sorting column dynamically

Columns in the Gantt component can be sorted dynamically using the [`sortColumn`](../api/gantt/#sortcolumn) method. The following code example demonstrates how to invoke the [`sortColumn`](../api/gantt/#sortcolumn) method by clicking the custom button.

{% tab template="gantt/sortingColumns", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent, Inject, Sort } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
   private gantt: any;
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
    };

    public clickHandler() {
        this.gantt.sortModule.sortColumn('TaskID', "Descending", false);
    }
    render() {
        return (<div>
            <ButtonComponent onClick={this.clickHandler.bind(this)}>Sort Column</ButtonComponent>
            <GanttComponent dataSource={data} ref={g => this.gantt = g} taskFields={this.taskFields}
                allowSorting={true} height='450px'>
               <Inject services={[Sort]} />
            </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Clear all the sorted columns dynamically

In the Gantt component, you can clear all the sorted columns and return to previous position using the [`clearSorting`](../api/gantt/#clearsorting) public method. The following code snippet shows how to clear all the sorted columns by clicking the custom button.

{% tab template="gantt/clearSorting", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent, Inject, Sort, SortSettingsModel } from '@syncfusion/ej2-react-gantt';
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
  private ganttInstance: any;
  public sortingOptions: SortSettingsModel = { columns: [{ field: 'TaskID', direction: 'Descending' }] };
  public clickHandler(){
  this.ganttInstance.clearSorting();
}
    render() {
        return (<div>
            <ButtonComponent onClick= { this.clickHandler.bind(this)}>Clear Sorting</ButtonComponent>
            <GanttComponent dataSource={data} taskFields={this.taskFields}  ref={gantt => this.ganttInstance = gantt} allowSorting={true} sortSettings={this.sortingOptions} height='450px'>
          <Inject services={[Sort]} />
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Sorting events

During the sort action, the Gantt component triggers two events. The [`actionBegin`](../api/gantt/#actionbegin) event triggers before the sort action starts, and the [`actionComplete`](../api/gantt/#actioncomplete) event triggers after the sort action is completed.

{% tab template="gantt/sorting", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Sort  } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    dependency: 'Predecessor',
    child: 'subtasks'
  };
  public actionHandler (args: any) {
        alert(args.requestType + ' ' + args.type);
    }
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} allowSorting={true}
        actionBegin={this.actionHandler.bind(this)} actionComplete={this.actionHandler.bind(this)} height='450px'>
          <Inject services={[Sort]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> The `args.requestType` is the current action name. For example, for sorting the `args.requestType`, value is **sorting**.