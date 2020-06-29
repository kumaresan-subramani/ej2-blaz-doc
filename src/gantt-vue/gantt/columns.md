---
title: "Columns"
component: "Gantt"
description: "Documentation on column reordering, resizing, header templates (custom header content), and column templates (custom cell content) in the Essential JS 2 Gantt component."
---

# Columns

The column displays information from a bound data source, and you can edit the values of column to update the task details through TreeGrid. The operations such as sorting, filtering, and searching can be performed based on column definitions. To display a Gantt column, the [`field`](../api/gantt/column/#field) property should be mapped from the data source to the column.

> If the column [`field`](../api/gantt/column/#field) is not specified in the dataSource, the column values will be empty.

The [`treeColumnIndex`](../api/gantt/#treecolumnindex) property is used to define the expander column in the Gantt component to expand and collapse the child rows.

## Defining columns

Using the [`columns`](../api/gantt/#columns) property, you can define the columns in Gantt. If the columns are not defined, then the default columns will be rendered based on the mapped data source fields in the [`taskFields`](../api/gantt/#taskfields) property. Refer to the following code example for defining the columns in Gantt along with their widths.

{% tab template="gantt/columns" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns = "columns"  :splitterSettings = "splitterSettings"></ejs-gantt>
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
            data:  [
        {
            TaskID: 1,
            TaskName: 'Project Initiation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
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
                { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 }
            ]
        },
    ],
            taskFields: {
             id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
            },
        splitterSettings:{
            columnIndex:2
            },
            height:'450px',
            columns: [
                { field: 'TaskID', width: '150' },
                { field: 'TaskName', width: '250' }
        ]
      };
  },
};
</script>

```

{% endtab %}

## Custom column header

The column header text can be defined using the [`headerText`](../api/gantt/column/#headertext) property, and you can customize the column headers using the [`headerTemplate`](../api/gantt/column/#headertemplate) property.

{% tab template="gantt/columns" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :splitterSettings = "splitterSettings">
            <e-columns>
            <e-column field='TaskName' :headerTemplate='projectName' width=150></e-column>
            <e-column field='StartDate' :headerTemplate='dateTemplate' width=150></e-column>
            <e-column field='Duration' :headerTemplate='durationTemplate' width=150></e-column>
            <e-column field='Progress' :headerTemplate='projectName' width=150></e-column>
            </e-columns>
        </ejs-gantt>
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
         projectName: function () {
            return { template : Vue.component('columnTemplate',{
                template: `<div>
                        <img src="taskname.png" width="20" height="20" class="e-image" />  Task Name
                        </div>`,
                data: function() {
                    return {
                        data: {}
                    }
                },
          })}
      },
        dateTemplate: function () {
            return { template : Vue.component('columnTemplate',{
                template: `<div>
                        <img src="startdate.png" width="20" height="20" class="e-image" />   Start Date
                        </div>`,
                data: function() {
                    return {
                        data: {}
                    }
                },
          })}
       },
        durationTemplate: function () {
          return { template : Vue.component('columnTemplate',{
                template: `<div>
                    <img src="duration.png" width="20" height="20" class="e-image" />   Duration
                    </div>`,
                data: function() {
                    return {
                        data: {}
                    }
                },
          })}
       },
        progressTemplate: function () {
          return { template : Vue.component('columnTemplate',{
                template: `<div>
                    <img src="progress.png" width="20" height="20" class="e-image" />   Progress
                    </div>`,
                data: function() {
                    return {
                        data: {}
                    }
                },
          })}
      },
      taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
        },
        height:'450px',
        splitterSettings:{
            columnIndex:4
            },
            columns: [
            { field: 'TaskName', headerTemplate:  '#projectName', width: '150' },
            { field: 'StartDate', headerTemplate: '#dateTemplate', width: '150' },
            { field: 'Duration',headerTemplate: '#durationTemplate', headerText: 'Duration', width: '150'},
            { field: 'Progress',headerTemplate: '#progressTemplate',  headerText: 'Progress', width: '150' },
        ],
      };
  },
};
</script>

```

{% endtab %}

## Format

To format the cell values based on a specific culture, use the [`columns.format`](../api/gantt/column/#format) property. The Gantt component uses the [`Internationalization`](../../common/internationalization/) library to format `number` and `date` values.

{% tab template="gantt/columns" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns = "columns" :rowHeight = "rowHeight" :splitterSettings = "splitterSettings"></ejs-gantt>
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
            taskFields: {
             id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
            },
            rowHeight:50,
        splitterSettings:{
            columnIndex:3
            },
            height:'450px',
            columns: [
                { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'Progress', headerText: 'Progress', width: '150',format: 'C' },
            { field: 'TaskName', headerText: 'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' }
        ]
      };
  },
};
</script>

