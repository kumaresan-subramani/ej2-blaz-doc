---
title: "Data Binding"
component: "Gantt"
description: "Learn how to bind local and remote data in the Essential JS 2 Gantt Component."
---

# Data Binding

The Gantt component uses `DataManager` for binding the data source, which supports both RESTful JSON data services and local JavaScript object array. The [`dataSource`](../api/gantt/#datasource) property can be assigned either with the instance of DataManager or JavaScript object array collection. The Gantt component supports binding two types of data:
* Local data
* Remote data

## Local data

To bind local data to Gantt, you can assign a JavaScript object array to the [`dataSource`](../api/gantt/#datasource) property. The local data source can also be provided as an instance of the `DataManager`.

In local data binding, the data source for rendering the Gantt component is retrieved from the same application locally.

The following are the two types of data binding possible with the Gantt component:

* Hierarchical data binding.
* Self-referential data binding (Flat data).

### Hierarchical data binding

The [`child`](../api/gantt/taskFields/#child) property is used to map the child records in hierarchical data.

The following code example shows how to bind the hierarchical local data into the Gantt component.

{% tab template="gantt/databinding", compileJsx=true %}

```typescript
let HierarchyData: Object[] = [
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
        }
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
    render() {
        return <GanttComponent dataSource={HierarchyData} taskFields={this.taskFields} height = '400px'>
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Self-referential data binding (Flat data)

The Gantt component can be bound with self-referential data by mapping the data source field values to the [`id`](../api/gantt/taskFields/#id) and [`parentID`](../api/gantt/taskFields/#parentid) properties.

* ID field: This field contains unique values used to identify each individual task and it is mapped to the [`id`](../api/gantt/taskFields/#id) property.
* Parent ID field: This field contains values that indicate parent tasks and it is mapped to the [`parentID`](../api/gantt/taskFields/#parentid) property.

{% tab template="gantt/databinding", compileJsx=true %}

```typescript

let SelfReferenceData: Object[]  = [
            { TaskID: 1,TaskName: 'Project Initiation',StartDate: new Date('04/02/2019'),EndDate: new Date('04/21/2019')},
            { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50,ParentId:1 },
            { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50, ParentId:1   },
            { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50,ParentId:1 },
            { TaskID: 5, TaskName: 'Project Estimation',StartDate: new Date('04/02/2019'),EndDate: new Date('04/21/2019')},
            { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50, ParentId:5  },
            { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50,ParentId:5  },
            { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50, ParentId:5  }
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
    parentID: 'ParentId'
  };
    render() {
        return <GanttComponent dataSource={SelfReferenceData} taskFields={this.taskFields} height = '450px'>
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Remote data

To bind remote data to the Gantt component, assign service data as an instance of `DataManager` to the [`dataSource`](../api/gantt/#datasource) property.

{% tab template="gantt/databinding", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
import { DataManager, WebApiAdaptor } from '@syncfusion/ej2-data';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskId',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    dependency: 'Predecessor',
    child: 'SubTasks'
  };
  public dataSource: DataManager = new DataManager({
    url: 'https://ej2services.syncfusion.com/production/web-services/api/GanttData',
    adaptor: new WebApiAdaptor,
    crossDomain: true
  });
    render() {
        return <GanttComponent dataSource={this.dataSource} taskFields={this.taskFields} height = '450px'>
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}