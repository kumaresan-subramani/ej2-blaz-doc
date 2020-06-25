# Add label template with drill down

Yon can add a label template as <div> element to the tree map control when using the label template. To add a label template to the tree map control, you have to hide another labels by setting the `showLabels` property to false in `leafItemSettings` to show only the label template.

To add label template to tree map drilldown, follow the given steps:

**Step 1**:

Create a tree map control and enable the drill-down option.

{% tab compileJsx=true%}

```tsx
import { TreeMapComponent, LevelDirective, LevelsDirective, ILoadedEventArgs, IDrillEndEventArgs } from '@syncfusion/ej2-react-treemap';
import * as React from 'react';
import * as ReactDOM from "react-dom";
import { CarSales } from './datasource';

class App extends React.Component {
  render() {
    return (
      <TreeMapComponent id='container' weightValuePath='Sales' palette={['white']} enableDrillDown={true} dataSource={CarSales}
          leafItemSettings={ {
            showLabels: false,
            labelTemplate: '#template',
            templatePosition: 'Center'
          } }>
          <LevelsDirective>
            <LevelDirective groupPath='Continent' fill='#336699' border={ { color: 'black', width: 0.5 } } />
            <LevelDirective groupPath='Company' fill='#336699' border={ { color: 'black', width: 0.5 } } />
          </LevelsDirective>
        </TreeMapComponent>
    );
  }
}
ReactDOM.render(
  <App />,
  document.getElementById('treemap') as HTMLElement
);
```

{% endtab %}

**Step 2**:

Add the label template in the `leafItemSettings` options, and then set the `showLabels` property to false to hide another labels and show only label template.

{% tab template="treemap/how-to/label-template", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true %}

```tsx

import { TreeMapComponent, LevelDirective, LevelsDirective, ILoadedEventArgs, IDrillEndEventArgs } from '@syncfusion/ej2-react-treemap';
import * as React from 'react';
import * as ReactDOM from "react-dom";
import { CarSales } from './datasource';

class App extends React.Component {
  public drillStart(args: IDrillStartEventArgs): void {
    let labelElementGroup: HTMLElement = document.getElementById('container_Label_Template_Group') as HTMLElement;
    labelElementGroup.remove();
  }
  render() {
    return (
     <TreeMapComponent drillStart={this.drillStart.bind(this)} id='container' weightValuePath='Sales' palette={['white']} enableDrillDown={true} dataSource={CarSales}
          leafItemSettings={ {
            showLabels: false,
            labelTemplate: '#template',
            templatePosition: 'Center'
          } }>
          <LevelsDirective>
            <LevelDirective groupPath='Continent' fill='#336699' border={ { color: 'black', width: 0.5 } } />
            <LevelDirective groupPath='Company' fill='#336699' border={ { color: 'black', width: 0.5 } } />
          </LevelsDirective>
        </TreeMapComponent>
    );
  }
}
ReactDOM.render(
  <App />,
  document.getElementById('treemap') as HTMLElement
);
```

{% endtab %}