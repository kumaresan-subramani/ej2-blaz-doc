# Drilldown

## Customize the header for treemap drilldown

Yon can add a header element as <div> and customize it to show the population of a particular country or continent on treemap drill-down.

To customize the header for treemap drill-down, follow the given steps:

**Step 1**:

<!-- markdownlint-disable MD031 -->
Initialize the treemap and enable the drill-down option.

{% tab compileJsx=true%}

```tsx
import { TreeMapComponent, LevelDirective, LevelsDirective, ILoadedEventArgs, IDrillEndEventArgs } from '@syncfusion/ej2-react-treemap';
import * as React from 'react';
import * as ReactDOM from "react-dom";
import { DrillDown } from './datasource';
class App extends React.Component {

  render() {
    return (
      <TreeMapComponent id='container' palette={ ['#9999ff', '#CCFF99', '#FFFF99', '#FF9999', '#FF99FF', '#FFCC66'] } enableDrillDown={true} format={"n"} useGroupingSeparator={true} dataSource={DrillDown} weightValuePath='Population' leafItemSettings={ {
            labelPath: 'Name',
            showLabels: false,
            labelStyle: { size: '0px' },
            border: { color: 'black', width: 0.5 }
          } }>
            <LevelsDirective>
              <LevelDirective groupPath='Continent' fill='#336699' border={ { color: 'black', width: 0.5 } } />
              <LevelDirective groupPath='States' fill='#336699' border={ { color: 'black', width: 0.5 } } />
              <LevelDirective groupPath='Region' showHeader={false} fill='#336699' border={ { color: 'black', width: 0.5 } } />
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

Show the population of a particular continent in the treemap `loaded` event. In this event, you can get the header element.

{% tab compileJsx=true%}

```jsx
    public loaded(args: ILoadedEventArgs): void {
    let header: Element = document.getElementById('header') as Element;
    let population: number = 0;
    for (let i: number = 0; i < args.treemap.layout.renderItems[0]['parent'].Continent.length; i++) {
      population += +(args.treemap.layout.renderItems[0]['parent'].Continent[i]['data'].Population);
    }
    header.innerHTML = 'Continent - Population : ' + population
  }
```

{% endtab %}

**Step 3**:

Customize the population for drilled countries or states in the header element when drill-down the treemap. The `drillEnd` event will be triggered when treemap is drilled.

{% tab template="treemap/how-to/header-template", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true %}

```tsx

import { TreeMapComponent, LevelDirective, LevelsDirective, ILoadedEventArgs, IDrillEndEventArgs } from '@syncfusion/ej2-react-treemap';

import * as React from 'react';
import * as ReactDOM from "react-dom";
import { DrillDown } from './datasource';

class App extends React.Component {
  public loaded(args: ILoadedEventArgs): void {
    let header: Element = document.getElementById('header') as Element;
    let population: number = 0;
    for (let i: number = 0; i < args.treemap.layout.renderItems[0]['parent'].Continent.length; i++) {
      population += +(args.treemap.layout.renderItems[0]['parent'].Continent[i]['data'].Population);
    }
    header.innerHTML = 'Continent - Population : ' + population
  }
  public drillEnd(args: IDrillEndEventArgs): void {
    let header: Element = document.getElementById('header') as Element;
    let layout: Element = document.getElementById("container_TreeMap_Squarified_Layout") as Element;
    let population: number = 0;
    if (args.treemap.layout.renderItems[0]['isDrilled']) {
      for (let i: number = 0; i < args.treemap.layout.renderItems.length; i++) {
        population += +(args.treemap.layout.renderItems[i]['data'].Population);
      }
      header.innerHTML = layout.children[0].children[1].innerHTML.split(']')[1] + ' - ' + population;
    }
    else if (args.treemap.layout.renderItems[0]['parent'].Continent) {
      for (let i: number = 0; i < args.treemap.layout.renderItems[0]['parent'].Continent.length; i++) {
        population += +(args.treemap.layout.renderItems[0]['parent'].Continent[i]['data'].Population);
      }
      header.innerHTML = 'Continent - Population : ' + population;
    } else {
      population = args.treemap.layout.renderItems[0]['data'].Population;
      header.innerHTML = layout.children[0].children[1].innerHTML.split(']')[1] + ' - Population : ' + population;
    }
  }
  render() {
    return (
      <TreeMapComponent drillEnd={this.drillEnd.bind(this)} loaded={this.loaded.bind(this)} id='container' palette={ ['#9999ff', '#CCFF99', '#FFFF99', '#FF9999', '#FF99FF', '#FFCC66'] } enableDrillDown={true} format={"n"} useGroupingSeparator={true} dataSource={DrillDown} weightValuePath='Population' leafItemSettings={ {
            labelPath: 'Name',
            showLabels: false,
            labelStyle: { size: '0px' },
            border: { color: 'black', width: 0.5 }
          } }>
            <LevelsDirective>
              <LevelDirective groupPath='Continent' fill='#336699' border={ { color: 'black', width: 0.5 } } />
              <LevelDirective groupPath='States' fill='#336699' border={ { color: 'black', width: 0.5 } } />
              <LevelDirective groupPath='Region' showHeader={false} fill='#336699' border={ { color: 'black', width: 0.5 } } />
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