```

{% endtab %}

> By default, the number and date values are formatted in `en-US` culture.

### Number formatting

The number or integer values can be formatted using the following format strings.

Format |Description |Remarks
-----|-----
N | Denotes numeric type. | The numeric format is followed by an integer value like N2 or N3, which denotes the number of precisions to be allowed.
C | Denotes currency type. | The currency format is followed by an integer value like C2 or C3, which denotes the number of precisions to be allowed.
P | Denotes percentage type | The percentage format expects the input value to be in the range of 0 to 100. For example, the cell value `0.2` is formatted as `20%`. The percentage format is followed by an integer value like P2, P3, which denotes the number of precisions to be allowed.

### Date formatting

You can format date values either using built-in date format string or custom format string.

For the built-in date format, you can specify the [`columns.format`](../api/gantt/column/#format) property as string (example: `yMd`).

You can also use the custom format string to format the date values. Some of the custom formats and the formatted date values are given in the following table.

Format | Formatted value
-----|-----
{ type:'date', format:'dd/MM/yyyy' } | 04/07/1996
{ type:'date', format:'dd.MM.yyyy' } | 04.07.1996
{ type:'date', skeleton:'short' } | 7/4/96
{ type: 'dateTime', format: 'dd/MM/yyyy hh:mm a' } | 04/07/1996 12:00 AM
{ type: 'dateTime', format: 'MM/dd/yyyy hh:mm:ss a' } | 07/04/1996 12:00:00 AM

{% tab template="gantt/columns" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns = "columns" :rowHeight = "rowHeight" :splitterSettings = "splitterSettings"></ejs-gantt>
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
            taskFields: {
             id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
            },
            rowHeight:50,
        splitterSettings:{
            columnIndex:3
            },
            height:'450px',
            columns: [
                { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150', format: { format: 'dd/MM/yyyy', type: 'date' } },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150',format: 'C' },
        ]
      };
  },
};
</script>

```

{% endtab %}

## Column reordering

The column reordering can be done by dragging a column header from one index to another index within the TreeGrid. To enable reordering, set the [`allowReordering`](../api/gantt/#allowreordering) property to `true`.

To reorder the columns, inject the `Reorder` module in the `provide` section.

{% tab template="gantt/columns" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns = "columns" :allowReordering = 'true' :splitterSettings = "splitterSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Reorder } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
         data: editingData,
         taskFields: {
             id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
            },
            height:'450px',
            splitterSettings:{
            columnIndex:3
            },
        columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ]
      };
  },
  provide: {
      gantt: [Reorder]
  }
};
</script>

```

{% endtab %}

> You can disable the reordering of a particular column by setting the [`columns.allowReordering`](../api/gantt/column/#allowreordering) property to `false`.

## Reorder multiple columns

Multiple columns can be reordered at a time by using the [`reorderColumns`](../api/gantt/#reordercolumns) method.

{% tab template="gantt/columns" %}

```html

