# Levels

You can give 'n' number of levels to the tree map. Each level can be separated using the [`groupPath`] property.

The following customization options are available to customize the tree map levels.

<!-- markdownlint-disable MD036 -->

**Group path**

The [`groupPath`] property is used to separate each level in tree map. The GroupPath accepts a field in dataSource.

{% tab template= "treemap/levels", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true , es5Template = "es5LevelGroupPath" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, LevelDirective, LevelsDirective } from '@syncfusion/ej2-react-treemap';

class App extends React.Component {
render() {
  return ( <TreeMapComponent id='treemap'
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
        palette= {["#f44336", "#29b6f6", "#ab47bc", "#ffc107", "#5c6bc0", "#009688"]}
        weightValuePath= 'EmployeesCount'>
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

<!-- markdownlint-disable MD036 -->

**Group gap**

The [`groupGap`] property is used to separate an item from every group or another item to differentiate the levels mentioned in the tree map.

{% tab template= "treemap/levels", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true , es5Template = "es5LevelGroupGap" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, LevelDirective, LevelsDirective } from '@syncfusion/ej2-react-treemap';

class App extends React.Component {
render() {
  return ( <TreeMapComponent id='treemap'
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
        palette= {["#f44336", "#29b6f6", "#ab47bc", "#ffc107", "#5c6bc0", "#009688"]}
        weightValuePath= 'EmployeesCount'>
        <LevelsDirective>
            <LevelDirective groupPath='Country' groupGap={10} border={{ color: 'black', width: 0.5 }} />
            <LevelDirective groupPath='JobDescription' groupGap={10} border={{ color: 'black', width: 0.5 }} />
            <LevelDirective groupPath='JobGroup' groupGap={10} border={{ color: 'black', width: 0.5 }} />
        </LevelsDirective>
    </TreeMapComponent> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

**Header format and alignment**

You can customize header using the [`headerFormat`] property in which fields are mapping from the dataSource. You can also align header using the [`headerAlignment`] property.

{% tab template= "treemap/levels", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true , es5Template = "es5LevelHeaderFormat" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, LevelDirective, LevelsDirective } from '@syncfusion/ej2-react-treemap';

class App extends React.Component {
render() {
  return ( <TreeMapComponent id='treemap'
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
        palette= {["#f44336", "#29b6f6", "#ab47bc", "#ffc107", "#5c6bc0", "#009688"]}
        weightValuePath= 'EmployeesCount'>
        <LevelsDirective>
            <LevelDirective groupPath='Country' headerFormat='${Country}-${EmployeesCount}' headerAlignment='Center' border={{ color: 'black', width: 0.5 }} />
            <LevelDirective groupPath='JobDescription' headerFormat='${JobDescription}-${EmployeesCount}' headerAlignment='Far' border={{ color: 'black', width: 0.5 }} />
            <LevelDirective groupPath='JobGroup' headerFormat='${JobGroup}-${EmployeesCount}' headerAlignment='Near' border={{ color: 'black', width: 0.5 }} />
        </LevelsDirective>
    </TreeMapComponent> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}

**Header height and style**

You can customize the font color, family, weight, and size using the [`headerStyle`] property. Based on font size, the header height can be given using the [`headerHeight`] property.

{% tab template= "treemap/levels", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true , es5Template = "es5LevelHeaderHeight" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, LevelDirective, LevelsDirective } from '@syncfusion/ej2-react-treemap';

class App extends React.Component {
render() {
  return ( <TreeMapComponent id='treemap'
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
        palette= {["#f44336", "#29b6f6", "#ab47bc", "#ffc107", "#5c6bc0", "#009688"]}
        weightValuePath= 'EmployeesCount'>
        <LevelsDirective>
            <LevelDirective groupPath='Country' headerHeight={35} headerStyle={{ size:'15px' }} border={{ color: 'black', width: 0.5 }} />
            <LevelDirective groupPath='JobDescription' headerHeight={45} headerStyle={{ size:'15px' }} border={{ color: 'black', width: 0.5 }} />
            <LevelDirective groupPath='JobGroup' headerHeight={40} headerStyle={{ size:'15px' }} border={{ color: 'black', width: 0.5 }} />
        </LevelsDirective>
    </TreeMapComponent> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}

**Header template and position**

The treemap header supports to customize header of each item using the [`headerTemplate`] property. It uses Essential JS2 [`Template engine`] to render the elements. You can position the template using the [`templatePosition`] property.

The template concepts are illustrated in the following example.

{% tab template= "treemap/levels", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true , es5Template = "es5LevelHeaderTemplate" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, LevelDirective, LevelsDirective } from '@syncfusion/ej2-react-treemap';

class App extends React.Component {
render() {
  return ( <TreeMapComponent id='treemap'
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
        palette= {["#f44336", "#29b6f6", "#ab47bc", "#ffc107", "#5c6bc0", "#009688"]}
        weightValuePath= 'EmployeesCount'>
        <LevelsDirective>
            <LevelDirective groupPath='Country' headerTemplate='<div>{{:Country}}</div>' headerAlignment='Center' border={{ color: 'black', width: 0.5 }} />
            <LevelDirective groupPath='JobDescription' headerTemplate='<div>{{:JobDescription}}</div>' headerAlignment='Center' border={{ color: 'black', width: 0.5 }} />
            <LevelDirective groupPath='JobGroup' headerTemplate='<div>{{:JobGroup}}</div>' headerAlignment='Far' border={{ color: 'black', width: 0.5 }} />
        </LevelsDirective>
    </TreeMapComponent> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}