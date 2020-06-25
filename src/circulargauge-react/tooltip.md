# Tooltip

Tooltip is used to display details about the items in tree map when the mouse hovers over the item.

## Default tooltip

By default, tooltip is not visible. You can enable the tooltip by setting the `enable` property to true and injecting the `TreeMapTooltip` module using the `TreeMap.Inject(TreeMapTooltip)`.

The following example shows the default tooltip.

{% tab template= "treemap/tooltip", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true , es5Template = "es5Tooltip" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, Inject, TreeMapTooltip } from '@syncfusion/ej2-react-treemap';

class App extends React.Component {
render() {
  return ( <TreeMapComponent id='treemap'
        dataSource={[
            { fruit:'Apple', count:5000 },
            { fruit:'Mango', count:3000 },
            { fruit:'Orange', count:2300 },
            { fruit:'Banana', count:500 },
            { fruit:'Grape', count:4300 },
            { fruit:'Papaya', count:1200 },
            { fruit:'Melon', count:4500 }
        ]}
        weightValuePath= 'count'
        leafItemSettings= {{
            labelPath: 'fruit'
        }}
        tooltipSettings= {{
            visible: true
        }}>
        <Inject services={[TreeMapTooltip]} />
    </TreeMapComponent> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}

## Format tooltip

By default, tooltip shows information about weight value of current item. In addition, to show more information in tooltip, format the tooltip as `${dataField}` from data source.

The following example shows formatting the tooltip.

{% tab template= "treemap/tooltip", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true , es5Template = "es5TooltipFormat" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, Inject, TreeMapTooltip } from '@syncfusion/ej2-react-treemap';

class App extends React.Component {
render() {
  return ( <TreeMapComponent id='treemap'
        dataSource={[
            { fruit:'Apple', count:5000 },
            { fruit:'Mango', count:3000 },
            { fruit:'Orange', count:2300 },
            { fruit:'Banana', count:500 },
            { fruit:'Grape', count:4300 },
            { fruit:'Papaya', count:1200 },
            { fruit:'Melon', count:4500 }
        ]}
        weightValuePath= 'count'
        leafItemSettings= {{
            labelPath: 'fruit'
        }}
        tooltipSettings= {{
            visible: true,
            format:'Name:${fruit} - TotalCount:${count}'
        }}>
        <Inject services={[TreeMapTooltip]} />
    </TreeMapComponent> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}

## Tooltip template

Any HTML element can be displayed in tooltip using the ‘template’ property. You can use `${dataField}` as placeholder in HTML element to display the values from data source.

The following example shows tooltip template.

{% tab template= "treemap/tooltip", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true , es5Template = "es5TooltipTemplate" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, Inject, TreeMapTooltip } from '@syncfusion/ej2-react-treemap';

class App extends React.Component {
render() {
  return ( <TreeMapComponent id='treemap'
        dataSource={[
            { fruit:'Apple', count:5000 },
            { fruit:'Mango', count:3000 },
            { fruit:'Orange', count:2300 },
            { fruit:'Banana', count:500 },
            { fruit:'Grape', count:4300 },
            { fruit:'Papaya', count:1200 },
            { fruit:'Melon', count:4500 }
        ]}
        weightValuePath= 'count'
        leafItemSettings= {{
            labelPath: 'fruit'
        }}
        tooltipSettings= {{
            visible: true,
            template:'<div><p>Name: ${fruit}</p><p>Total Count: ${count}</p></div>'
        }}>
        <Inject services={[TreeMapTooltip]} />
    </TreeMapComponent> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}