<template>
     <div>
        <ejs-button id="reorder" cssClass="e-info" v-on:click.native="change">Reorder</ejs-button>
        <br><br><br>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height="height" :columns = "columns" :allowReordering = 'true' :splitterSettings = "splitterSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Reorder } from "@syncfusion/ej2-vue-gantt";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
Vue.use(ButtonPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            taskFields: {
             id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
            },
            height:'450px',
            splitterSettings:{
            columnIndex:3
            },
        columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ]
      };
  },
  provide: {
      gantt: [Reorder]
  },
  methods: {
      change: function(e){
            var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
            ganttChart.reorderColumns(['TaskID','TaskName'],'Progress');
        }
    },
};
</script>

```

{% endtab %}

## Column resizing

The column width can be resized by clicking and dragging the right edge of the column header. While dragging, the width of the column will be resized immediately. Each column can be auto resized by double-clicking the right edge of the column header to fit the width of that column based on the widest cell content. To resize the column, set the [`columns.allowResizing`](../api/gantt/column/#allowresizing) property to `true`. The following code example shows how to enable the column resize feature in the Gantt component.

To resize the column, inject the `Resize` module in the `provide` section.

{% tab template="gantt/columns" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns = "columns" :splitterSettings = "splitterSettings" :allowResizing = 'true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Resize } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            taskFields: {
             id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
            },
            splitterSettings:{
            columnIndex:4
            },
            height:'450px',
            columns: [
                { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ]
      };
  },
  provide: {
      gantt: [Resize]
  }
};
</script>

```

{% endtab %}

> You can disable resizing for a particular column by setting the [`columns.allowResizing`](../api/gantt/column/#allowresizing) to `false`.

### Defining minimum and maximum column width

The column resizing can be restricted between minimum and maximum widths by defining the [`columns->minWidth`](../api/gantt/column/#minwidth) and [`columns->maxWidth`](../api/gantt/column/#maxwidth) properties.

In the following example, the minimum and maximum widths are defined for the `Duration`, and `Task Name` columns.

{% tab template="gantt/columns" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns = "columns" :splitterSettings="splitterSettings" :allowResizing = 'true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Resize } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            taskFields: {
             id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
            },
            height:'450px',
        columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '200',minWidth: '150' ,maxWidth: '250',},
            { field: 'Duration', headerText: 'Duration', width: '100',minWidth: '50' ,maxWidth: '200' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        splitterSettings:{
            columnIndex:4
          },
          };
  },
  provide: {
      gantt: [Resize]
  }
};
</script>

```

{% endtab %}

## Column template

A column template is used to customize the column’s look. The following code example explains how to define the custom template in Gantt using the [`template`](../api/gantt/column/#template) property.

{% tab template="gantt/columns" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height"  :rowHeight = "rowHeight" :splitterSettings = "splitterSettings" :allowResizing = 'true' :resourceNameMapping="resourceNameMapping" :resourceIDMapping="resourceIDMapping" :resources="resources">
            <e-columns>
            <e-column field='TaskID' headerText='Task ID' textAlign= 'Left' width= '100'></e-column>
                <e-column field='TaskName' headerText= 'Task Name' width= '150'></e-column>
                <e-column field= 'resources' headerText= 'Resources' width= '250' :template= 'cTemplate' ></e-column>
                <e-column field= 'StartDate' headerText='Start Date' width= '150' ></e-column>
                <e-column field= 'Duration' headerText='Duration' width= '150' ></e-column>
                <e-column field= 'Progress' headerText= 'Progress' width= '150' ></e-column>
            </e-columns>
        </ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
import { editingData , editingResources } from './data-source.js';
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
        subtasks: [
            {
                TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 0,
                Progress: 30, resources: [1], info: 'Measure the total property area alloted for construction'
            },
            {
                TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Predecessor: '2',
                resources: [2, 3, 5], info: 'Obtain an engineered soil test of lot where construction is planned.' +
                    'From an engineer or company specializing in soil testing'
            },
            { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 0, Predecessor: '3', Progress: 30, resources: [9, 11], },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project Estimation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {
                TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'),
                Duration: 3, Predecessor: '4', Progress: 30, resources: [4],
                info: 'Develop floor plans and obtain a materials list for estimations'
            },
            {
                TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'),
                Duration: 3, Predecessor: '6', resources: [4, 8], info: ''
            },
            {
                TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'),
                Duration: 0, Predecessor: '7', info: ''
            }
        ]
    },
            ],
            taskFields: {
             id: 'TaskID',
            name: 'TaskName',
            resourceInfo: 'resources',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
            },
        cTemplate: function () {
          return { template : Vue.component('columnTemplate',{
                template: `<div v-if="data.ganttProperties.resourceNames">
                    <img :src="image" style="height:40px;width:40px"/>{{data.ganttProperties.resourceNames}}</div>`,
                    data: function() {
                    return {
                        data: {}
                    }
                },
                computed: {
                    image: function() {
                         return './' + this.data.TaskID + '.png';
                    }
                }
          })}
      },
      rowHeight:50,
        splitterSettings:{
            columnIndex:3
            },
            height:'450px',
        resourceNameMapping: 'resourceName',
        resourceIDMapping: 'resourceId',
        resources: editingResources
      }
  },
};
</script>

```

