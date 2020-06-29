---
title: "Appearance customization"
component: "Gantt"
description: "The overview section describes how to customize the Gantt taskbar and task labels in Gantt"
---

# Appearance customization

## Taskbar customization

### Taskbar Height

Height of child taskbars and parent taskbars can be customized by using [`taskbarHeight`](../api/gantt/#taskbarheight) property. The following code example shows how to use the property.

{% tab template="gantt/appearanceandstyle", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
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
        return <GanttComponent dataSource={data} taskFields={this.taskFields} rowHeight={50}
        taskbarHeight={40} height = '450px'>
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> NOTE
The [`taskbarHeight`](../api/gantt/#taskbarheight) value should be lower than the [`rowHeight`](../api/gantt/#rowheight) property value and these properties accept only pixel values.

### Conditional formatting

The default taskbar UI can be replaced with custom templates using the [`queryTaskbarInfo`](../api/gantt/#querytaskbarinfo) event. The following code example shows customizing the taskbar UI based on task progress values in the Gantt component.

{% tab template="gantt/appearanceandstyle", compileJsx=true %}

```typescript
let data: Object[] = [
  {
      TaskID: 1,
      TaskName: 'Project Initiation',
      StartDate: new Date('04/02/2019'),
      EndDate: new Date('04/21/2019'),
      subtasks: [
          { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
          { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 70 },
          { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 80 },
      ]
  },
  {
      TaskID: 5,
      TaskName: 'Project Estimation',
      StartDate: new Date('04/02/2019'),
      EndDate: new Date('04/21/2019'),
      subtasks: [
          { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
          { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
          { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 70 }
      ]
  },
];

import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-react-gantt';

class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  public queryTaskbarInfo(args: any) {
            if (args.data.Progress == 50) {
                    args.progressBarBgColor = "red";
                } else if (args.data.Progress == 70) {
                    args.progressBarBgColor = "yellow";
                } else if (args.data.Progress == 80) {
                    args.progressBarBgColor = "lightgreen";
                }
            }
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        queryTaskbarInfo={this.queryTaskbarInfo.bind(this)} height = '450px'>
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Taskbar template

You can design your own taskbars to view the tasks in Gantt by using [`taskbarTemplate`](../api/gantt/#taskbartemplate) property. And it is possible to map the template script element’s ID value to this property. It is also possible to customize the parent taskbars and milestones with custom templates by using [`parentTaskbarTemplate`](../api/gantt/#parenttaskbartemplate) and [`milestoneTemplate`](../api/gantt/#milestonetemplate) properties.

{% tab template="gantt/customization", compileJsx=true %}

```typescript
import * as React from "react";
import * as ReactDOM from "react-dom";
import { GanttComponent } from "@syncfusion/ej2-react-gantt";
import { data } from "./datasource";
class App extends React.Component<{}, {}> {
  public taskFields: any = {
    id: "TaskID",
    name: "TaskName",
    startDate: "StartDate",
    duration: "Duration",
    progress: "Progress",
    child: "subtasks"
  };

  public TaskbarTemplate(props: any) {
    return (
      <div
        className="e-gantt-child-taskbar-inner-div e-gantt-child-taskbar"
        style={{ height: "100%" }}
      >
        <div
          className="e-gantt-child-progressbar-inner-div e-gantt-child-progressbar"
          style={{
            width: props.ganttProperties.progressWidth + "px",
            height: "100%"
          }}
        >
        </div>
        <span
            className="e-task-label"
            style={{
              position: "absolute",
              fontSize: "12px",
              color: "white",
              top: "5px",
              left: "10px",
              fontFamily: "Segoe UI",
              cursor: "move"
            }}
          >
            {props.TaskName}
          </span>
      </div>
    );
  }
  public ParentTaskbarTemplate(props: any) {
    return (
      <div
        className="e-gantt-parent-taskbar-inner-div e-gantt-parent-taskbar"
        style={{ height: "100%" }}
      >
        <div
          className="e-gantt-parent-progressbar-inner-div e-row-expand e-gantt-parent-progressbar"
          style={{ width: props.ganttProperties.progressWidth+"px", height: "100%" }}
        >
         </div>
         <span
            className="e-task-label"
            style={{
              position: "absolute",
              fontSize: "12px",
              color: "white",
              top: "5px",
              left: "10px",
              fontFamily: "Segoe UI",
              cursor: "move"
            }}
          >
            {props.TaskName}
          </span>
      </div>
    );
  }
  public MilestoneTemplate(props: any) {
    return (
      <div className="e-gantt-milestone" style={{ position: "absolute" }}>
        <div
          className="e-milestone-top"
          style={{
            borderRightWidth: "15px",
            borderLeftWidth: "15px",
            borderBottomWidth: "15px"
          }}
        />
        <div
          className="e-milestone-bottom"
          style={{
            top: "15px",
            borderRightWidth: "15px",
            borderLeftWidth: "15px",
            borderTopWidth: "15px"
          }}
        />
      </div>
    );
  }
  render() {
    return (
      <GanttComponent
        dataSource={data}
        rowHeight={60}
        taskFields={this.taskFields}
        taskbarTemplate={this.TaskbarTemplate.bind(this)}
        parentTaskbarTemplate={this.ParentTaskbarTemplate.bind(this)}
        milestoneTemplate={this.MilestoneTemplate.bind(this)}
        height="450px"
      />
    );
  }
}
ReactDOM.render(<App />, document.getElementById("gantt"));
```

{% endtab %}

## Task labels

The Gantt component maps any data source fields to task labels using the [`labelSettings.leftLabel`](../api/gantt/labelSettings/#leftlabel), [`labelSettings.rightLabel`](../api/gantt/labelSettings/#rightlabel), and [`labelSettings.taskLabel`](../api/gantt/labelSettings/#tasklabel) properties. You can customize the task labels with templates.

{% tab template="gantt/customization1", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
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
  public labelSettings: any = {
    leftLabel: 'TaskID',
    rightLabel: 'Task Name: ${taskData.TaskName}',
    taskLabel: '${Progress}%'
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        labelSettings={this.labelSettings} height = '450px'>
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Connector lines

The width and background color of connector lines in Gantt can be customized using the [`connectorLineWidth`](../api/gantt/#connectorlinewidth) and [`connectorLineBackground`](../api/gantt/#connectorlinebackground) properties. The following code example shows how to use these properties.

{% tab template="gantt/appearanceandstyle", compileJsx=true %}

```typescript
let data: Object[]  = [
  {
      TaskID: 1,
      TaskName: 'Project Initiation',
      StartDate: new Date('04/02/2019'),
      EndDate: new Date('04/21/2019'),
      subtasks: [
          { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
          { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50  },
          { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'),Predecessor:"3SS", Duration: 4, Progress: 50 },
      ]
  },
  {
      TaskID: 5,
      TaskName: 'Project Estimation',
      StartDate: new Date('04/02/2019'),
      EndDate: new Date('04/21/2019'),
      subtasks: [
          { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
          { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
          { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'),Predecessor:"7FS", Duration: 3, Progress: 50 }
      ]
  },
];

import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-react-gantt';

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
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        connectorLineWidth={2} connectorLineBackground='#0aecb8' height = '450px'>
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Customize rows and cells

While rendering the TreeGrid part in Gantt, the [`rowDataBound`](../api/gantt/#rowdatabound) and [`queryCellInfo`](../api/gantt/#querycellinfo) events trigger for every row and cell. Using these events, you can customize the rows and cells. The following code example shows how to customize the cell and row elements using these events.

{% tab template="gantt/appearanceandstyle", compileJsx=true %}

```typescript
let data: Object[]  = [
  {
      TaskID: 1,
      TaskName: 'Project Initiation',
      StartDate: new Date('04/02/2019'),
      EndDate: new Date('04/21/2019'),
      subtasks: [
          { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 80 },
          { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50  },
          { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
      ]
  },
  {
      TaskID: 5,
      TaskName: 'Project Estimation',
      StartDate: new Date('04/02/2019'),
      EndDate: new Date('04/21/2019'),
      subtasks: [
          { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
          { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 60 },
          { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 3 , Progress: 50 }
      ]
  },
];


import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent } from '@syncfusion/ej2-react-gantt';

class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
    public splitterSettings: any = {
        columnIndex: 5
    };
  public customizeCell(args: any) {
            if (args.column.field == "Progress") {
               if (args.data.Progress < 60)
                  args.cell.style.backgroundColor="lightgreen"
               else
                  args.cell.style.backgroundColor="yellow"
        }
    };
    public rowDataBound(args: any) {
        if(args.data.TaskID==4)
            args.row.style.backgroundColor="red"
    }
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        splitterSettings={this.splitterSettings} queryCellInfo={this.customizeCell.bind(this)}
        rowDataBound={this.rowDataBound.bind(this)}
        height = '450px'>
     </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Grid lines

In the Gantt component, you can show or hide the grid lines in the TreeGrid side and chart side by using the [`gridLines`](../api/gantt/gridLine/) property.

The following options are available in the Gantt component for rendering the grid lines:

* Horizontal: The horizontal grid lines alone will be visible.
* Vertical: The vertical grid lines alone will be visible.
* Both: Both the horizontal and vertical grid lines will be visible on the TreeGrid and chart sides.
* None: Gridlines will not be visible on TreeGrid and chart sides.

> By default, the [`gridLines`](../api/gantt/gridLine/) property is set to `Horizontal` type.

The following code example shows how to change the gridlines rendering mode in the Gantt component.

{% tab template="gantt/appearanceandstyle", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
import {data} from './datasource';
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
        return <GanttComponent dataSource={data} gridLines='Both' taskFields={this.taskFields} height = '450px'>
      </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Splitter

In the Gantt component, the Splitter separates the TreeGrid section from the Chart section. You can change the position of the Splitter when loading the Gantt component using the [`splitterSettings`](../api/gantt/splitterSettings/) property. By splitting the TreeGrid from the chart, the width of the TreeGrid and chart sections will vary in the component. The [`splitterSettings.position`](../api/gantt/splitterSettings/#position) property denotes the percentage of the TreeGrid section’s width to be rendered and this property supports both pixels and percentage values. You can define the splitter position as column index value using the [`splitterSettings.columnIndex`](../api/gantt/splitterSettings/#columnindex) property. You can also define the splitter position with built-in splitter view modes by using the [`splitterSettings.view`](../api/gantt/splitterSettings/#view) property. The following list is the possible values for this property:

* `Default`: Shows Grid side and Gantt side.
* `Grid`: Shows Grid side alone in Gantt.
* `Chart`: Shows chart side alone in Gantt.

{% tab template="gantt/how-to splitter", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
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
  public splitterSettings: any = {
      position: "80%"
    };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        splitterSettings={this.splitterSettings} height = '450px'>
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Change splitter position dynamically

In Gantt, we can change the splitter position dynamically by using [`setSplitterPosition`](../api/gantt/#setsplitterposition) method. We can change the splitter position by passing value and type parameter to [`setSplitterPosition`](../api/gantt/#setsplitterposition) method. Type parameter will accept one of the following values 'position', 'columnIndex', 'viewType'. The following code example shows how to use this method.

{% tab template="gantt/changeSplitterDynamically", compileJsx=true %}

```typescript
let DropData: any[] =  [
    { text: 'Default', value: 'Default' },
    { text: 'Grid', value: 'Grid' },
    { text: 'Chart', value: 'Chart' },
];

import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { DropDownListComponent, ChangeEventArgs } from "@syncfusion/ej2-react-dropdowns";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
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
    let viewType:any = sel.value.toString();
    this.ganttInstance.setSplitterPosition(viewType, 'view');
}
  public clickHandler(){
    this.ganttInstance.setSplitterPosition('50%', 'position');
}
 public changeindex(){
    this.ganttInstance.setSplitterPosition(0, 'columnIndex');
}
    render() {
        return (<div>
            <DropDownListComponent dataSource={DropData}
        change={this.onChange.bind(this) as any} width= {150} value="Default"></DropDownListComponent>
        <ButtonComponent  onClick= { this.clickHandler.bind(this)}>ChangeByPosition</ButtonComponent>
        <ButtonComponent onClick= { this.changeindex.bind(this)}>ChangeByIndex</ButtonComponent>
        <GanttComponent dataSource={data} taskFields={this.taskFields}
        height = '450px' ref={gantt => this.ganttInstance = gantt}>
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}
