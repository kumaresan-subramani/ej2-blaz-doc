---
title: "Getting Started React"
component: "Gantt"
description: "Learn how to create a Gantt and to enable the features like Editing, filtering, sorting in React"
---

# Getting started

This section explains you the steps required to create a simple Essential JS 2 Gantt in a React application and demonstrates its basic features.

## Dependencies

Following is the list of minimum dependencies required to use the Gantt.

```javascript
|-- @syncfusion/ej2-react-gantt
    |-- @syncfusion/ej2-grids
    |-- @syncfusion/ej2-gantt
    |-- @syncfusion/ej2-layouts
    |-- @syncfusion/ej2-treegrid

```

## Setup for Local Development

You can use [create-react-app](https://github.com/facebookincubator/create-react-app) to setup the applications.
To install create-react-app run the following command.

```sh
npm install -g create-react-app
```

* To setup basic React sample use following commands.

<div class='tsx'>

```sh

create-react-app quickstart --scripts-version=react-scripts-ts

cd quickstart

```

</div>

<div class='jsx'>

```sh

create-react-app quickstart

cd quickstart

```

</div>

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [npmjs.com](https://www.npmjs.com/~syncfusionorg) public registry.
To install Gantt component, use the following command

```sh
npm install @syncfusion/ej2-react-gantt --save
```

## Adding CSS reference

 Add components style as given below in src/App.css.

```css
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-calendars/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-gantt/styles/material.css';
@import '../node_modules/@syncfusion/ej2-grids/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-richtexteditor/styles/material.css';
@import '../node_modules/@syncfusion/ej2-treegrid/styles/material.css';
```

> To refer App.css in the application then import it in the src/App.tsx file.

## Adding Gantt component

Now, you can start adding Gantt component in the application. For getting started, add the Gantt component in `src/App.tsx` file using following code.

Place the following gantt code in the src/App.tsx.

{% tab compileJsx=true%}

```typescript
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import './App.css';

const GanttData: object[] = [
    {
        TaskID: 1,
        TaskName: 'Project Initiation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
            { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
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
];
class App extends React.Component {
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks',
    };
    public render() {
        return (
            <GanttComponent dataSource={GanttData} height="450px" taskFields={this.taskFields}/>
        );
    }
}
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Mapping task fields

The data source fields that are required to render the tasks are mapped to the Gantt component using the [`taskFields`](../api/gantt/#taskfields) property.

{% tab compileJsx=true%}

```typescript
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import './App.css';

const GanttData: object[] = [
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
    ];
class App extends React.Component {
  public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks',
    };
  public render() {
    return (
     <GanttComponent dataSource={GanttData} height="450px" taskFields={this.taskFields}/>
        );
    }
}
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Defining columns

Gantt has an option to define columns as an array. You can customize the Gantt columns using the following properties:

* `field`: Maps the data source fields to the columns.
* `headerText`: Changes the title of columns.
* `textAlign`: Changes the alignment of columns. By default, columns will be left aligned. To change the columns to right align, set `textAlign` to right.
* `format`: Formats the number and date values to standard or custom formats. Here, it is defined for the conversion of numeric values to currency.

{% tab compileJsx=true%}

```typescript
import { GanttComponent, ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import './App.css';

const GanttData: object[] = [
    {
        TaskID: 1,
        TaskName: 'Project Initiation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
            { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
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
];
class App extends React.Component {
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks',
    };
    public render() {
        return (
            <GanttComponent dataSource={GanttData} height="450px" taskFields={this.taskFields}>
                <ColumnsDirective>
                    <ColumnDirective field='TaskID' width='50' />
                    <ColumnDirective field='TaskName' headerText='Job Name'/>
                    <ColumnDirective field='StartDate'/>
                    <ColumnDirective field='Duration'/>
                </ColumnsDirective>
            </GanttComponent>
        );
    }
}
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Module Injection

Gantt component features are segregated into individual feature-wise modules.
In order to use a particular feature, you need to inject its feature service in the App.
In the current application, we are going to use editing, sorting and filtering  feature of Gantt.
Please find relevant feature service name and description as follows.

* [`Edit`](../api/gantt/#editmodule): Inject this module to use the editing feature.
* [`Filter`](../api/gantt/#filtermodule): Inject this module to use the filtering feature.
* [`Sort`](../api/gantt/#sortmodule): Inject this module to use the sorting feature.

These modules should be injected into the gantt using the Inject directive.

## Enable editing

The editing feature enables you to edit the tasks in the Gantt component. It can be enabled by using the [`editSettings.allowEditing`](../api/gantt/editSettings/#allowediting) and [`editSettings.allowTaskbarEditing`](../api/gantt/editSettings/#allowtaskbarediting) properties.

The following editing options are available to update the tasks in Gantt,

* Cell
* Dialog
* Taskbar
* Connector line

### Cell editing

Modify the task details through cell editing by setting the edit mode to `Auto`. Inject the [`Edit`](../api/gantt/#editmodule) module as follows. If the [`Edit`](../api/gantt/#editmodule) module is not injected, you cannot edit the cell when a grid cell is clicked.

{% tab template="gantt/celledit", compileJsx=true %}

```typescript
import { GanttComponent, Inject, Edit, Selection } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { data } from './datasource';
class App extends React.Component<{}, {}> {
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks',
  };
  public editSettings: any = {
    allowEditing: true,
    mode: 'Auto',
  };
  public  render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} allowSelection={true}
        editSettings={this.editSettings} height = '400px'>
           <Inject services={[Edit, Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

`Note:` When the edit mode is set to `Auto`, you can change the cells to editable mode by double-clicking anywhere at the TreeGrid and edit the task details in the edit dialog by double-clicking anywhere at the chart.

### Dialog editing

Modify the task details through dialog by setting the edit mode to `Dialog`. Inject the [`Edit`](../api/gantt/#editmodule) module as follows. If the [`Edit`](../api/gantt/#editmodule) module is not injected, you cannot edit the task details through the edit dialog.

{% tab template="gantt/dialogedit", compileJsx=true %}

```typescript
import { GanttComponent, Inject, Edit, Selection } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { data } from './datasource';
class App extends React.Component<{}, {}> {
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
  };
  public editSettings: any = {
    allowEditing: true,
    mode: 'Dialog'
  };
  public  render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} allowSelection={true}
        editSettings={this.editSettings} height = '400px'>
         <Inject services={[Edit, Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

`Note:` In dialog editing mode, the edit dialog will appear while performing double-click action in both TreeGrid and chart sides.

### Taskbar editing

Modify the task details through user interaction such as resizing and dragging the taskbar by enabling the [`allowTaskbarEditing`](../api/gantt/editSettings/#allowtaskbarediting) property.
Inject the [`Edit`](../api/gantt/#editmodule) module as follows. If the [`Edit`](../api/gantt/#editmodule) module is not injected, you cannot edit the task details while dragging the taskbar.

{% tab template="gantt/taskbaredit", compileJsx=true %}

```typescript
import { GanttComponent, Inject, Edit } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { data } from './datasource';
class App extends React.Component<{}, {}> {
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
  };
  public editSettings: any = {
    allowTaskbarEditing: true
  };
  public  render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        editSettings={this.editSettings}  height = '400px'>
            <Inject services={[Edit]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Dependency editing

Modify the task dependencies using mouse interactions by enabling the [`allowTaskbarEditing`](../api/gantt/editSettings/#allowtaskbarediting)  property along with mapping the task dependency data source field to the [`dependency`](../api/gantt/taskFields/#dependency) property.

{% tab template="gantt/dependencyedit", compileJsx=true %}

```typescript
import { GanttComponent, Inject, Edit } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

const data: object[] = [
        {
            TaskID: 1,
            TaskName: 'Project Initiation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50,Predecessor:'2FS'  },
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
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50,Predecessor:'7SS' }
            ]
        },
    ];
class App extends React.Component<{}, {}> {
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks',
    dependency: 'Predecessor'
  };
  public editSettings: any = {
    allowTaskbarEditing: true
  };
  public  render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        editSettings={this.editSettings} height = '400px'>
            <Inject services={[Edit]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Enabling predecessors or task relationships

Predecessor or task dependency in the Gantt component is used to depict the relationship between the tasks.

* Start to Start (SS): You cannot start a task until the dependent task starts.
* Start to Finish (SF): You cannot finish a task until the dependent task finishes.
* Finish to Start (FS): You cannot start a task until the dependent task completes.
* Finish to Finish (FF): You cannot finish a task until the dependent task completes.
You can show the relationship in tasks by using the [`dependency`](../api/gantt/taskFields/#dependency) property as shown in the following code example.

{% tab template="gantt/dependency", compileJsx=true %}

```typescript
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

const data: object[] = [
        {
            TaskID: 1,
            TaskName: 'Project Initiation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50,Predecessor:'2FS'  },
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
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50,Predecessor:'7SS' }
            ]
        },
    ];
class App extends React.Component<{}, {}> {
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    dependency: 'Predecessor',
    child: 'subtasks'
  };
  public  render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} height = '400px'/>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Assigning resources

You can display and assign the resource for each task in the Gantt component.
Create a collection of JSON object, which contains ID and name of the resource and assign it to the [`resources`](../api/gantt/#resources) property.
Map the resource ID and name with [`resourceIDMapping`](../api/gantt/#resourceidmapping) and [`resourceNameMapping`](../api/gantt/#resourcenamemapping) properties, respectively.

{% tab template="gantt/resource", compileJsx=true %}

```typescript

const projectResources: object[] = [
    { resourceId: 1, resourceName: 'Martin Tamer' },
    { resourceId: 2, resourceName: 'Rose Fuller' },
    { resourceId: 3, resourceName: 'Margaret Buchanan' },
    { resourceId: 4, resourceName: 'Fuller King' }
];
const data: object[] = [
        {
            TaskID: 1,
            TaskName: 'Project Initiation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50,resources: [2, 3] },
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50,resources: [2] },
                { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50,resources: [1] }
            ]
        },
        {
            TaskID: 5,
            TaskName: 'Project Estimation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            subtasks: [
                { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
                { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50,resources: [1, 3, 5] },
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 }
            ]
        },
    ];
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

class App extends React.Component<{}, {}> {
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks',
        resourceInfo: 'resources'
};
public labelSettings: any = {
  rightLabel: 'resources'
};
publi resourceFields: any = {
  id: 'resourceId',
  name: 'resourceName',
};

public  render() {
      return <GanttComponent dataSource={data} taskFields={this.taskFields} labelSettings={this.labelSettings}
      resourceFields={resourceFields} resources={projectResources} height = '450px'/>
  }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Enable filtering

The filtering feature enables you to view the reduced amount of records based on filter criteria. Gantt provides the menu filtering support for each column. It can be enabled by setting the [`allowFiltering`](../api/gantt/#allowfiltering) property to true along with injecting the [`Filter`](../api/gantt/#filtermodule) module as shown in the following code example. Filtering feature can also be customized using the [`filterSettings`](../api/gantt/filterSettings/) property.

{% tab template="gantt/filtering", compileJsx=true %}

```typescript
import { GanttComponent, Inject, Filter } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
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
    public render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
         allowFiltering={true} height = '400px'>
            <Inject services={[Filter]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Enable sorting

The sorting feature enables you to order the records. It can be enabled by setting the [`allowSorting`](../api/gantt/#allowsorting) property to `true`. Inject the [`Sort`](../api/gantt/#sortmodule) module as follows. If the [`Sort`](../api/gantt/#sortmodule) module is not injected, you cannot sort the records when a header is clicked. The sorting feature can be customized using the [`sortSettings`](../api/gantt/sortSettings/) property.

{% tab template="gantt/sorting", compileJsx=true %}

```typescript
import { GanttComponent, Inject, Sort } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { data } from './datasource';
class App extends React.Component<{}, {}> {
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks'
    };
    public render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
          allowSorting={true} height='400px'>
        <Inject services={[Sort]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Run the application

The [create-react-app](https://github.com/facebookincubator/create-react-app) will pre-configure the project to compile and run the application in browser. Use the following command to run the application.

```sh

npm start

```

Output will be appears as follows.

{% tab template="gantt/run", compileJsx=true %}

```typescript
const projectResources: object[] = [
    { resourceId: 1, resourceName: 'Project Manager' },
    { resourceId: 2, resourceName: 'Software Analyst' },
    { resourceId: 3, resourceName: 'Developer' },
    { resourceId: 4, resourceName: 'Testing Engineer' }
];
const data: object[] = [
    {
        TaskID: 1,
        TaskName: 'Project Initiation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50, resources: [2, 3] },
            { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50, resources: [2] },
            { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4, Predecessor: '3FS', Progress: 50, resources: [1] },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project Estimation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
            { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50, resources: [1, 3, 5] },
            { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 3, Predecessor: '7SS', Progress: 50 }
        ]
    },
];
import { GanttComponent, Inject, Edit, Filter, Sort } from '@syncfusion/ej2-react-gantt';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

class App extends React.Component<{}, {}> {
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks',
        dependency: 'Predecessor',
        resourceInfo: 'resources'
    };
    public labelSettings: any = {
        rightLabel: 'resources'
    };
    public editSettings: any = {
        allowEditing: true,
        editMode: 'Auto',
        allowTaskbarEditing: true
    };
  public render() {
        return <GanttComponent dataSource={data} allowFiltering={true} allowSorting={true} taskFields={this.taskFields} editSettings={this.editSettings} labelSettings={this.labelSettings}
            resourceNameMapping='resourceName' resourceIDMapping='resourceId' resources={projectResources} height='400px'>
            <Inject services={[Edit, Filter, Sort]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}