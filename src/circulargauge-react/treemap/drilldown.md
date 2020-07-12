# Drill-down

The tree map control supports drill-down to expose the hierarchy achieved by clicking a node. If you click an item in tree map, the tree map will be moved to the next level or sub level and returned back to the previous level by clicking the node header. A single level of the tree map is visible at a time.

## Perform drill-down action

The tree map elements can be drilled down by setting the enableDrillDown property to true. You can view the hierarchy of the tree map by clicking the tree map items and move to the previous level by clicking the drill-down header.

The drill-down concepts are shown in the following code example.

{% tab template= "treemap/drilldown", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true , es5Template = "es5Drilldown" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, LevelDirective, LevelsDirective } from '@syncfusion/ej2-react-treemap';

class App extends React.Component {
render() {
  return ( <TreeMapComponent id='treemap'
        palette= {["#f44336", "#29b6f6", "#ab47bc", "#ffc107", "#5c6bc0", "#009688"]}
        dataSource={[
            { Category: 'Employees', Country: 'USA', JobDescription: 'Sales', JobGroup: 'Executive', EmployeesCount: 20 },
            { Category: 'Employees', Country: 'USA', JobDescription: 'Sales', JobGroup: 'Analyst', EmployeesCount: 30 },
            { Category: 'Employees', Country: 'USA', JobDescription: 'Marketing', EmployeesCount: 40 },
            { Category: 'Employees', Country: 'USA', JobDescription: 'Management', EmployeesCount: 80 },
            { Category: 'Employees', Country: 'India', JobDescription: 'Technical', JobGroup: 'Testers', EmployeesCount: 100 },
            { Category: 'Employees', Country: 'India', JobDescription: 'HR Executives', EmployeesCount: 30 },
            { Category: 'Employees', Country: 'India', JobDescription: 'Accounts', EmployeesCount: 40 },
            { Category: 'Employees', Country: 'Germany', JobDescription: 'Sales', JobGroup: 'Executive', EmployeesCount: 50 },
            { Category: 'Employees', Country: 'Germany', JobDescription: 'Sales', JobGroup: 'Analyst', EmployeesCount: 60 },
            { Category: 'Employees', Country: 'Germany', JobDescription: 'Marketing', EmployeesCount: 70 },
            { Category: 'Employees', Country: 'Germany', JobDescription: 'Technical', JobGroup: 'Testers', EmployeesCount: 80 },
            { Category: 'Employees', Country: 'Germany', JobDescription: 'Management', EmployeesCount: 10 },
            { Category: 'Employees', Country: 'Germany', JobDescription: 'Accounts', EmployeesCount: 20 },
            { Category: 'Employees', Country: 'UK', JobDescription: 'Technical', JobGroup: 'Testers', EmployeesCount: 30 },
            { Category: 'Employees', Country: 'UK', JobDescription: 'HR Executives', EmployeesCount: 50 },
            { Category: 'Employees', Country: 'UK', JobDescription: 'Accounts', EmployeesCount: 60 },
            { Category: 'Employees', Country: 'France', JobDescription: 'Technical', JobGroup: 'Testers', EmployeesCount: 70 },
            { Category: 'Employees', Country: 'France', JobDescription: 'Marketing', EmployeesCount: 100 }
        ]}
        weightValuePath= 'EmployeesCount'
        enableDrillDown= {true}
        leafItemSettings={{
            labelPath: 'Car',
            labelFormat:'${Car}-${Brand}',
            interSectAction:'WrapByWord'
        }}>
        <LevelsDirective>
            <LevelDirective groupPath='Country' border={{ color: 'black', width: 0.5 }} />
            <LevelDirective groupPath='JobDescription' border={{ color: 'black', width: 0.5 }} />
            <LevelDirective groupPath='JobGroup' border={{ color: 'black', width: 0.5 }} />
        </LevelsDirective>
    </TreeMapComponent> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}