{% endtab %}

## Column menu

The column menu has options to integrate features like sorting, filtering, and autofit. It will show a menu with the integrated feature when users click the Multiple icon of the column. To enable the column menu, you should set the [`showColumnMenu`](../api/gantt/#showcolumnmenu) property to `true`.

The default items are displayed in the following table:

| Item | Description |
|-----|-----|
| `SortAscending` | Sort the current column in ascending order. |
| `SortDescending` | Sort the current column in descending order. |
| `AutoFit` | Auto fit the current column. |
| `AutoFitAll` | Auto fit all columns. |
| `Filter` | Show the filter option as given in `filterSettings.type` |

{% tab template="gantt/columns" %}

```html
<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns = "columns" :allowFiltering = 'true' :splitterSettings = "splitterSettings" :showColumnMenu = 'true' :allowSorting = 'true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Sort, Filter } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
         data: editingData,
         taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
            },
            height:'450px',
            splitterSettings:{
            position: '100%'
          },
        columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
      };
  },
    provide: {
      gantt: [ Sort, Filter ]
  }
};
</script>

```

{% endtab %}

> You can disable the column menu for a particular column by setting the `columns.showColumnMenu` to `false`.

## Responsive columns

You can toggle the column visibility based on media queries, which are defined in the [`hideAtMedia`](../api/gantt/column/#hideatmedia). The [`hideAtMedia`](../api/gantt/column/#hideatmedia) accepts valid [Media Queries]( http://cssmediaqueries.com/what-are-css-media-queries.html ).

{% tab template="gantt/columns" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns = "columns" :splitterSettings = "splitterSettings" :allowResizing = 'true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Resize } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            taskFields: {
             id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
            },
            height:'450px',
            splitterSettings:{
            columnIndex:4
          },
        columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '200',hideAtMedia: '(min-width: 700px)'},
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '100', hideAtMedia: '(max-width: 500px)'},
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ]
      };
  },
  provide: {
      gantt: [ Resize ]
  }
};
</script>

```

{% endtab %}

## Change tree/expander column

The tree/expander column is a column in the Gantt component, that has icons to expand or collapse the parent records. You can define the tree column index in the Gantt component by using the [`treeColumnIndex`](../api/gantt/#treecolumnindex) property and the default value of this property is `0`. The following code example shows how to use this property.

{% tab template="gantt/columns" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :treeColumnIndex='2' :splitterSettings = "splitterSettings" :allowResizing = 'true'></ejs-gantt>
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
            taskFields: {
             id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks',
            },
            splitterSettings:{
            columnIndex:3
            },
            height:'450px',
      };
  },
};
</script>

```

{% endtab %}