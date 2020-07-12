---
title: "How To"
component: "Gantt"
description: "Learn how to copy and paste records in Gantt control."
---

# Copy and Paste records in Gantt

You can copy and paste a record in the Gantt chart by using the `addRecord` method and `custom context menu`. It is also possible to copy and paste the parent record with multiple hierarchical child records on the required position.

{% tab template="gantt/how-to-copypaste", compileJsx=true %}

```typescript

import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, Edit, Selection, ContextMenu } from '@syncfusion/ej2-react-gantt';
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
            dependency: 'Predecessor',
            child: 'subtasks'
        };
        this.editSettings = {
            allowAdding: true,
            allowEditing: true,
            allowDeleting: true
        };
        this.contextMenuItems = [{ text: 'Copy', target: '.e-content', id: 'copy' },
            { text: 'Paste', target: '.e-content', id: 'paste' }
        ];
    };
    public copiedRecord: any;
    contextMenuClick(args) {
        if (args.item.id === 'copy') {
            this.copiedRecord = args.rowData;
            this.copiedRecord.taskData.TaskID = this.gantt.currentViewData.length + 1;
        }
        if (args.item.id === 'paste') {
            this.gantt.addRecord(this.copiedRecord.taskData,'Below',args.rowData.index);
            if(this.copiedRecord.hasChildRecords) {
                this.addChildRecords(this.copiedRecord, args.rowData.index + 1);
            }
            this.copiedRecord = undefined;
        }
    };
    contextMenuOpen(args) {
        if (args.type !== 'Header') {
            if (this.copiedRecord) {
                args.hideItems.push('Copy');
            } else {
                args.hideItems.push('Paste');
             }
        }
    };
    addChildRecords(record: any, index: any) {
        for(var i=0; i<record.childRecords.length; i++) {
              var childRecord = record.childRecords[i];
              childRecord.taskData.TaskID = this.gantt.currentViewData.length + 1;
              this.gantt.addRecord(childRecord.taskData,'Below',index);
              if(childRecord.hasChildRecords) {
                  this.addChildRecords(childRecord, index + (i+1));
              }
        }
      };
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} editSettings={this.editSettings} enableContextMenu={true} enableContextMenu={true} contextMenuItems={this.contextMenuItems} contextMenuClick={this.contextMenuClick.bind(this)} contextMenuOpen={this.contextMenuOpen.bind(this)} ref={gantt => this.gantt = gantt} height='450px'>
            <Inject services={[Edit, ContextMenu, Selection]}/>
        </GanttComponent>;
    }
}
;
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %}