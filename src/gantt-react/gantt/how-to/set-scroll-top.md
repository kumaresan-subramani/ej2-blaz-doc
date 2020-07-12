---
title: "How To"
component: "Gantt"
description: "Learn how to set the setScrollTop position in Gantt chart side."
---

# Set the vertical scroll position

In the Gantt component, you can set the vertical scroller position dynamically by clicking the custom button using the [`setScrollTop`](../../api/gantt/#setscrolltop) method.

{% tab template="gantt/how-to setscrolltop", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { GanttComponent } from '@syncfusion/ej2-react-gantt';
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
  public clickHandler(){
    this.ganttInstance.ganttChartModule.scrollObject.setScrollTop(300);
};
    render() {
        return (<div>
        <ButtonComponent onClick= { this.clickHandler.bind(this)}>SetScrollTop</ButtonComponent>
        <GanttComponent dataSource={data} taskFields={this.taskFields}
        height = '450px' ref={gantt => this.ganttInstance = gantt}>
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}