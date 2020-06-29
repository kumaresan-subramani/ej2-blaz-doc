---
title: "Task scheduling"
component: "Gantt"
description: "Learn how to schedule the tasks in the Essential JS 2 Gantt control."
---

# Task Scheduling

The Gantt provides support for automatic and manual task scheduling modes. It is used to indicate whether the start date and end date of all the tasks will be automatically validated or not. [`taskMode`](../api/gantt/#taskmode) is the property used to change the schedule mode of a task.

The Gantt control supports three types of mode. They are:

* `Auto`: All the tasks are automatically validate.
* `Manual`: All the tasks are manually validate by the user.
* `Custom`: Both Auto and Manual tasks are render by mapped from data source.

>Note: The default value of [`taskMode`](../api/gantt/#taskmode) is `Auto`.

## Automatically Scheduled Tasks

When the [`taskMode`](../api/gantt/#taskmode) property is set as `Auto`, the start date and end date of all the tasks in the project will be automatically validated. That is, dates are validated based on various factors such as working time, holidays, weekends and predecessors.

{% tab template="gantt/task-scheduling", compileJsx=true %}

```typescript

import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Edit, Selection, Toolbar } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component {
    constructor() {
        super(...arguments);
        this.taskFields = {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'Children'
        };
        this.toolbarOptions = ['Add', 'Edit', 'Delete', 'Cancel', 'Update', 'PrevTimeSpan', 'NextTimeSpan', 'ExpandAll', 'CollapseAll', 'Search'];
        this.editSettings = {
            allowEditing: true,
            allowDeleting: true,
            allowTaskbarEditing: true
        };
    }
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} highlightWeekends={true} toolbar={this.toolbarOptions} editSettings={this.editOptions} taskMode='Auto' height='450px'>
         <Inject services={[Edit, Selection, Toolbar]}/>
        </GanttComponent>;
    }
}
;
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %}

## Manually Scheduled Tasks

When the [`taskMode`](../api/gantt/#taskmode) property is set as `Manual`, the start date and end date of all the tasks in the project will be same as given in the data source. That is, dates are not validated based on various factors such as dependencies between tasks, holidays, weekends, working time.
We can restrict this mode in predecessor validation alone. That is, we can automatically validate the dates based on predecessor values by enabling the [`validateManualTasksOnLinking`](../api/gantt/#validatemanualtasksonlinking) property.

{% tab template="gantt/task-scheduling", compileJsx=true %}

```typescript

import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Edit, Selection, Toolbar } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component {
    constructor() {
        super(...arguments);
        this.taskFields = {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'Children'
        };
        this.toolbarOptions = ['Add', 'Edit', 'Delete', 'Cancel', 'Update', 'PrevTimeSpan', 'NextTimeSpan', 'ExpandAll', 'CollapseAll', 'Search'];
        this.editSettings = {
            allowEditing: true,
            allowDeleting: true,
            allowTaskbarEditing: true
        };
    }
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} highlightWeekends={true} toolbar={this.toolbarOptions} editSettings={this.editOptions} taskMode='Manual' height='450px'>
         <Inject services={[Edit, Selection, Toolbar]}/>
        </GanttComponent>;
    }
}
;
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %}

## Custom

