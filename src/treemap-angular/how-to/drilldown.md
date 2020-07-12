# How To

## Customize the header for treemap drilldown

Yon can add a header element as <div> and customize it to show the population of a particular country or continent on treemap drill-down.

To customize the header for treemap drill-down, follow the given steps:

**Step 1**:

<!-- markdownlint-disable MD031 -->
<!-- markdownlint-disable MD010 -->
Initialize the treemap and enable the drill-down option.

```typescript
import { Component, ViewEncapsulation } from '@angular/core';
import { TreeMap, IDrillEndEventArgs, ILoadEventArgs } from '@syncfusion/ej2-angular-treemap';
import { DrillDown } from './datasource';

@Component({
  selector: 'app-container',
  template: '<ejs-treemap id="container" #treemap style="display:block;" [dataSource]="dataSource" [weightValuePath]="weightValuePath"[leafItemSettings]="leafItemSettings" [palette]="palette" format="n" useGroupingSeparator="true" enableDrillDown="true"><e-levels><e-level groupPath="Continent" fill="#336699" [border]="border"> </e-level><e-level groupPath="States" fill="#336699" [border]="border"> </e-level><e-level groupPath="Region" showHeader="false" fill="#336699" [border]="border"></e-level></e-levels></ejs-treemap>',
  encapsulation: ViewEncapsulation.None
})
export class AppComponent implements OnInit {
  public palette: string[] = ['#9999ff', '#CCFF99', '#FFFF99', '#FF9999', '#FF99FF', '#FFCC66'];
  public dataSource: object[] = DrillDown;
  public weightValuePath: string = 'Population';
  public leafItemSettings: object = {
    labelPath: 'Name',
    showLabels: false,
    labelStyle: { size: '0px' },
    border: { color: 'black', width: 0.5 }
  };
  border: object = {
    color: 'black',
    width: 0.5
  };
};
```

**Step 2**:

Show the population of a particular continent in the treemap `loaded` event. In this event, you can get the header element.

```typescript
    public loaded = (args: ILoadEventArgs) => {
    let header: Element = document.getElementById('header');
    let population: number = 0;
    for (let i: number = 0; i < args.treemap.layout.renderItems[0]['parent'].Continent.length; i++) {
      population += +(args.treemap.layout.renderItems[0]['parent'].Continent[i]['data'].Population);
    }
    header.innerHTML = 'Continent - Population : ' + population
  }
```

**Step 3**:

Customize the population for drilled countries or states in the header element when drill-down the treemap. The `drillEnd` event will be triggered when treemap is drilled.

{% tab template= "treemap/how-to/header-template", sourceFiles="app/**/*.ts" , isDefaultActive=true %}

```typescript

import { Component, ViewEncapsulation } from '@angular/core';
import { TreeMap, IDrillEndEventArgs, ILoadEventArgs } from '@syncfusion/ej2-angular-treemap';
import { DrillDown } from './datasource';

@Component({
  selector: 'app-container',
  template: '<ejs-treemap id="container" #treemap style="display:block;" [dataSource]="dataSource" [weightValuePath]="weightValuePath"[leafItemSettings]="leafItemSettings" [palette]="palette" format="n" useGroupingSeparator="true" enableDrillDown="true"(loaded)="loaded($event)" (drillEnd)="drillEnd($event)"><e-levels><e-level groupPath="Continent" fill="#336699" [border]="border"> </e-level><e-level groupPath="States" fill="#336699" [border]="border"> </e-level><e-level groupPath="Region" showHeader="false" fill="#336699" [border]="border"></e-level></e-levels></ejs-treemap>',
  encapsulation: ViewEncapsulation.None
})
export class AppComponent implements OnInit {
  public loaded = (args: ILoadEventArgs) => {
    let header: Element = document.getElementById('header');
    let population: number = 0;
    for (let i: number = 0; i < args.treemap.layout.renderItems[0]['parent'].Continent.length; i++) {
      population += +(args.treemap.layout.renderItems[0]['parent'].Continent[i]['data'].Population);
    }
    header.innerHTML = 'Continent - Population : ' + population
  }
  public drillEnd = (args: IDrillEndEventArgs) => {
    let header: Element = document.getElementById('header');
    let layout: Element = document.getElementById("container_TreeMap_Squarified_Layout");
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
  public palette: string[] = ['#9999ff', '#CCFF99', '#FFFF99', '#FF9999', '#FF99FF', '#FFCC66'];
  public dataSource: object[] = DrillDown;
  public weightValuePath: string = 'Population';
  public leafItemSettings: object = {
    labelPath: 'Name',
    showLabels: false,
    labelStyle: { size: '0px' },
    border: { color: 'black', width: 0.5 }
  };
  border: object = {
    color: 'black',
    width: 0.5
  };
};
```

{% endtab %}