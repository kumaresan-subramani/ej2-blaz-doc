# Internationalization

The tree map control supports internationalization for the following elements:

* Data label
* Tooltip

For more information about number and date formatter, refer to [`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html).

<!-- markdownlint-disable MD036 -->
<!-- markdownlint-disable MD024 -->

## Globalization

Globalization is the process of designing and developing a component that works in different cultures/locales. Internationalization library is used to globalize number, date, and time values in the tree map control using the [`format`] property in the treemap model.

## Numeric format

In the following code example, tooltip is globalized to Deutsch culture.

```typescript

import { TreeMap, TreeMapTooltip } from '@syncfusion/ej2-treemap';
import { NumericTextBox} from '@syncfusion/ej2-inputs';
import { loadCldr, Ajax, setCulture, setCurrencyCode } from '@syncfusion/ej2-base';
TreeMap.Inject(TreeMapTooltip);
loadCultureFiles("de");
setCulture("de");
setCurrencyCode('EUR');
let treemap: TreeMap = new TreeMap({
    locale: "de",
    format: "c" ,
 dataSource: [
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
],
tooltipSettings: {
            visible: true,
    },
   weightValuePath: 'GDP'
}, '#container');
function loadCultureFiles(name: string) {
    var files = ['currencies.json', 'numbers.json'];
    var loadCulture = function (prop: number) {
        let val:  any, ajax: Ajax;
        // ajax = new Ajax('http://ej2.syncfusion.com/javascript/demos/' + 'src/common/cldr-data/main/' + name + '/' + files[prop], 'GET', false);
        ajax = new Ajax('/node_modules/cldr-data/main/' + name + '/' + files[prop], 'GET', false);
        ajax.onSuccess = function (value: any) {
            val = value;
        };
        ajax.send();
        loadCldr(JSON.parse(val));
    };
    for (var prop = 0; prop < files.length; prop++) {
        loadCulture(prop);
    }
}

```

## Right-to-left rendering

The TreeMap control supports right-to-left rendering for all its elements such as nodes, tooltip, data labels, and legends.

## Legend with Rtl support

If you set the `enableRtl` property to true, then the legend icon will be rendered on the right and the legend text will be rendered on the left of the legend icon.

{% tab template= "treemap/internationalization", sourceFiles="index.ts,index.html", es5Template="es5RtlLegend" %}

```typescript
let CarDetails:Object[] = [{ Car:'Mustang', Brand:'Ford', count:232, color: '#71B081' },
                       { Car:'EcoSport', Brand:'Ford', count:121,  color: '#5A9A77' },
                       { Car:'Swift', Brand:'Maruti', count:143, color: '#498770' },
                       { Car:'Baleno', Brand:'Maruti', count:454, color: '#39776C' },
                       { Car:'Vitara Brezza', Brand:'Maruti', count:545 , color: '#266665' },
                       { Car:'A3 Cabriolet', Brand:'Audi',count:123, color: '#124F5E' }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: CarDetails ,
    weightValuePath: 'count',
    colorValuePath: 'color',
    enableRtl:true,
    legendSettings: {
        visible: true,
        position:'Top'
    },
    leafItemSettings: {
        labelPath: 'Car'
     },
}, '#container');

```

{% endtab %}

## Tooltip with Rtl support

If the `enableRtl` property is set to true, the tooltip data will be rendered in reverse direction.

The following example shows the format of the tooltip.

{% tab template= "treemap/internationalization", sourceFiles="index.ts,index.html", es5Template="es5RtlTooltip" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapTooltip } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapTooltip);

let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    palette:['#71B081','#5A9A77', '#498770', '#39776C', '#266665','#124F5E'],
     tooltipSettings: {
            visible: true,
            format:'${count} : ${fruit}'
    },
    leafItemSettings: {
        labelPath: 'fruit'
     }
}, '#container');

```

{% endtab %}

## Treemap Item Rendering Direction

By default, the direction of tree map item is `TopLeftBottomRight`. You can customize the rendering direction of the tree map item by setting the `renderDirection` property.
The TreeMap can be rendered in the following four different directions.
      `TopLeftBottomRight`
      `TopRightBottomLeft`
      `BottomRightTopLeft`
      `BottomLeftTopRight`

The following example demonstrate how to render the treemap in the RTL direction with `TopLeftBottomRight`.

{% tab template= "treemap/internationalization", sourceFiles="index.ts,index.html", es5Template="es5TopLeftBottomRight" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapTooltip } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapTooltip);

let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    palette:['#71B081','#5A9A77', '#498770', '#39776C', '#266665','#124F5E'],
    renderDirection:'TopLeftBottomRight',
    leafItemSettings: {
        labelPath: 'fruit'
     }
}, '#container');

```

{% endtab %}

The following example demonstrate how to render the treemap in the RTL direction with `TopRightBottomLeft`.

{% tab template= "treemap/internationalization", sourceFiles="index.ts,index.html", es5Template="es5TopRightBottomLeft" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapTooltip } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapTooltip);

let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    palette:['#71B081','#5A9A77', '#498770', '#39776C', '#266665','#124F5E'],
    renderDirection:'TopRightBottomLeft',
    leafItemSettings: {
        labelPath: 'fruit'
     }
}, '#container');

```

