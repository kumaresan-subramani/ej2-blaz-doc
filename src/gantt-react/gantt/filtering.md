---
title: "Filtering"
component: "Gantt"
description: "Learn how to filter rows in the Gantt using the menu filtering. Also learn how to use custom filter components in the Essential JS 2 Gantt component."
---

# Filtering

Filtering allows you to view specific or related records based on filter criteria. This can be done in the Gantt component by using the filter menu and toolbar search. To enable filtering in the Gantt component, set the [`allowFiltering`](../api/gantt/#allowfiltering) to `true`. Menu -filtering support can be configured using the [`filterSettings`](../api/gantt/filterSettings/) property and toolbar searching can be configured using the [`searchSettings`](../api/gantt/searchSettings/) property.

To use filter, inject the [`Filter`](../api/gantt/#filtermodule) module into the Gantt component.

## Menu filtering

The Gantt component provides menu-filtering support for each column. You can enable the filter menu by setting the [`allowFiltering`](../api/gantt/#allowfiltering) to `true`. The filter menu UI will be rendered based on its column type, which allows you to filter data. You can filter the records with different operators.

{% tab template="gantt/filtering", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Filter } from '@syncfusion/ej2-react-gantt';
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
         allowFiltering={true} height = '450px'>
            <Inject services={[Filter]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

>The [`allowFiltering`](../api/gantt/#allowfiltering) property should be set to `true` to enable the filter menu.
>Setting the [`columns.allowFiltering`](../api/gantt/column/#allowfiltering) property to `false` prevents rendering the filter menu for a particular column.

### Filter hierarchy modes

The Gantt component supports a set of filtering modes with the [`filterSettings.hierarchyMode`](../api/gantt/filterSettings/#hierarchymode) property. The following are the types of filter hierarchy modes available in the Gantt component:

* `Parent`: This is the default filter hierarchy mode in Gantt. The filtered records are displayed with their parent records. If the filtered records do not have any parent record, then only the filtered records will be displayed.

* `Child`: Displays the filtered records with their child record. If the filtered records do not have any child record, then only the filtered records will be displayed.

* `Both`: Displays the filtered records with their both parent and child records. If the filtered records do not have any parent or child records, then only the filtered records will be displayed.

* `None`: Displays only the filtered records.

{% tab template="gantt/filterhierarchy", compileJsx=true %}

```typescript

let DropData: any[] =  [
  { text: 'Parent', value: 'Parent' },
  { text: 'Child', value: 'Child' },
  { text: 'Both', value: 'Both' },
  { text: 'None', value: 'None' },
];
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { DropDownListComponent, ChangeEventArgs } from "@syncfusion/ej2-react-dropdowns";
import { GanttComponent, Inject, Filter } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    private ganttInstance: any;
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  public onChange(sel: ChangeEventArgs): void {
        let mode:any = sel.value.toString();
        this.ganttInstance.filterSettings.hierarchyMode = mode;
        this.ganttInstance.clearFiltering();
    }
    render() {
        return(<div>
        <DropDownListComponent dataSource={DropData}
        change={this.onChange.bind(this) as any} width= {150} value="Parent"></DropDownListComponent>
        <GanttComponent dataSource={data} taskFields={this.taskFields}
         allowFiltering={true} height = '450px' ref={gantt => this.ganttInstance = gantt}>
          <Inject services={[Filter]} />
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Initial filter

To apply the filter at initial rendering, set the filter to `predicate` object in the [`filterSettings.columns`](../api/gantt/filterSettings/#columns) property.

{% tab template="gantt/initialfilter", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Filter, FilterSettingsModel } from '@syncfusion/ej2-react-gantt';
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
  public FilterOptions: FilterSettingsModel = {
    columns: [
        { field: 'TaskName', matchCase: false, operator: 'startswith', predicate: 'and', value: 'Identify' },
       { field: 'TaskID', matchCase: false, operator: 'equal', predicate: 'and', value: 2 }]
};
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
         allowFiltering={true} filterSettings={this.FilterOptions} height = '450px'>
         <Inject services={[Filter]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Filter operators

The filter operator for a column can be defined in the `filterSettings.columns.operator` property.

The available operators and their supported data types are:

Operator |Description |Supported Types
-----|-----|-----
startswith |Checks whether the value begins with the specified value. |String
endswith |Checks whether the value ends with the specified value. |String
contains |Checks whether the value contains the specified value. |String
equal |Checks whether the value is equal to the specified value. |String &#124; Number &#124; Boolean &#124; Date
notequal |Checks for the values that are not equal to the specified value. |String &#124; Number &#124; Boolean &#124; Date
greaterthan |Checks whether the value is greater than the specified value. |Number &#124; Date
greaterthanorequal|Checks whether the value is greater than or equal to the specified value. |Number &#124; Date
lessthan |Checks whether the value is less than the specified value. |Number &#124; Date
lessthanorequal |Checks whether the value is less than or equal to the specified value. |Number &#124; Date

> By default, the `filterSettings.columns.operator` value is `equal`

### Diacritics

By default, the Gantt component ignores the diacritic characters while filtering. To include diacritic characters, set the [`filterSettings.ignoreAccent`](../api/gantt/filterSettings/#ignoreaccent) to `true`.

In the following sample, type **Perform** in the `TaskName` column to filter diacritic characters.

{% tab template="gantt/diacriticsfilter", compileJsx=true %}

```typescript
let data: Object[]  = [
  {
      TaskID: 1,
      TaskName: 'Projéct initiàtion',
      StartDate: new Date('04/02/2019'),
      EndDate: new Date('04/21/2019'),
      subtasks: [
          {TaskID: 2, TaskName: 'Identify site locàtion', StartDate: new Date('04/02/2019'), Duration: 4,Progress: 50 },
          {TaskID: 3, TaskName: 'Perförm soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
          {TaskID: 4, TaskName: 'Soil tëst appröval', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
      ]
  },
  {
      TaskID: 5,
      TaskName: 'Project estimation',
      StartDate: new Date('04/02/2019'),
      EndDate: new Date('04/21/2019'),
      subtasks: [
          {TaskID: 6, TaskName: 'Develöp floor plan for estimàtion', StartDate: new Date('04/04/2019'),Duration: 3, Progress: 50, resources: [4]},
          {TaskID: 7, TaskName: 'List matërials', StartDate: new Date('04/04/2019'),Duration: 3, Progress: 50},
          {TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'),Duration: 3, Progress: 50 }
      ]
  }];


import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Filter, FilterSettingsModel } from '@syncfusion/ej2-react-gantt';

class App extends React.Component<{}, {}>{
  public taskFields: any = {
  id: 'TaskID',
  name: 'TaskName',
  startDate: 'StartDate',
  duration: 'Duration',
  progress: 'Progress',
  child: 'subtasks'
};
public FilterOptions: FilterSettingsModel = {
          ignoreAccent:true
      };
  render() {
      return <GanttComponent dataSource={data} taskFields={this.taskFields}
       allowFiltering={true} filterSettings={this.FilterOptions} height = '450px'>
          <Inject services={[Filter]} />
      </GanttComponent>
  }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Filtering a specific column by method

You can filter the columns dynamically by using the [`filterByColumn`](../api/gantt/#filterbycolumn) method.

{% tab template="gantt/filterbymethod", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent, Inject, Filter } from '@syncfusion/ej2-react-gantt';
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
  public clickHandler(){
    this.gantt.filterByColumn('TaskName','startswith','Perf');
}
    render() {
        return(<div>
        <ButtonComponent onClick= { this.clickHandler.bind(this)}>Filter Column</ButtonComponent>
        <GanttComponent dataSource={data} taskFields={this.taskFields}
         allowFiltering={true} height = '450px' ref={gantt => this.gantt = gantt}>
            <Inject services={[Filter]} />
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Clear filtered columns

You can clear all the filtering conditions done in the Gantt component by using the [`clearFiltering`](../api/gantt/#clearfiltering) method.
The following code snippet explains the above behavior.

{% tab template="gantt/clearfilter", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent, Inject, Filter, FilterSettingsModel } from '@syncfusion/ej2-react-gantt';
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
  public FilterOptions: FilterSettingsModel = {
            columns: [
                { field: 'TaskName', matchCase: false, operator: 'startswith', predicate: 'and', value: 'perfor' },
               { field: 'TaskID', matchCase: false, operator: 'equal', predicate: 'and', value: 3 }]
        };
  public clickHandler(){
    this.gantt.clearFiltering();
}
    render() {
        return(<div>
        <ButtonComponent  onClick= { this.clickHandler.bind(this)}>Clear Filter</ButtonComponent>
        <GanttComponent dataSource={data} taskFields={this.taskFields} filterSettings={this.FilterOptions}
         allowFiltering={true} height = '450px' ref={gantt => this.gantt = gantt}>
            <Inject services={[Filter]} />
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Search

You can search for records in the Gantt component by using the [`search`](../api/gantt/#search) method with search key as a parameter. The Gantt component provides an option to integrate the search text box in the toolbar by adding the search item to the [`toolbar`](../api/gantt/#toolbar) property.

To search records, inject the `Filter` module into the Gantt component.

{% tab template="gantt/searching", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Filter, Toolbar, ToolbarItem } from '@syncfusion/ej2-react-gantt';
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
  public toolbarOptions: ToolbarItem[] = ['Search'];
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
         allowFiltering={true} toolbar={this.toolbarOptions} height = '450px'>
            <Inject services={[Filter, Toolbar]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Initial search

In the Gantt component, you can load a task with some search criteria by using the [`searchSettings`](../api/gantt/searchSettings/) property.
To apply a search at initial rendering, set the value for [`fields`](../api/gantt/searchSettings/#fields), [`operator`](../api/gantt/searchSettings/#operator), [`key`](../../api/gantt/searchSettings/#key), and [`ignoreCase`](../api/gantt/searchSettings/#ignorecase) in the [`searchSettings`](../api/gantt/searchSettings/) property.

{% tab template="gantt/searching", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Filter, Toolbar, ToolbarItem, SearchSettingsModel } from '@syncfusion/ej2-react-gantt';
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
  public toolbarOptions: ToolbarItem[] = ['Search'];
  public searchSettings: SearchSettingsModel = {
      fields: ['TaskName'], operator: 'contains', key: 'Soil', ignoreCase: true
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
         allowFiltering={true} toolbar={this.toolbarOptions} searchSettings={this.searchSettings}
         height = '450px'>
           <Inject services={[Filter, Toolbar]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> By default, Gantt searches all the bound column values. To customize this behavior, define the [`searchSettings.fields`](../api/gantt/searchSettings/#fields) property.

### Search operators

The search operator can be defined in the [`searchSettings.operator`](../api/gantt/searchSettings/#operator) property to configure specific searching.

The following operators are supported in searching:

Operator |Description
-----|-----
startsWith |Checks whether a value begins with the specified value.
endsWith |Checks whether a value ends with the specified value.
contains |Checks whether a value contains the specified value.
equal |Checks whether a value is equal to the specified value.
notEqual |Checks for the values that are not equal to the specified value.

> By default, the [`searchSettings.operator`](../api/gantt/searchSettings/#operator) value is `contains`.

### Search by external button

To search the Gantt records from an external button, invoke the [`search`](../api/gantt/#search) method.

{% tab template="gantt/searching", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent, Inject, Filter } from '@syncfusion/ej2-react-gantt';
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
  private textInput:any;
  public inputStyle={
         width:"250px"
  };
  public clickHandler(){
     this.ganttInstance.search(this.textInput.value);
}
    render() {
        return(<div>
        <div className='e-float-input' style={this.inputStyle}>
            <input type="text" className="searchtext" ref={(input) => this.textInput = input}   />
            <span className="e-float-line"></span>
            <label className="e-float-text">Search text</label>
        </div>
        <ButtonComponent onClick= { this.clickHandler.bind(this)}>Search</ButtonComponent>
        <GanttComponent dataSource={data}  ref={gantt => this.ganttInstance = gantt}  taskFields={this.taskFields}
         allowFiltering={true} height = '450px'>
        <Inject services={[Filter]} />
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

>Note: You should set the [`allowFiltering`](../api/gantt/#allowfiltering) property to `true` for searching the content externally.

### Search specific columns

By default, the Gantt component searches all the columns. You can search specific columns by defining the specific column's field names in the [`searchSettings.fields`](../api/gantt/searchSettings/#fields) property.

{% tab template="gantt/searching", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Filter, Toolbar, ToolbarItem, SearchSettingsModel } from '@syncfusion/ej2-react-gantt';
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
  public toolbarOptions: ToolbarItem[] = ['Search'];
  private searchSettings: SearchSettingsModel = {fields: ['TaskName','Duration']};
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
         allowFiltering={true} searchSettings={this.searchSettings} toolbar={this.toolbarOptions}
         height = '450px'>
           <Inject services={[Filter, Toolbar]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> In above sample, you can search only **TaskName** and **Duration** column values.