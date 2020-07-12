---
title: "How To"
component: "Gantt"
description: "Learn how to add Custom Fields in the General Tab in Add/Edit in the JS 2 Gantt component."
---

# Add Custom Fields in the General Tab in Add/Edit Dialog

Generally in Gantt, Custom fields are displayed in the Custom Tab of the Add/Edit dialogs. However, they can be included in the General Tab of Add/Edit Dialog Box using `actionBegin` and `actionComplete` events. These events are used to append the custom field to the dialog box. The following code snippets demonstrate the solution.

{% tab template="gantt/how-to-customfield", compileJsx=true %}

```typescript

import { GanttComponent, Inject, Edit, Selection, ColumnsDirective, ColumnDirective, AddDialogFieldsDirective, EditDialogFieldsDirective, EditDialogFieldDirective, AddDialogFieldDirective, Toolbar } from '@syncfusion/ej2-react-gantt';
import { CheckBox } from "@syncfusion/ej2-buttons";
import { TextBox, NumericTextBox, MaskedTextBox } from "@syncfusion/ej2-inputs";
import { DatePicker, DateTimePicker } from "@syncfusion/ej2-calendars";
import { DropDownList } from "@syncfusion/ej2-dropdowns";
import * as React from 'react';
import * as ReactDOM from 'react-dom';
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
            child: 'subtasks'
        };
        this.editOptions = {
        allowAdding: true,
        allowEditing: true,
        allowDeleting: true,
        mode: "Dialog"
        };
        this.toolbarOptions = ['Add', 'Edit', 'Delete', 'Cancel', 'Update', 'ExpandAll', 'CollapseAll', 'Search'];
    };
    public divElement: any;
    public inputs = {
       booleanedit: CheckBox,
       dropdownedit: DropDownList,
       datepickeredit: DatePicker,
       datetimepickeredit: DateTimePicker,
       maskededit: MaskedTextBox,
       numericedit: NumericTextBox,
       stringedit: TextBox
     };
    actionBegin(args) {
        if (args.requestType === "beforeOpenEditDialog" || args.requestType === "beforeOpenAddDialog" ) {
          var column = this.ganttInstance.columnByField["CustomField"];
          this.divElement = this.ganttInstance.createElement("div", {
            className: "e-edit-form-column"
          });
          var inputElement: any;
          inputElement = this.ganttInstance.createElement("input", {
            attrs: {
              type: "text",
              id: this.ganttInstance.controlId + "" + column.field,
              name: column.field,
              title: column.field
            }
          });
          this.divElement.appendChild(inputElement);
          var input = {
            enabled: true,
            floatLabelType: "Auto",
            placeholder: "CustomField",
            value: args.rowData.CustomField
          };
          var inputObj = new this.inputs[column.editType](input);
          inputObj.appendTo(inputElement);
        }
    };
    actionComplete(args) {
        if (args.requestType === "openEditDialog" || args.requestType === "openAddDialog") {
          var generalTab = document.getElementById(
            this.ganttInstance.controlId + "GeneralTabContainer"
          );
          generalTab.appendChild(this.divElement);
        }
      };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} allowSelection={true} editSettings={this.editOptions}
        toolbar={this.toolbarOptions} actionBegin={this.actionBegin.bind(this)} actionComplete={this.actionComplete.bind(this)} ref={gantt => this.ganttInstance = gantt} height='400px'>
         <ColumnsDirective>
                <ColumnDirective field='TaskID' width='150'></ColumnDirective>
                <ColumnDirective field='TaskName' width='250'></ColumnDirective>
                <ColumnDirective field='StartDate' width='250'></ColumnDirective>
                <ColumnDirective field='EndDate' width='250'></ColumnDirective>
                <ColumnDirective field='Duration' width='250'></ColumnDirective>
                <ColumnDirective field='Progress' width='250'></ColumnDirective>
                <ColumnDirective field='CustomField' width='250'></ColumnDirective>
          </ColumnsDirective>
           <AddDialogFieldsDirective>
            <AddDialogFieldDirective type='General' headerText='General'></AddDialogFieldDirective>
            <AddDialogFieldDirective type='Dependency'></AddDialogFieldDirective>
            <AddDialogFieldDirective type='Resources'></AddDialogFieldDirective>
            <AddDialogFieldDirective type='Notes'></AddDialogFieldDirective>
        </AddDialogFieldsDirective>
           <EditDialogFieldsDirective>
              <EditDialogFieldDirective type='General' headerText='General'></EditDialogFieldDirective>
              <EditDialogFieldDirective type='Dependency'></EditDialogFieldDirective>
              <EditDialogFieldDirective type='Resources'></EditDialogFieldDirective>
              <EditDialogFieldDirective type='Notes'></EditDialogFieldDirective>
            </EditDialogFieldsDirective>
         <Inject services={[Edit, Selection, Toolbar]}/>
        </GanttComponent>;
    }
};
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %}