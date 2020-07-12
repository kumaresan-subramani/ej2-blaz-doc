# Data Binding

The tree map control supports data binding using the dataSource property.

## Populate data

The [`dataSource`] property accepts collection values as input. For example, a list of objects can be provided as input. Data can be given as either flat or hierarchical collection to the [`dataSource`] property.

<!-- markdownlint-disable MD036 -->

**Flat collection**

The following code shows how to bind a flat collection as data source to the tree map control.

{% tab template= "treemap/databind", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent } from '@syncfusion/ej2-react-treemap';

class App extends React.Component {
render() {
  return ( <TreeMapComponent id='treemap'
        dataSource={[
            {State:"United States", GDP:17946, percentage:11.08, Rank:1},
            {State:"China", GDP:10866, percentage: 28.42, Rank:2},
            {State:"Japan", GDP:4123, percentage:-30.78, Rank:3},
            {State:"Germany", GDP:3355, percentage:-5.19, Rank:4},
            {State:"United Kingdom", GDP:2848, percentage:8.28, Rank:5},
            {State:"France", GDP:2421, percentage:-9.69, Rank:6},
            {State:"India", GDP:2073, percentage:13.65, Rank:7},
            {State:"Italy", GDP:1814, percentage:-12.45, Rank:8},
            {State:"Brazil", GDP:1774, percentage:-27.88, Rank:9},
            {State:"Canada", GDP:1550, percentage:-15.02, Rank:10}
        ]}
        weightValuePath='GDP'
        leafItemSettings={{
            labelPath: 'State'
        }}>
    </TreeMapComponent> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}

**Hierarchical collection**

The following code shows how to bind a hierarchical collection as data source to the treemap control.

<!-- markdownlint-disable MD010 -->

{% tab compileJsx=true%}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, LevelDirective, LevelsDirective } from '@syncfusion/ej2-react-treemap';

class App extends React.Component {
render() {
  return ( <TreeMapComponent id='treemap'
       dataSource={[
            {
                    { Name: "United States", Sales: 28092, Expense: 26000, States: [
                    { Name: "New York", Sales: 2353, Expense: 2000 },
                    { Name: "Los Angeles", Sales: 3453, Expense: 3000 },
                    { Name: "San Francisco", Sales: 8456, Expense: 8000 },
                    { Name: "Chicago", Sales: 6785, Expense: 7000 },
                    { Name: "Miami", Sales: 7045, Expense: 6000 },
                ]
            },
            {
                Name: "Canada", Sales: 19240, Expense: 18500, States: [
                    { Name: "Toronto", Sales: 7045, Expense: 7000 },
                    { Name: "Vancouver", Sales: 4352, Expense: 4000 },
                    { Name: "Winnipeg", Sales: 7843, Expense: 7500 }
                ]
            },
            {
                Name: "Mexico",Sales: 16980, Expense: 14500, States: [
                    { Name: "Mexico City", Sales: 7843, Expense: 6500, States1: [
                        { Name: "Cancun1", Sales: 6683, Expense: 6000 },
                        { Name: "Acapulco1", Sales: 2454, Expense: 2000 }
                    ]
                    },
                    { Name: "Cancun", Sales: 6683, Expense: 6000 },
                    { Name: "Acapulco", Sales: 2454, Expense: 2000 }
                ]
            },
        ]}
        weightValuePath='Sales'
        leafItemSettings={{
            labelPath: 'Name'
        }}>
        <LevelsDirective>
            <LevelDirective groupPath='States' groupGap={3} showHeader={true} headerHeight={25} showLabels={true} headerTemplate='headertemplate' labelTemplate: 'labeltemplate' />
        </LevelsDirective>
    </TreeMapComponent> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}