When the [`taskMode`](../api/gantt/#taskmode) property is set as `Custom`, the scheduling mode for each tasks will be mapped from the data source field. The `Boolean` property [`taskFields.manual`](../api/gantt/taskFields/#manual) is used to map the manual scheduling mode field from the data source.

{% tab template="gantt/task-scheduling", compileJsx=true %}

```typescript

import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Edit, Selection, Toolbar, ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component {
    constructor() {
        super(...arguments);
        this.taskFields = {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'Children',
            manual: 'isManual'
        };
        this.toolbarOptions = ['Add', 'Edit', 'Delete', 'Cancel', 'Update', 'PrevTimeSpan', 'NextTimeSpan', 'ExpandAll', 'CollapseAll', 'Search'];
        this.editSettings = {
            allowEditing: true,
            allowDeleting: true,
            allowTaskbarEditing: true
        };
    }
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} highlightWeekends={true} toolbar={this.toolbarOptions} editSettings={this.editOptions} taskMode='Custom' height='450px'>
         <ColumnsDirective>
                <ColumnDirective field='TaskID' visible={false}></ColumnDirective>
                <ColumnDirective field='TaskName'></ColumnDirective>
                <ColumnDirective field='isManual'></ColumnDirective>
            </ColumnsDirective>
         <Inject services={[Edit, Selection, Toolbar]}/>
        </GanttComponent>;
    }
}
;
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %} -->

## Unscheduled Tasks

Unscheduled tasks are planned for a project without any definite schedule dates. The Gantt control supports rendering the unscheduled tasks. You can create or update the tasks with anyone of start date, end date, and duration values or none. You can enable or disable the unscheduled tasks by using the [`allowUnscheduledTasks`](../api/gantt/#allowunscheduledtasks) property. The following images represent the various types of unscheduled tasks in Gantt.

Taskbar state |Auto |Manual
-----|-----|-----
`Start Date Only` | ![Alt text](images/startDate-only.png) | ![Alt text](images/startDate-manual.png)
`End Date Only` | ![Alt text](images/endDate-only.png) | ![Alt text](images/endDate-manual.png)
`Duration Only` | ![Alt text](images/duration-only.png) | ![Alt text](images/duration-manual.png)
`Milestone`| ![Alt text](images/milestone.png) | ![Alt text](images/milestone.png)

>Note: A milestone is a task that has no start and end dates, but it has a duration value of zero

## Define unscheduled tasks in data source

You can define the various types of unscheduled tasks in the data source as follows

{% tab template="gantt/task-scheduling", compileJsx=true %}

```typescript

let GanttData = [
    {
        TaskID: 1,
        TaskName: 'Project Initiation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            { TaskID: 2, TaskName: 'Identify Site location', Duration: 3, Progress: 50 },
            { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Progress: 50 },
            { TaskID: 4, TaskName: 'Soil test approval', EndDate: new Date('04/08/2019'), Progress: 50 },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project Estimation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), EndDate: new Date('04/08/2019'), Progress: 50 },
            { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Progress: 50 },
            { TaskID: 8, TaskName: 'Estimation approval', Duration: 0, Progress: 50 }
        ]
    },
];
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Edit } from '@syncfusion/ej2-react-gantt';
class App extends React.Component {
    constructor() {
        super(...arguments);
        this.taskFields = {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            endDate: 'EndDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        };
this.editSettings = {
            allowEditing: true,
            allowTaskbarEditing: true,
        };
    }
    render() {
        return <GanttComponent dataSource={GanttData} taskFields={this.taskFields} editSettings={this.editSettings} allowUnscheduledTasks={true} height='400px'>
<Inject services={[Edit]}/>
        </GanttComponent>;
    }
}
;
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %}

> NOTE
> If the [`allowUnscheduledTasks`](../api/gantt/#allowunscheduledtasks) property is set to false, then the Gantt control automatically calculates the scheduled date values with a default value of duration 1 and the project start date is considered as the start date for the task.

## Working Time Range

In the Gantt control, working hours in a day for a project can be defined by using the [`dayWorkingTime`](../api/gantt/dayWorkingTime/) property. Based on the working hours, automatic date scheduling and duration validations for a task are performed.

The following code snippet explains how to define the working time range for the project in Gantt.

{% tab template="gantt/task-scheduling", compileJsx=true %}

```typescript

import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component {
    constructor() {
        super(...arguments);
        this.taskFields = {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'Children'
        };
        this.timelineSettings = {
            timelineViewMode: 'Day'
        };
        this.dayWorkingTime = [{ from: 9, to: 18 }];
    }
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} dayWorkingTime={this.dayWorkingTime} timelineSettings={this.timelineSettings} height='450px'>
      </GanttComponent>;
    }
}
;
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %}

> NOTE
>* Individual tasks can lie between any time within the defined working time range of the project.
>* The [`dayWorkingTime`](../api/gantt/dayWorkingTime/) property is used to define the working time for the whole project.

## Weekend/Non-working days

Non-working days/weekend are used to represent the non-productive days in a project. You can define the non-working days in a week using the [`workWeek`](../api/gantt/#workweek) property in Gantt.

{% tab template="gantt/task-scheduling", compileJsx=true %}

```typescript

import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, DayMarkers } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component {
    constructor() {
        super(...arguments);
        this.taskFields = {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'Children'
        };
        this.workWeek = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday'];
    }
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} highlightWeekends={true} workWeek={this.workWeek} height='450px'>
         <Inject services={[DayMarkers]}/>
        </GanttComponent>;
    }
}
;
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %}

> By default, Saturdays and Sundays are considered as non-working days/weekend in a project.
> In the Gantt control, you can make weekend as working day by setting the [`includeWeekend`](../api/gantt/#includeweekend) property to `true`.