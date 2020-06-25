# Print and Export

## Print

The rendered tree map can be printed directly from the browser by calling the public method print. The ID of the tree map div element must be passed as argument to that method.

The following code example shows how to print the tree map.

{% tab template= "treemap/printAndExport", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent } from '@syncfusion/ej2-react-treemap';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';

export class App extends React.Component {
public click(){
  this.treemap.print();
}
private treemap: TreeMapComponent;
render() {
  return ( <div>
    <ButtonComponent value='Print' onClick= { this.click.bind(this)}>Print</ButtonComponent>
    <TreeMapComponent id='treemap' ref={g => this.treemap = g}
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
        weightValuePath= 'GDP'
        leafItemSettings= {{
            labelPath: 'State',
            labelFormat: '${State}<br>$${GDP} Trillion<br>(${percentage} %)',
            labelStyle: {
                color: '#000000'
            },
            border: {
                color: '#000000',
                width: 0.5
            }
        }}>
    </TreeMapComponent></div> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}

## Export

The rendered tree map can be exported to JPEG or PNG format using export method in tree map. The input parameters for this method are Export Type for format and fileName for result.

The following code example shows how to export the tree map.

{% tab template= "treemap/printAndExport", compileJsx=true, sourceFiles="app/**/*.tsx" , isDefaultActive=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent } from '@syncfusion/ej2-react-treemap';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';

export class App extends React.Component {
public click(){
  this.treemap.export('PNG', 'export');
}
public treemap: TreeMapComponent;
render() {
  return ( <div>
    <ButtonComponent value='Export' onClick= { this.click.bind(this)}>Export</ButtonComponent> <TreeMapComponent id='treemap' ref={g => this.treemap = g}
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
        weightValuePath= 'GDP'
        leafItemSettings= {{
            labelPath: 'State',
            labelFormat: '${State}<br>$${GDP} Trillion<br>(${percentage} %)',
            labelStyle: {
                color: '#000000'
            },
            border: {
                color: '#000000',
                width: 0.5
            }
        }}>
    </TreeMapComponent> </div> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}