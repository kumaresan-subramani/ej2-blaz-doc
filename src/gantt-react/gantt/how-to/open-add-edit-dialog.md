---
title: "How To"
component: "Gantt"
description: "Learn how to dynamically open the ADD and Edit Dialog's in Gantt component."
---

# Open add/edit dialog dynamically

Gantt add and edit dialogs can be opened dynamically by using [`openAddDialog`](../../api/gantt/#openadddialog) and [`openEditDialog`](../../api/gantt/#openeditdialog) methods. The following code example shows how to open add and dialog on separate button click actions.

{% tab template="gantt/openEditAddDialog", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
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
  public ganttInstance:any;
  public editOptions: EditSettingsModel = {
      allowEditing: true,
      allowAdding:true
  };
  public editHandler(){
    this.ganttInstance.editModule.dialogModule.openEditDialog();
}
 public addHandler(){
    this.ganttInstance.editModule.dialogModule.openAddDialog();
}
    render() {
        return (<div>
        <ButtonComponent  onClick= { this.addHandler.bind(this)}>Open Add Dialog</ButtonComponent>
        <ButtonComponent  onClick= { this.editHandler.bind(this)}>Open Edit Dialog</ButtonComponent>
        <GanttComponent dataSource={data} ref={gantt => this.ganttInstance = gantt} taskFields={this.taskFields} allowSelection={true}
        editSettings={this.editOptions} height = '450px'>
            <Inject services={[Edit, Selection]} />
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

>NOTE: We should select any one of the row in Gantt to open the edit dialog.