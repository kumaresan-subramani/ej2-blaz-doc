---
title: "Work"
component: "Gantt"
description: "Learn how to map the work field to the tasks in the Essential JS 2 Gantt control."
---

# Work

The work is the total hours required to complete a task. Work can be mapped from the data source field using the property [`taskFields.work`](../api/gantt/taskFields/#work). Work can be measured in
`Hour`, `Day`, `Minute`. By default, work is measured in `Hour` and it can be changed, by using the property [`workUnit`](../api/gantt/#viewtype).

>Note: When the work field is mapped from the data source, the default task type will be `FixedWork`.

{% tab template="gantt/work", compileJsx=true %}

```typescript

export let ProjectResources = [
    { resourceId: 1, resourceName: 'Martin Tamer' },
    { resourceId: 2, resourceName: 'Rose Fuller' },
    { resourceId: 3, resourceName: 'Margaret Buchanan' },
    { resourceId: 4, resourceName: 'Fuller King' },
    { resourceId: 5, resourceName: 'Davolio Fuller' },
    { resourceId: 6, resourceName: 'Van Jack' },
    { resourceId: 7, resourceName: 'Fuller Buchanan' },
    { resourceId: 8, resourceName: 'Jack Davolio' },
    { resourceId: 9, resourceName: 'Tamer Vinet' },
    { resourceId: 10, resourceName: 'Vinet Fuller' },
    { resourceId: 11, resourceName: 'Bergs Anton' },
    { resourceId: 12, resourceName: 'Construction Supervisor' }
];
let data = [
    {
        TaskID: 1,
        TaskName: 'Project initiation',
        StartDate: new Date('03/29/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {
                TaskID: 2, TaskName: 'Identify site location', StartDate: new Date('03/29/2019'), Duration: 2,
                Progress: 30, Work: 16, resources: [{ resourceId: 1, Unit: 70 }, 6]
            },
            {
                TaskID: 3, TaskName: 'Perform soil test', StartDate: new Date('03/29/2019'), Duration: 4,
                resources: [2, 3, 5], Work: 96
            },
            {
                TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('03/29/2019'), Duration: 1,
                Work: 16, resources: [8, { resourceId: 9, Unit: 50 }], Progress: 30
            },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation', StartDate: new Date('03/29/2019'), EndDate: new Date('04/21/2019'),
        subtasks: [
            {
                TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('03/29/2019'),
                Duration: 3, Progress: 30, resources: [{ resourceId: 4, Unit: 50 }], Work: 30
            },
            {
                TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/01/2019'), Duration: 3,
                Work: 48, resources: [4, 8]
            },
            {
                TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/01/2019'),
                Duration: 2, Work: 60, resources: [12, { resourceId: 5, Unit: 70 }]
            }
        ]
    },
    {
        TaskID: 9, TaskName: 'Sign contract', StartDate: new Date('04/01/2019'), Duration: 1,
        Progress: 30, resources: [12], Work: 24
    }
];
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, ColumnsDirective, ColumnDirective, Inject, Edit, Selection, Toolbar } from '@syncfusion/ej2-react-gantt';
class App extends React.Component {
    constructor() {
        super(...arguments);
        this.taskFields = {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            resourceInfo: 'resources',
            work: 'Work',
            child: 'subtasks'
        };
        this.resourceFields = {
            id: 'resourceId',
            name: 'resourceName',
            unit: 'Unit'
        };
        this.editSettings = {
            allowAdding: true,
            allowEditing: true,
            allowDeleting: true,
            allowTaskbarEditing: true,
            showDeleteConfirmDialog: true
        };
        this.workUnit = 'Hour';
        this.toolbar = ['Add', 'Edit', 'Update', 'Delete', 'Cancel', 'ExpandAll', 'CollapseAll'];
    }
    render() {
        return <GanttComponent id='root' dataSource = { data } treeColumnIndex = { 1} allowSelection = { true} allowResizing = { true} highlightWeekends = { true} toolbar = { this.toolbar } editSettings = { this.editSettings } resourceFields = { this.resourceFields } taskFields = { this.taskFields } height = '410px' resources = { ProjectResources } >
            <ColumnsDirective>
            <ColumnDirective field= 'TaskID' visible= {false} > </ColumnDirective>
            <ColumnDirective field= 'TaskName'  headerText= 'Task Name'  width= '180' > </ColumnDirective>
            <ColumnDirective field= 'resources'  headerText= 'Resources'  width= '160' > </ColumnDirective>
            <ColumnDirective field= 'Work'  width= '110' > </ColumnDirective>
            <ColumnDirective field= 'Duration' width= '100' > </ColumnDirective>
            </ColumnsDirective>
            <Inject services={[ Toolbar, Edit, Selection ]}/>
        </GanttComponent>;
    }
};
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %}

## Task type

The work, duration and resource unit fields of a task depends upon each other and will change automatically on editing any one of these fields. But we can also set these field’s values as constant using the [`taskType`](../api/gantt/#tasktype) property. `FixedUnit` is the default [`taskType`](../api/gantt/#tasktype). The following values can be set to the [`taskType`](../api/gantt/#tasktype)
 property,

* `FixedDuration` - Duration task field will remain constant while updating resource unit or work field.
* `FixedWork` - Work field will remain constant while updating resource unit or duration fields.
* `FixedUnit` - Resource units will remain constant while updating duration or work field.

{% tab template="gantt/work", compileJsx=true %}

```typescript

export let ProjectResources = [
    { resourceId: 1, resourceName: 'Martin Tamer' },
    { resourceId: 2, resourceName: 'Rose Fuller' },
    { resourceId: 3, resourceName: 'Margaret Buchanan' },
    { resourceId: 4, resourceName: 'Fuller King' },
    { resourceId: 5, resourceName: 'Davolio Fuller' },
    { resourceId: 6, resourceName: 'Van Jack' },
    { resourceId: 7, resourceName: 'Fuller Buchanan' },
    { resourceId: 8, resourceName: 'Jack Davolio' },
    { resourceId: 9, resourceName: 'Tamer Vinet' },
    { resourceId: 10, resourceName: 'Vinet Fuller' },
    { resourceId: 11, resourceName: 'Bergs Anton' },
    { resourceId: 12, resourceName: 'Construction Supervisor' }
];
let data = [
    {
        TaskID: 1,
        TaskName: 'Project initiation',
        StartDate: new Date('03/29/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {
                TaskID: 2, TaskName: 'Identify site location', StartDate: new Date('03/29/2019'), Duration: 2,
                Progress: 30, Work: 16, resources: [{ resourceId: 1, Unit: 70 }, 6]
            },
            {
                TaskID: 3, TaskName: 'Perform soil test', StartDate: new Date('03/29/2019'), Duration: 4,
                resources: [2, 3, 5], Work: 96
            },
            {
                TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('03/29/2019'), Duration: 1,
                Work: 16, resources: [8, { resourceId: 9, Unit: 50 }], Progress: 30
            },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation', StartDate: new Date('03/29/2019'), EndDate: new Date('04/21/2019'),
        subtasks: [
            {
                TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('03/29/2019'),
                Duration: 3, Progress: 30, resources: [{ resourceId: 4, Unit: 50 }], Work: 30
            },
            {
                TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/01/2019'), Duration: 3,
                Work: 48, resources: [4, 8]
            },
            {
                TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/01/2019'),
                Duration: 2, Work: 60, resources: [12, { resourceId: 5, Unit: 70 }]
            }
        ]
    },
    {
        TaskID: 9, TaskName: 'Sign contract', StartDate: new Date('04/01/2019'), Duration: 1,
        Progress: 30, resources: [12], Work: 24
    }
];
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, ColumnsDirective, ColumnDirective, Inject, Edit, Selection, Toolbar } from '@syncfusion/ej2-react-gantt';
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
            resourceInfo: 'resources',
            work: 'Work',
            child: 'subtasks'
        };
        this.resourceFields = {
            id: 'resourceId',
            name: 'resourceName',
            unit: 'Unit'
        };
        this.editSettings = {
            allowAdding: true,
            allowEditing: true,
            allowDeleting: true,
            allowTaskbarEditing: true,
            showDeleteConfirmDialog: true
        };
        this.workUnit = 'Hour';
        this.taskType = 'FixedWork';
        this.toolbar = ['Add', 'Edit', 'Update', 'Delete', 'Cancel', 'ExpandAll', 'CollapseAll'];
    }
    render() {
        return <GanttComponent id='root' dataSource = { data } treeColumnIndex = { 1} allowSelection = { true} allowResizing = { true} highlightWeekends = { true} toolbar = { this.toolbar } editSettings = { this.editSettings } resourceFields = { this.resourceFields } taskFields = { this.taskFields } height = '410px' resources = { ProjectResources } >
            <ColumnsDirective>
            <ColumnDirective field= 'TaskID' visible= {false} > </ColumnDirective>
            <ColumnDirective field= 'TaskName'  headerText= 'Task Name' width= '180' > </ColumnDirective>
            <ColumnDirective field= 'resources' headerText= 'Resources' width= '160' > </ColumnDirective>
            <ColumnDirective  field= 'Work'  width= '110' > </ColumnDirective>
            <ColumnDirective field= 'Duration' width= '100' > </ColumnDirective>
            <ColumnDirective field= 'taskType'  headerText= 'Task Type'  width= '110' > </ColumnDirective>
            </ColumnsDirective>
            <Inject services={[ Toolbar, Edit, Selection ]}/>
        </GanttComponent>;
    }
};
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %}

Following table explains how the work, duration and resource unit fields will gets updated on changing any of the fields

Task Type | Changes in Duration | Changes in work | Changes in Resource Units
-----|-----|-----|-----
Fixed Duration | Work field updates | Resource unit updates| Work field updates
Fixed Work | Resource unit updates. Note: For manually scheduled task work will update.| Duration field updates. Note: For manually scheduled task resource unit updates. |Duration will update. Note: For manually scheduled task work field updates.
Fixed Unit | Work field updates | Duration field updates. Note: For manually scheduled task resource unit updates.| Duration will update. Note: For manually scheduled task work field updates.

>Note: 1. Fixed Unit is the default taskType in Gantt. 2. The above calculations are not applicable for Milestones.