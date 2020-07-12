---
title: "Holidays"
component: "Gantt"
description: "Learn how to highlight the non-working days in the Essential JS 2 Gantt component."
---

# Holidays

Non-working days in a project can be displayed in the Gantt component using the [`holidays`](../api/gantt/#holidays) property. Each holiday can be defined with the following properties:

* [`from`](../api/gantt/holiday/#from): Defines start date of the holiday(s).
* [`to`](../api/gantt/holiday/#to): Defines end date of the holiday(s).
* [`label`](../api/gantt/holiday/#label): Defines the description or label for the holiday.
* [`cssClass`](../api/gantt/holiday/#cssclass): Formats the holidays label in the Gantt chart.

To highlight the holidays, inject the [`DayMarkers`](../api/gantt/#daymarkersmodule) module into the Gantt component.

The following code example shows how to display the non-working days in the Gantt component.

{% tab template="gantt/holiday", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { GanttComponent, Inject, DayMarkers, HolidaysDirective, HolidayDirective } from '@syncfusion/ej2-react-gantt';
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
    render() {
        return <GanttComponent dataSource={data} taskFields={this.taskFields}
        height = '450px'>
            <HolidaysDirective>
                <HolidayDirective from='04/10/2019' label='Local Holiday' cssClass='e-custom-holiday'></HolidayDirective>
            </HolidaysDirective>
            <Inject services={[DayMarkers]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}