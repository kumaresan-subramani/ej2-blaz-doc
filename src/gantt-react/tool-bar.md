---
title: "Toolbar"
component: "Gantt"
description: "Learn how to use the toolbar and add custom toolbar items in the Essential JS 2 Gantt component"
---

# Toolbar

The Gantt component provides the toolbar support to handle Gantt actions. The [`toolbar`](../api/gantt/#toolbar) property accepts the collection of built-in toolbar items and `ItemModel` objects for custom toolbar items.

## Built-in toolbar items

Built-in toolbar items execute standard actions of the Gantt component, and these items can be added to toolbar by defining the [`toolbar`](../api/gantt/#toolbar) as a collection of built-in items. It renders the button with icon and text.

The following table shows built-in toolbar items and its actions.

| Built-in Toolbar Items | Actions |
|------------------------|---------|
| Add | Adds a new record. |
| Cancel | Cancels the edit state. |
| CollapseAll | Collapses all the rows. |
| Delete | Deletes the selected record. |
| Edit | Edits the selected record. |
| Indent | Indent the selected record to one level.|
| Outdent | Outdent the elected record to one level.|
| ExpandAll | Expands all the rows. |
| NextTimeSpan | Navigate the Gantt timeline to next time span. |
| PrevTimeSpan | Navigate the Gantt timeline to previous time span. |
| Search | Searches the records by the given key. |
| Update | Updates the edited record. |

{% tab template="gantt/toolbar", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Edit, Filter, EditSettingsModel, Selection, Toolbar, ToolbarItem }from '@syncfusion/ej2-react-gantt';
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
      allowAdding: true,
      allowEditing: true,
      allowDeleting: true
  };
  public toolbarOptions: ToolbarItem[] = ['Add','Edit','Delete','Cancel','Update','PrevTimeSpan','NextTimeSpan','ExpandAll','CollapseAll','Search','Indent','Outdent'];
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} allowSelection={true}
        editSettings={this.editOptions} toolbar={this.toolbarOptions} height = '450px'>
           <Inject services={[Edit, Selection, Toolbar, Filter]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> * The [`toolbar`](../api/gantt/#toolbar) has options to define both built-in and custom toolbar items.

## Custom toolbar items

Custom toolbar items can be added to the toolbar by defining the [`toolbar`](../api/gantt/#toolbar) property as a collection of `ItemModels`.
Actions for this customized toolbar items are defined in the [`toolbarClick`](../api/gantt/#toolbarclick) event.

By default, the custom toolbar items are at left position. You can change the position by using the `align` property. In the following sample, the `Quick Filter` toolbar item is positioned at right.

{% tab template="gantt/customtoolbar", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Filter, Toolbar } from '@syncfusion/ej2-react-gantt';
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
  public toolbarOptions: any[] = [{text: 'Quick Filter', tooltipText: 'Quick Filter', id: 'toolbarfilter', align:'Right', prefixIcon: 'e-quickfilter' }];
  public toolbarClick(): void {
              this.ganttInstance.filterByColumn('TaskName', 'startswith', 'Identify');
        };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        allowFiltering={true}  toolbar={this.toolbarOptions} toolbarClick={this.toolbarClick.bind(this)} height = '450px' ref={gantt => this.ganttInstance = gantt}>
         <Inject services={[Filter, Toolbar]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> * The [`toolbar`](../api/gantt/#toolbar) has options to define both built-in and custom toolbar items.
> * If a toolbar item does not match the built-in items, it will be treated as a custom toolbar item.

## Built-in and custom items in toolbar

The Gantt component has an option to use both built-in and custom toolbar items at the same time.

In the following example, the `ExpandAll` and `CollapseAll` are built-in toolbar items and `Test` is the custom toolbar item.

{% tab template="gantt/defaultandCustomtoolbar", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { GanttComponent, Inject, Toolbar } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    public taskFields: any = {
    id: 'TaskID',
    name: 'TaskName',
    startDate: 'StartDate',
    duration: 'Duration',
    progress: 'Progress',
    child: 'subtasks',
    dependency: 'Predecessor',
  };
  public toolbarOptions: any[] = ['ExpandAll', 'CollapseAll', { text: 'Test', tooltipText: 'Test',id: 'Test' }];
  public toolbarClick(args: ClickEventArgs): void {
       if (args.item.text === 'Test') {
        alert("Custom toolbar Click...");
      }
    };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}  
        toolbar={this.toolbarOptions} toolbarClick={this.toolbarClick.bind(this)} height = '450px'>
            <Inject services={[Toolbar]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Enable/disable toolbar items

You can enable or disable the toolbar items by using the `enableItems` method.

{% tab template="gantt/enabledisableToolbar", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { GanttComponent, Inject, Toolbar, Filter, ColumnsDirective, ColumnDirective} from '@syncfusion/ej2-react-gantt';
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
  public toolbarOptions: any[] = ['QuickFilter', 'ClearFilter'];
  public enable() {
      this.ganttInstance.toolbarModule.enableItems([this.ganttInstance.element.id + '_QuickFilter', this.ganttInstance.element.id + '_ClearFilter'], true);// enable toolbar items.
   };
   public disable() {
      this.ganttInstance.toolbarModule.enableItems([this.ganttInstance.element.id + '_QuickFilter', this.ganttInstance.element.id + '_ClearFilter'], false);// disable toolbar items.
    };
    public toolbarClick(args: ClickEventArgs): void {
        if (args.item.text === 'QuickFilter') {
           this.ganttInstance.filterByColumn('TaskName', 'startswith', 'Identify');
        }
        if (args.item.text === 'ClearFilter') {
           this.ganttInstance.clearFiltering();
        }
    };

    render() {
        return (<div>
        <ButtonComponent  onClick= { this.enable.bind(this)}>Enable</ButtonComponent>
        <ButtonComponent  onClick= { this.disable.bind(this)}>Disable</ButtonComponent>
        <GanttComponent dataSource={data} taskFields={this.taskFields} toolbar={this.toolbarOptions}
         toolbarClick={this.toolbarClick.bind(this)} allowFiltering={true} height = '450px'
         ref={gantt => this.ganttInstance = gantt}>
            <Inject services={[Toolbar, Filter]} />
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Add input elements in Toolbar

In Gantt toolbar, it is possible to add EJ2 editor elements like numeric text box, dropdown list and date picker components. The following code snippets explains how to add EJ2 editors in Gantt toolbar.

{% tab template="gantt/customToolbarItems", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { NumericTextBox} from '@syncfusion/ej2-inputs';
import { GanttComponent, Inject, Toolbar } from '@syncfusion/ej2-react-gantt';
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
  public toolbarOptions: any[] = [ { type: 'Input',template:new NumericTextBox({ format: 'c2', value:1 })} ];
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}  
        toolbar={this.toolbarOptions} height = '400px'>
            <Inject services={[Toolbar]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}
