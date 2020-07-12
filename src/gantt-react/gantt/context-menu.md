---
title: "Context Menu"
component: "Gantt"
description: "Learn how to use the context menu and add custom context menu items in the Essential JS 2 Gantt control."
---

# Context menu

The Gantt control allows you to perform quick actions by using context menu. When right-clicking the context menu, the context menu options are shown. To enable this feature, set the [`enableContextMenu`](../api/gantt/#enablecontextmenu) to true. The default context menu options are enabled using the [`editSettings`](../api/gantt/#editsettings) property. The context menu options can be customized using the [`contextMenuItems`](../api/gantt/#contextmenuitems) property.

To use the context menu, inject the [`ContextMenu`](../api/gantt/#contextmenumodule) module into the Gantt component.

The default items are listed in the following table.

Items| Description
----|----
`AutoFit`|  Auto-fits the current column.
`AutoFitAll` | Auto-fits all columns.
`SortAscending` | Sorts the current column in ascending order.
`SortDescending` | Sorts the current column in descending order.
`TaskInformation`|  Edits the current task.
`Add` | Adds a new row to the Gantt.
`Indent` | Indent the selected record to one level.
`Outdent` | Outdent the selected record to one level.
`DeleteTask` | Deletes the current task.
`Save` | Saves the edited task.
`Cancel` | Cancels the edited task.
`DeleteDependency` | Deletes the current dependency task link.
`Convert` | Converts current task to milestone or vice-versa.

{% tab template="gantt/contextmenu", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Edit, Selection, ContextMenu, Sort, Resize, EditSettingsModel } from '@syncfusion/ej2-react-gantt';
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
  public editSettings: EditSettingsModel = {
      allowAdding: true,
      allowEditing: true,
      allowDeleting: true
  };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} editSettings={this.editSettings} allowSorting={true} allowResizing={true} enableContextMenu={true} height = '450px'>
            <Inject services={[Edit, ContextMenu, Selection, Sort, Resize]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Custom context menu items

The custom context menu items can be added by defining the [`contextMenuItems`](../api/gantt/#contextmenuitems) as a collection of [`contextMenuItemModel`](../api/grid/contextMenuItemModel/).
Actions for the customized items can be defined in the [`contextMenuClick`](../api/gantt/#contextmenuclick) event and the visibility of customized items can be defined in the [`contextMenuOpen`](../api/gantt/#contextmenuopen) event.

The following sample shows context menu item for parent rows to expand or collapse child rows.

{% tab template="gantt/customcontextmenu", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Edit, Selection, ContextMenu, Sort, Resize, EditSettingsModel, IGanttData } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    private ganttInstance: any;
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    dependency: 'Predecessor',
    child: 'subtasks'
  };
  public editSettings: EditSettingsModel = {
      allowAdding: true,
      allowEditing: true,
      allowDeleting: true
  };
  public contextMenuItems: any = ['AutoFitAll', 'AutoFit', 'TaskInformation', 'DeleteTask', 'Save', 'Cancel', 'SortAscending', 'SortDescending', 'Add', 'DeleteDependency', 'Convert',
        { text: 'Collapse the Row', target: '.e-content', id: 'collapserow' },
        { text: 'Expand the Row', target: '.e-content', id: 'expandrow' },
        ];
    public contextMenuClick (args: any) {
        let record: IGanttData = args.rowData;
        if (args.item.id === 'collapserow') {
            this.ganttInstance.collapseByID(Number(record.ganttProperties.taskId));
            }
        if (args.item.id === 'expandrow') {
            this.ganttInstance.expandByID(Number(record.ganttProperties.taskId));
            }
        };
    public contextMenuOpen (args: any) {
        let record: IGanttData = args.rowData;
            if (args.type !== 'Header') {
                if (!record.hasChildRecords) {
                    args.hideItems.push('Collapse the Row');
                    args.hideItems.push('Expand the Row');
                } else {
                    if(record.expanded){
                    args.hideItems.push("Expand the Row");
                    } else {
                    args.hideItems.push("Collapse the Row");
                    }
                }
            }
        };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} editSettings={this.editSettings} allowSorting={true} allowResizing={true} enableContextMenu={true} contextMenuItems={this.contextMenuItems} contextMenuClick={this.contextMenuClick.bind(this)} contextMenuOpen={this.contextMenuOpen.bind(this)} ref={gantt => this.ganttInstance = gantt} height = '450px'>
            <Inject services={[Edit, ContextMenu, Selection, Sort, Resize]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> You can show an specific item in context menu for header/content area in the Gantt control by defining the `target` property.