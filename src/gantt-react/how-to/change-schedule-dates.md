---
title: "How To"
component: "Gantt"
description: "Learn how to change schedule start date and end date values dynamically in the JS 2 Gantt Component."
---

# Change schedule start and end dates

In the Gantt component, you can change the schedule start and end dates by clicking the custom button programmatically using the [`updateProjectDates`](../../api/gantt/#updateprojectdates) method. You can pass the start and end dates as method arguments to the [`updateProjectDates`](../../api/gantt/#updateprojectdates) method. You can also pass the Boolean value as an additional parameter, which is used to round-off the schedule start and end dates displayed in Gantt timeline.

{% tab template="gantt/how-to-changescheduledates", compileJsx=true %}

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
    child: 'subtasks'
  };
  public clickHandler(){
    this.ganttInstance.updateProjectDates(new Date('01/10/2019'),new Date('06/20/2019'),true);
}
    render() {
        return (<div>
        <ButtonComponent onClick= { this.clickHandler.bind(this)}>Update ScheduleDates</ButtonComponent>
        <GanttComponent dataSource={data} taskFields={this.taskFields}
        height = '450px' ref={gantt => this.ganttInstance = gantt}>
        </GanttComponent></div>)
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}
