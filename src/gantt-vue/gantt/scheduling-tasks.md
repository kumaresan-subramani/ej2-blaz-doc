---
title: "Scheduling Tasks"
component: "Gantt"
description: "Learn about duration values in the Essential JS 2 Gantt component."
---

# Scheduling tasks

## Duration units

In the Gantt component, the tasks’ duration value can be measured by the following duration units:

* Day
* Hour
* Minute

In the Gantt component, you can define the duration unit for whole project by using the [`durationUnit`](../api/gantt/#durationunit) property. When you define a value for this property, the duration unit will be applied for all tasks that do not have duration unit value.

Each task in the project can be defined with different duration units and the duration unit of a task can be defined by the following ways:
* Using the [`taskFields.durationUnit`](../api/gantt/taskFields/#durationunit) property, you can map the duration unit of data source field.
* Defining the duration unit value along with duration field in the data source.

### Mapping the duration unit field

The following code snippet explains mapping the data source field of the duration unit to the Gantt component using the [`taskFields.durationUnit`](../api/gantt/taskFields/#durationunit) property.

{% tab template="gantt/scheduling-tasks" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :splitterSettings = "splitterSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            height:'450px',
            taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            durationUnit:'DurationUnit',
            child: 'subtasks'
        },
        splitterSettings:{
            columnIndex:4
            }
      };
  },
};
</script>

```

{% endtab %}

> NOTE
The default value of the [`durationUnit`](../api/gantt/#durationunit) property is `day`.

### Defining duration unit along with duration field

A duration unit for a task can be defined along with duration value, the following code snippet explains the duration unit for a task along with duration value.

{% tab template="gantt/scheduling-tasks" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :splitterSettings = "splitterSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: [
        {
            TaskID: 1,
            TaskName: 'Project Initiation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            isParent:true,
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: '3days', DurationUnit:'day', Progress: 50,isParent:false },
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: '12hours',DurationUnit:'hour', Progress: 70, resources: [2, 3, 5],isParent:false   },
                { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: '1800minutes',DurationUnit:'minute', Predecessor:"2FS", Progress: 80,isParent:false  },
            ]
        },
        {
            TaskID: 5,
            TaskName: 'Project Estimation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            isParent:true,
            subtasks: [
                { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: '12hours', DurationUnit:'hour', Progress: 50, resources: [4],isParent:false  },
                { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: '3days', Progress: 50, DurationUnit:'day', resources: [4, 8],isParent:false  },
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: '480minutes',Predecessor:"6SS", DurationUnit:'minute', Progress: 70, resources: [12, 5],isParent:false  }
            ]
        },
    ],
    height:'450px',
    taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        splitterSettings:{
            columnIndex:4
            }
      };
  },
};
</script>

```

{% endtab %}

>NOTE:
The edit type of the duration column in Gantt is string to edit the duration field along with duration units.

## Unscheduled tasks

Unscheduled tasks are planned for a project without any definite schedule dates. The Gantt component supports rendering the unscheduled tasks. You can create or update the tasks with anyone of start date, end date, and duration values or none. You can enable or disable the unscheduled tasks by using the [`allowUnscheduledTasks`](../api/gantt/#allowunscheduledtasks) property.

## Unscheduled task types

The following images represent the various types of unscheduled tasks in Gantt.

### Start date only

![Alt text](images/startDate-only.png)

### End date only

![Alt text](images/endDate-only.png)

### Duration only

![Alt text](images/duration-only.png)

### Milestone

A milestone is a task that has no start and end dates, but it has a duration value of zero. It is represented as follows.

![Alt text](images/milestone.png)

### Define unscheduled tasks in data source

You can define the various types of unscheduled tasks in the data source as follows.

{% tab template= "gantt/scheduling-tasks" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :editSettings= "editSettings" :allowUnscheduledTasks='true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit } from "@syncfusion/ej2-vue-gantt";
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: [
        {
            TaskID: 1,
            TaskName: 'Project Initiation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            isParent:true,
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', Duration: 3, Progress: 50},
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Progress: 50   },
                { TaskID: 4, TaskName: 'Soil test approval', EndDate: new Date('04/08/2019'), Progress: 50 },
            ]
        },
        {
            TaskID: 5,
            TaskName: 'Project Estimation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            isParent:true,
            subtasks: [
                { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Progress: 50, resources: [4],isParent:false  },
                { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Progress: 50  },
                { TaskID: 8, TaskName: 'Estimation approval',Duration: 0,Progress: 50}
            ]
        },
    ],
            height: '450px',
            taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            endDate:'EndDate',
            duration:'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        editSettings: {
            allowEditing:true,
        }
    };
  },
  provide: {
      gantt: [ Edit ]
  }
};
</script>

```

{% endtab %}

> NOTE
> If the [`allowUnscheduledTasks`](../api/gantt/#allowunscheduledtasks) property is set to false, then the Gantt control automatically calculates the scheduled date values with a default value of duration 1 and the project start date is considered as the start date for the task.

## Working time range

In the Gantt component, working hours in a day for a project can be defined by using the [`dayWorkingTime`](../api/gantt/#dayworkingtime) property. Based on the working hours, automatic date scheduling and duration validations for a task are performed.

The following code snippet explains how to define the working time range for the project in Gantt.

{% tab template="gantt/scheduling-tasks" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :highlightWeekends='true' :splitterSettings= "splitterSettings" :dayWorkingTime="dayWorkingTime" :timelineSettings="timelineSettings"  :editSettings= "editSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit, DayMarkers } from "@syncfusion/ej2-vue-gantt";
import { editingData } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            height: '450px',
            taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        editSettings:{
            allowTaskbarEditing:true
            },
            splitterSettings: {
                columnIndex: 1
                },
            dayWorkingTime: [
                {from: 9,
                to: 18 }
             ],
             timelineSettings:{
           timelineViewMode:'Day'
           }
           };
  },
  provide: {
      gantt: [ DayMarkers, Edit ]
  },
};
</script>

```

{% endtab %}

> NOTE
>* Individual tasks can lie between any time within the defined working time range of the project.
>* The [`dayWorkingTime`](../api/gantt/#dayworkingtime) property is used to define the working time for the whole project.

## Weekend / Non-working days

Non-working days/weekend are used to represent the non-productive days in a project. You can define the non-working days in a week using the [`workWeek`](../api/gantt/#workweek) property in Gantt.

{% tab template="gantt/scheduling-tasks" %}

```html

<template>
     <div>
        <ejs-gantt id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :highlightWeekends='true' :workWeek="workWeek"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, DayMarkers } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            height: '450px',
                taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                child: 'subtasks'
            },
            workWeek: ["Sunday","Monday","Tuesday","Wednesday","Thursday"],
            };
    },
    provide: {
      gantt: [ DayMarkers ]
    }  
};
</script>

```

{% endtab %}

> By default, Saturdays and Sundays are considered as non-working days/weekend in a project.
> In the Gantt component, you can make weekend as working day by setting the [`includeWeekend`](../api/gantt/#includeweekend) property to `true`.