---
title: "Timeline"
component: "Gantt"
description: "Learn about timeline modes and customizations in the Essential JS 2 Gantt component."
---

# Timeline

In the Gantt component, timeline is used to represent the project duration as individual cells with defined unit and formats.

## Timeline view modes

Gantt contains the following in-built timeline view modes:

* Hour
* Day
* Week
* Month
* Year

Timescale mode in Gantt can be defined by using [`timelineViewMode`](../api/gantt/timelineViewMode/) property and also we can define timescale mode of top tier and bottom tier by using [`topTier.unit`](../api/gantt/timelineTierSettingsModel/#unit) and [`bottomTier.unit`](../api/gantt/timelineTierSettingsModel/#unit) properties.

### Week timeline mode

In the `Week` timeline mode, the upper part of the schedule header displays the weeks, whereas the bottom half of the header displays the days. Refer to the following code example.

{% tab template="gantt/weektimeline", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent} from '@syncfusion/ej2-react-gantt';
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
  public timelineSettings: any = {
    timelineViewMode:'Week'
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        timelineSettings={this.timelineSettings} height = '450px'>
       </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Month timeline mode

In the `Month` timeline mode, the upper part of the schedule header displays the months, whereas the bottom header of the schedule displays its corresponding weeks. Refer to the following code example.

{% tab template="gantt/monthtimeline", compileJsx=true %}

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
  public timelineSettings: any = {
    timelineUnitSize: 80,
    timelineViewMode:'Month'
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        timelineSettings={this.timelineSettings} height = '450px'>
       </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Year timeline mode

In the `Year` timeline mode, the upper schedule header displays the years whereas, the bottom header displays its corresponding months. Refer to the following code example.

{% tab template="gantt/yeartimeline", compileJsx=true %}

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
  public timelineSettings: any = {
    timelineUnitSize: 80,
    timelineViewMode:'Year'
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        timelineSettings={this.timelineSettings} height = '450px'>
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Day timeline mode

In the `Day` timeline mode, the upper part of the header displays the days whereas, the bottom schedule header displays its corresponding hours. Refer to the following code example.

{% tab template="gantt/daytimeline", compileJsx=true %}

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
  public timelineSettings: any = {
    timelineViewMode:'Day'
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        timelineSettings={this.timelineSettings} height = '450px'>
      </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Hour timeline mode

An `Hour` timeline mode tracks the tasks in minutes scale. In this mode, the upper schedule header displays hour scale and the lower schedule header displays its corresponding minutes.

{% tab template="gantt/hourtimeline", compileJsx=true %}

```typescript
let data: Object[]  = [
    {
        TaskID: 1,
        TaskName: 'Project Initiation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019 08:05:00 AM'), Duration: 10, Progress: 50 },
            { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019 08:05:00 AM'), Duration: 10, Progress: 50 },
            { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019 08:05:00 AM'), Duration: 10, Progress: 50 },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project Estimation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/02/2019 08:15:00 AM'), Duration: 15, Progress: 50 },
            { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/02/2019 08:15:00 AM'), Duration: 15, Progress: 50 },
            { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/02/2019 08:15:00 AM'), Duration: 15, Progress: 50  }
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
  public timelineSettings: any = {
    timelineViewMode:'Hour'
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} dateFormat="M/d/yyyy hh:mm:ss tt" durationUnit="Minute"
        timelineSettings={this.timelineSettings} height = '450px'>
      </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Top tier and Bottom tier

Gantt component contains two tier layout in timeline, we can customize the top tier and bottom tier using [`topTier`](../api/gantt/timelineSettings/#toptier) and [`bottomTier`](../api/gantt/timelineSettings/#bottomtier) properties. Timeline tier's unit can be defined by using [`unit`](../api/gantt/timelineTierSettings/#unit) property and [`format`](../api/gantt/timelineTierSettings/#format) property was used to define date format of timeline cell and [`count`](../api/gantt/timelineTierSettings/#count) property was used to define how many unit will be combined as single cell and [`formatter`](../api/gantt/timelineTierSettings/#formatter) property was used to define custom method to format the date value of timeline cell.

{% tab template="gantt/timeline", compileJsx=true %}

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
  public timelineSettings: any = {
    topTier: {
      format: 'MMM',
      unit: 'Month'
  },
      bottomTier: {
      unit: 'Day'
}
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        timelineSettings={this.timelineSettings} height = '450px'>
      </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Combining timeline cells

In Gantt, timeline cells in top tier and bottom tier can be combined with number of timeline units, this can be acheived by using [`topTier.count`](../api/gantt/timelineTierSettings/#count) and [`bottomTier.count`](../api/gantt/timelineTierSettings/#count) properties. Please refer the below sample.

{% tab template="gantt/combinetimeline", compileJsx=true %}

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
  public timelineSettings: any = {
    timelineUnitSize:200,
    topTier: {
      unit: 'Year'
      },
    bottomTier: {
      unit: 'Month',
      count:6
      }
    };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        timelineSettings={this.timelineSettings} height = '450px'>
      </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Format value of timeline cell

In the Gantt component, you can format the value of top and bottom timeline cells using the standard date format string or the custom formatter method. This can be done using the [`topTier.format`](../api/gantt/timelineTierSettings/#format), [`topTier.formatter`](../api/gantt/timelineTierSettings/#formatter), [`bottomTier.format`](../api/gantt/timelineTierSettings/#format) and [`bottomTier.formatter`](../api/gantt/timelineTierSettings/#formatter) properties. The following example shows how to use the formatter method for timeline cells.

{% tab template="gantt/formattimeline", compileJsx=true %}

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
  public timelineSettings: any = {
    timelineUnitSize: 50,
    topTier: {
      unit: 'Month',
      count: 3,
      formatter: (date:any) => {
                var month = date.getMonth();
                if (month >= 0 && month <=2) {
                return 'Q1';
                } else if(month >= 3 && month <=5) {
                    return 'Q2';
                } else if(month >= 6 && month <=8) {
                    return 'Q3';
                } else {
                    return 'Q4';
                }
            }
    },
    bottomTier: {
      unit: 'Month',
      format: 'MMM'
    },
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} projectStartDate='01/04/2019' projectEndDate='12/30/2019'
        timelineSettings={this.timelineSettings} height = '450px'>
      </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Timeline cell width

In the Gantt component, you can define the width value of timeline cell using the [`timelineSettings.timelineUnitSize`](../api/gantt/timelineSettings/#timelineunitsize) property. This value will be set to the bottom timeline cell, and the width value of top timeline cell will be calculated automatically based on bottom tier cell width using the [`topTier.unit`](../api/gantt/timelineTierSettings/#unit) and [`timelineSettings.timelineUnitSize`](../api/gantt/timelineSettings/#timelineunitsize) properties. Refer to the following example.

{% tab template="gantt/timelineWidth", compileJsx=true %}

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
  public timelineSettings: any = {
    timelineUnitSize: 150
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        timelineSettings={this.timelineSettings} height = '450px'>
      </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Week start day customization

In the Gantt component, you can customize the week start day using the [`weekStartDay`](../api/gantt/timelineSettings/#weekstartday) property. By default, the [`weekStartDay`](../api/gantt/timelineSettings/#weekstartday) is set to 0, which specifies the Sunday as a start day of the week. But, you can customize the week start day by using the following code example.

{% tab template="gantt/weekstartdaytimeline", compileJsx=true %}

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
  public timelineSettings: any = {
    timelineViewMode:'Week',
    weekStartDay: 3
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        timelineSettings={this.timelineSettings} height = '450px'>
      </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Customize automatic timescale update action

In the Gantt component, the schedule timeline will be automatically updated when the tasks date values are updated beyond the project start date and end date ranges. This can be enabled or disabled using the [`updateTimescaleView`](../api/gantt/timelineSettings/#updatetimescaleview) property.

{% tab template="gantt/updatetimescale", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Edit, EditSettingsModel, Selection } from '@syncfusion/ej2-react-gantt';
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
  public editOptions: EditSettingsModel = {
    allowEditing: true,
    allowTaskbarEditing: true
  };
  public timelineSettings: any = {
    updateTimescaleView: false
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        timelineSettings={this.timelineSettings} allowSelection={true}
        editSettings={this.editOptions} height = '450px'>
            <Inject services={[Edit, Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Zooming

The zooming support provides options to increase or decrease the width of timeline cells and also provides options to change the timeline units dynamically. This support enables you to view the tasks in a project clearly from minute to decade timespan. To enable the zooming features, define the `ZoomIn`, `ZoomOut`, and `ZoomToFit` items to toolbar items collections, and this action can be performed on external actions such as button click using the [`zoomIn`](../api/gantt/#zoomin), [`zoomOut`](../api/gantt/#zoomout), and [`fitToProject`](../api/gantt/#fittoproject) built-in methods. The following zooming options are available to view the project:

### Zoom in

This support is used to increase the timeline width and timeline unit from years to minutes
timespan. When the `ZoomIn` icon was clicked, the timeline cell width is increased when the cell
size exceeds the specified range and the timeline unit is changed based on the current zoom levels.

### Zoom out

This support is used to increase the timeline width and timeline unit from minutes to years timespan. When the `ZoomOut` icon was clicked, the timeline cell width is decreased when the cell size falls behind the specified range and the timeline view mode is changed based on the current zooming levels.

### Zoom to fit

This support is used to view all the tasks available in a project within available area on the chart part of Gantt. When users click the `ZoomToFit` icon, then all the tasks are rendered within the available chart container width.

{% tab template="gantt/zooming", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Toolbar, ToolbarItem }from '@syncfusion/ej2-react-gantt';
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
  
  public toolbarOptions: ToolbarItem[] = ['ZoomIn','ZoomOut','ZoomToFit'];
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        toolbar={this.toolbarOptions} height = '450px'>
           <Inject services={[Toolbar]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Customizing zooming levels

In Gantt, the zoom in and zoom out actions are performed based on the predefined zooming levels in the `zoomingLevels` property. You can customize the zooming actions by defining the required zooming collection to the `zoomingLevels` property.

{% tab template="gantt/zooming", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Toolbar, ToolbarItem , ZoomTimelineSettings}from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
let customZoomingLevels: ZoomTimelineSettings[] =  [{
                topTier: { unit: 'Month', format: 'MMM, yy', count: 1 },
                bottomTier: { unit: 'Week', format: 'dd', count: 1 }, timelineUnitSize: 33, level: 0,
                timelineViewMode: 'Month', weekStartDay: 0, updateTimescaleView: true, weekendBackground: null, showTooltip: true
            },
            {
                topTier: { unit: 'Month', format: 'MMM, yyyy', count: 1 },
                bottomTier: { unit: 'Week', format: 'dd MMM', count: 1 }, timelineUnitSize: 66, level: 1,
                timelineViewMode: 'Month', weekStartDay: 0, updateTimescaleView: true, weekendBackground: null, showTooltip: true
            },
            {
                topTier: { unit: 'Month', format: 'MMM, yyyy', count: 1 },
                bottomTier: { unit: 'Week', format: 'dd MMM', count: 1 }, timelineUnitSize: 99, level: 2,
                timelineViewMode: 'Month', weekStartDay: 0, updateTimescaleView: true, weekendBackground: null, showTooltip: true
            },
            {
                topTier: { unit: 'Week', format: 'MMM dd, yyyy', count: 1 },
                bottomTier: { unit: 'Day', format: 'd', count: 1 }, timelineUnitSize: 33, level: 3,
                timelineViewMode: 'Week', weekStartDay: 0, updateTimescaleView: true, weekendBackground: null, showTooltip: true
            },
            {
                topTier: { unit: 'Week', format: 'MMM dd, yyyy', count: 1 },
                bottomTier: { unit: 'Day', format: 'd', count: 1 }, timelineUnitSize: 66, level: 4,
                timelineViewMode: 'Week', weekStartDay: 0, updateTimescaleView: true, weekendBackground: null, showTooltip: true
            },
            {
                topTier: { unit: 'Day', format: 'E dd yyyy', count: 1 },
                bottomTier: { unit: 'Hour', format: 'hh a', count: 12 }, timelineUnitSize: 66, level: 5,
                timelineViewMode: 'Day', weekStartDay: 0, updateTimescaleView: true, weekendBackground: null, showTooltip: true
            },
            {
                topTier: { unit: 'Day', format: 'E dd yyyy', count: 1 },
                bottomTier: { unit: 'Hour', format: 'hh a', count: 6 }, timelineUnitSize: 99, level: 6,
                timelineViewMode: 'Day', weekStartDay: 0, updateTimescaleView: true, weekendBackground: null, showTooltip: true
            },
];
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
   private ganttInstance:any;
   public dataBound() {
       this.ganttInstance.zoomingLevels = customZoomingLevels;
  };
  public toolbarOptions: ToolbarItem[] = ['ZoomIn','ZoomOut','ZoomToFit'];
    render() {
        return <GanttComponent dataSource={data}
        ref={gantt => this.ganttInstance = gantt} taskFields={this.taskFields}  
        dataBound = {this.dataBound.bind(this)} toolbar={this.toolbarOptions}
        height = '450px'>
           <Inject services={[Toolbar]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Zoom action by methods

You can perform the various zoom actions dynamically or on external click action using the following methods:
* Zoom in - [`zoomIn`](../api/gantt/#zoomin)
* Zoom out - [`zoomOut`](../api/gantt/#zoomout)
* Fit to project - [`fitToProject`](../api/gantt/#fittoproject)

{% tab template="gantt/zooming", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent}from '@syncfusion/ej2-react-gantt';
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
   private ganttInstance:any;
    zoomIn() {
        this.ganttInstance.zoomIn();
    }
    zoomOut() {
        this.ganttInstance.zoomOut();
    }
    fitToProject() {
        this.ganttInstance.fitToProject();
    }
    render() {
         return (<div>
        <ButtonComponent onClick={this.zoomIn.bind(this)}>ZoomIn</ButtonComponent>
        <ButtonComponent onClick={this.zoomOut.bind(this)}>ZoomOut</ButtonComponent>
        <ButtonComponent onClick={this.fitToProject.bind(this)}>FitToProject</ButtonComponent>
        <GanttComponent dataSource={data}
        ref={gantt => this.ganttInstance = gantt} taskFields={this.taskFields} height = '450px'>
        </GanttComponent></div>);
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}