{% endtab %}

The following example demonstrate how to render the treemap in the RTL direction with `BottomRightTopLeft`.

{% tab template= "treemap/internationalization", sourceFiles="index.ts,index.html", es5Template="es5BottomRightTopLeft" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapTooltip } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapTooltip);

let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    palette:['#71B081','#5A9A77', '#498770', '#39776C', '#266665','#124F5E'],
    renderDirection:'BottomRightTopLeft',
    leafItemSettings: {
        labelPath: 'fruit'
     }
}, '#container');

```

{% endtab %}

The following example demonstrate how to render the treemap in the RTL direction with `BottomLeftTopRight`.

{% tab template= "treemap/internationalization", sourceFiles="index.ts,index.html", es5Template="es5BottomLeftTopRight" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapTooltip } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapTooltip);

let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    palette:['#71B081','#5A9A77', '#498770', '#39776C', '#266665','#124F5E'],
    renderDirection:'BottomLeftTopRight',
    leafItemSettings: {
        labelPath: 'fruit'
     }
}, '#container');

```

{% endtab %}

## Right-to-left rendering

The TreeMap control supports right-to-left rendering for all its elements such as nodes, tooltip, data labels, and legends.

## Legend with Rtl support

If you set the `enableRtl` property to true, then the legend icon will be rendered on the right and the legend text will be rendered on the left of the legend icon.

{% tab template= "treemap/internationalization",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "es5RtlLegend" %}

```typescript
let CarDetails:Object[] = [{ Car:'Mustang', Brand:'Ford', count:232, color: '#71B081' },
                       { Car:'EcoSport', Brand:'Ford', count:121,  color: '#5A9A77' },
                       { Car:'Swift', Brand:'Maruti', count:143, color: '#498770' },
                       { Car:'Baleno', Brand:'Maruti', count:454, color: '#39776C' },
                       { Car:'Vitara Brezza', Brand:'Maruti', count:545 , color: '#266665' },
                       { Car:'A3 Cabriolet', Brand:'Audi',count:123, color: '#124F5E' }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: CarDetails ,
    weightValuePath: 'count',
    colorValuePath: 'color',
    enableRtl:true,
    legendSettings: {
        visible: true,
        position:'Top'
    },
    leafItemSettings: {
        labelPath: 'Car'
     },
}, '#container');

```

{% endtab %}

## Tooltip with Rtl support

If the `enableRtl` property is set to true, the tooltip data will be rendered in reverse direction.

The following example shows the format of the tooltip.

{% tab template= "treemap/internationalization",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "es5RtlTooltip" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapTooltip } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapTooltip);

let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    palette:['#71B081','#5A9A77', '#498770', '#39776C', '#266665','#124F5E'],
     tooltipSettings: {
            visible: true,
            format:'${count} : ${fruit}'
    },
    leafItemSettings: {
        labelPath: 'fruit'
     }
}, '#container');

```

{% endtab %}

## Treemap Item Rendering Direction

By default, the direction of tree map item is `TopLeftBottomRight`. You can customize the rendering direction of the tree map item by setting the `renderDirection` property.
The TreeMap can be rendered in the following four different directions.
      `TopLeftBottomRight`
      `TopRightBottomLeft`
      `BottomRightTopLeft`
      `BottomLeftTopRight`

The following example demonstrate how to render the treemap in the RTL direction with `TopLeftBottomRight`.

{% tab template= "treemap/internationalization",sourceFiles="index.ts,index.html", isDefaultActive=true , es5Template = "es5TopLeftBottomRight" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapTooltip } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapTooltip);

let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    palette:['#71B081','#5A9A77', '#498770', '#39776C', '#266665','#124F5E'],
    renderDirection:'TopLeftBottomRight',
    leafItemSettings: {
        labelPath: 'fruit'
     }
}, '#container');

```

{% endtab %}

The following example demonstrate how to render the treemap in the RTL direction with `TopRightBottomLeft`.

{% tab template= "treemap/internationalization", sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "es5TopRightBottomLeft" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapTooltip } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapTooltip);

let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    palette:['#71B081','#5A9A77', '#498770', '#39776C', '#266665','#124F5E'],
    renderDirection:'TopRightBottomLeft',
    leafItemSettings: {
        labelPath: 'fruit'
     }
}, '#container');

```

{% endtab %}

The following example demonstrate how to render the treemap in the RTL direction with `BottomRightTopLeft`.

{% tab template= "treemap/internationalization",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "es5BottomRightTopLeft" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapTooltip } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapTooltip);

let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    palette:['#71B081','#5A9A77', '#498770', '#39776C', '#266665','#124F5E'],
    renderDirection:'BottomRightTopLeft',
    leafItemSettings: {
        labelPath: 'fruit'
     }
}, '#container');

```

{% endtab %}

The following example demonstrate how to render the treemap in the RTL direction with `BottomLeftTopRight`.

{% tab template= "treemap/internationalization", sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "es5BottomLeftTopRight" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapTooltip } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapTooltip);

let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    palette:['#71B081','#5A9A77', '#498770', '#39776C', '#266665','#124F5E'],
    renderDirection:'BottomLeftTopRight',
    leafItemSettings: {
        labelPath: 'fruit'
     }
}, '#container');

```

{% endtab %}