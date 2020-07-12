# Add label template with drill down

Yon can add a label template as <div> element to the tree map control when using the label template. To add a label template to the tree map control, you have to hide another labels by setting the `showLabels` property to false in `leafItemSettings` to show only the label template.

To add label template to tree map drilldown, follow the given steps:

**Step 1**:

Create a tree map control and enable the drill-down option.

```javascript
import { TreeMap, IDrillStartEventArgs } from '@syncfusion/ej2-treemap';
import { CarSales } from './datasource';

let treemap: TreeMap = new TreeMap({
  dataSource: CarSales,
  enableDrillDown: true,
  weightValuePath: 'Sales',
  palette: ["white"],
  levels: [
    {
      groupPath: 'Continent',
      border: { width: 0.5, color: 'black' }
    },
    {
      groupPath: 'Company',
      border: { width: 0.5, color: 'black' }
    },
  ]
}, '#container');
```

**Step 2**:

Add the label template in the `leafItemSettings` options, and then set the `showLabels` property to false to hide another labels and show only label template.

{% tab template= "treemap/how-to/label-template", es5Template="es5LabelTemplate" %}

```typescript

import { TreeMap, IDrillStartEventArgs } from '@syncfusion/ej2-treemap';
import { CarSales } from './datasource.ts';

let treemap: TreeMap = new TreeMap({
  dataSource: CarSales,
  enableDrillDown: true,
  weightValuePath: 'Sales',
  drillStart: function(args: IDrillStartEventArgs) {
    let labelElementGroup: HTMLElement = document.getElementById('container_Label_Template_Group');
    labelElementGroup.remove();
  },
  palette: ["white"],
  leafItemSettings: {
    showLabels: false,
    // Add label template here
    labelTemplate: '#template',
    // positioning the label template
    templatePosition: 'Center'
  },
  levels: [
    {
      groupPath: 'Continent',
      border: { width: 0.5, color: 'black' }
    },
    {
      groupPath: 'Company',
      border: { width: 0.5, color: 'black' }
    },
  ]
}, '#container');
```

{% endtab %}