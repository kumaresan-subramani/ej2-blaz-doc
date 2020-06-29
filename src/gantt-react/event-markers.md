---
title: "Event Markers"
component: "Gantt"
description: "Learn how to highlight the important event in Gantt chart part in the Essential JS 2 Gantt Component."
---

# Event markers

The event markers in the Gantt component is used to highlight the important events in a project. Event markers can be initialized by using the [`eventMarkers`](../api/gantt/eventMarker/) property, and you can define date and label for the event markers using the [`day`](../api/gantt/eventMarker/#day) and [`label`](../api/gantt/eventMarker/#label) properties. You can also customize it using the [`cssClass`](../api/gantt/eventMarker/#cssclass) properties. The following code example shows how to add event markers in the Gantt component.

To highlight the days, inject the [`DayMarkers`](../api/gantt/#daymarkersmodule) module into the Gantt component.

{% tab template="gantt/event-markers", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, DayMarkers, EventMarkersDirective, EventMarkerDirective } from '@syncfusion/ej2-react-gantt';
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
  public eventMarkerDay: Date = new Date('4/10/2019');
  render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields} height = '450px'>
        <EventMarkersDirective>
              <EventMarkerDirective day={this.eventMarkerDay} cssClass='e-custom-event-marker'  label='Project approval and kick-off' ></EventMarkerDirective>
        </EventMarkersDirective>
            <Inject services={[DayMarkers]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}