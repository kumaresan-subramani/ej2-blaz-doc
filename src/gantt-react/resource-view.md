---
title: "Resource View"
component: "Gantt Chart"
description: "Learn how to specify the view type for a project in the Essential JS 2 Gantt control."
---

# Resource Breakdown View

The resource breakdown view is used to visualize the tasks assigned to each resource in hierarchy manner. Resources are displayed as parents and all the tasks assigned to each resource are displayed as its child records. It can be initialized by setting the [`viewType`](../api/gantt/#viewtype) property to `ResourceView`.

## Unassigned task

A task not assigned to any one of the resource are termed as unassigned tasks. The unassigned tasks are grouped with a name as `Unassigned Task` and displayed at the bottom of Gantt data collection . It is validated at load time during Gantt record creation by default based on a task `resourceInfo` mapping property in the Gantt chart data source. If the resource is assigned to the unassigned grouped tasks, the task will be moved as child to the respective resource.

## Resource task

A task assigned to one or more resources are termed as resource task and it is added as child task to the respective resource. Already assigned task can also be shared or moved with other resources by adding a resource name to the task or removing resource name from the task by cell or dialog editing.

>Note: Currently, there is no support for predecessor validation in `ResourceView` type.

{% tab template="gantt/resource-view", compileJsx=true %}

```typescript

let resourceCollection: object[] = [
    { resourceId: 1, resourceName: 'Martin Tamer', resourceGroup: 'Planning Team'},
    { resourceId: 2, resourceName: 'Rose Fuller', resourceGroup: 'Testing Team' },
    { resourceId: 3, resourceName: 'Margaret Buchanan', resourceGroup: 'Approval Team' },
    { resourceId: 4, resourceName: 'Fuller King', resourceGroup: 'Development Team' },
    { resourceId: 5, resourceName: 'Davolio Fuller', resourceGroup: 'Approval Team' },
    { resourceId: 6, resourceName: 'Van Jack', resourceGroup: 'Development Team' },
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
                Progress: 30, work: 10, resources: [{ resourceId: 1, resourceUnit: 50 }]
            },
            {
                TaskID: 3, TaskName: 'Perform soil test', StartDate: new Date('03/29/2019'), Duration: 4,
                resources: [{resourceId: 2, resourceUnit: 70}], Progress: 30, work: 20
            },
            {
                TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('03/29/2019'), Duration: 1,
                resources: [{resourceId: 3, resourceUnit: 25}, { resourceId: 1, resourceUnit: 75 }], Progress: 30, work: 10,
            },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation', StartDate: new Date('03/29/2019'), EndDate: new Date('04/21/2019'),
        subtasks: [
            {
                TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('03/29/2019'),
                Duration: 3, Progress: 30, resources: [{ resourceId: 4, resourceUnit: 50 }, {resourceId: 2, resourceUnit: 70}], work: 30
            },
            {
                TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/01/2019'), Duration: 3,
                resources: [{resourceId: 6, resourceUnit: 40}], Progress: 30, work: 40
            },
            {
                TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/01/2019'),
                Duration: 2, resources: [{ resourceId: 5, resourceUnit: 75 }], Progress: 30, work: 60,
            }
        ]
    },
    {
        TaskID: 9, TaskName: 'Sign contract', StartDate: new Date('04/01/2019'), Duration: 1,
        Progress: 30,
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
            child: 'subtasks'
        };
        this.resourceFields = {
            id: 'resourceId',
            name: 'resourceName',
            unit: 'Unit',
            group: 'resourceGroup'
        };
        this.editSettings = {
            allowAdding: true,
            allowEditing: true,
            allowDeleting: true,
            allowTaskbarEditing: true,
            showDeleteConfirmDialog: true
        };
        this.toolbar = ['Add', 'Edit', 'Delete', 'Cancel', 'Update', 'PrevTimeSpan', 'NextTimeSpan', 'ExpandAll', 'CollapseAll', 'Search'];
        this.labelSettings = {
            rightLabel: 'resources'
        };
        this.splitterSettings = {
            columnIndex: 3
        };
        this.projectStartDate = new Date('03/28/2019');
        this.projectEndDate = new Date('05/18/2019');
    }
    render() {
        return <GanttComponent id='root' dataSource = { data } treeColumnIndex = { 1} viewType = 'ResourceView' allowSelection = { true}  allowResizing = { true} highlightWeekends = { true} toolbar = { this.toolbar } editSettings = { this.editSettings } projectStartDate = { this.projectStartDate } projectEndDate = { this.projectEndDate } resourceFields = { this.resourceFields } taskFields = { this.taskFields } labelSettings = { this.labelSettings } splitterSettings = { this.splitterSettings } height = '410px' resources = { resourceCollection } >
            <ColumnsDirective>
            <ColumnDirective field= 'TaskID' visible= {false} > </ColumnDirective>
            <ColumnDirective field= 'TaskName'  headerText= 'Task Name'  width= '180' > </ColumnDirective>
            <ColumnDirective field= 'work'  headerText= 'Work' > </ColumnDirective>
            <ColumnDirective field= 'Progress' > </ColumnDirective>
            <ColumnDirective field= 'resourceGroup'  headerText= 'Group' > </ColumnDirective>
            <ColumnDirective field= 'StartDate' > </ColumnDirective>
            <ColumnDirective field= 'Duration' > </ColumnDirective>
            </ColumnsDirective>
            <Inject services={[ Toolbar, Edit, Selection ]}/>
            </GanttComponent>;
    }
};
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %}