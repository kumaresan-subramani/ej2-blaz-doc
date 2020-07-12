# Legend

Legend is used to provide valuable information for interpreting what the tree map is displaying and can be represented in various colors, shapes or other identifiers based on data.

## Position and alignment

Legend position is used to place legend in various positions. Based on the legend position, the legend item will be aligned. For example, if the position is top or bottom, the legend items are placed by rows. If the position is left or right, the legend items are placed by columns.

The following options are available to customize the legend position:

* Top
* Bottom
* Left
* Right
* Float

The following code example shows the legend position.

{% tab template= "treemap/legend", sourceFiles="index.ts,index.html", es5Template="es5LegendPosition" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapLegend } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapLegend);
let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    rangeColorValuePath:'count',
    legendSettings: {
        visible: true,
        position: 'Top'
    },
    leafItemSettings: {
        labelPath: 'fruit',
        colorMapping:[
            {
               from:500,
               to:3000,
               color:'orange'
           },
           {
               from:3000,
               to:5000,
               color:'green'
           }
        ]
     }
}, '#container');

```

{% endtab %}

Legend Alignment is used to align the legend items in specific location. The following options are available to customize the legend alignment:

* Near
* Center
* Far

The following code example shows legend alignment.

{% tab template= "treemap/legend", sourceFiles="index.ts,index.html", es5Template="es5LegendAlignment" %}

```typescript
let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap, TreeMapLegend } from '@syncfusion/ej2-treemap';
TreeMap.Inject(TreeMapLegend);
let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    rangeColorValuePath:'count',
    legendSettings: {
        visible: true,
        alignment:'Far',
    },
    leafItemSettings: {
        labelPath: 'fruit',
        colorMapping:[
            {
               from:500,
               to:3000,
               color:'orange'
           },
           {
               from:3000,
               to:5000,
               color:'green'
           }
        ]
     }
}, '#container');

```

{% endtab %}

## Legend mode

The tree map control supports two different types of legend rendering modes such as `Default` and `Interactive`.

<!-- markdownlint-disable MD036 -->

**Default mode**

In default mode, legends have symbols with legend labels that are used to identify the items in tree map control.

The following code example shows the default mode of legends.

{% tab template= "treemap/legend", sourceFiles="index.ts,index.html", es5Template="es5LegendDefaultMode" %}

```typescript
let CarDetails:Object[] = [{ Car:'Mustang', Brand:'Ford', count:232 },
                       { Car:'EcoSport', Brand:'Ford', count:121 },
                       { Car:'Swift', Brand:'Maruti', count:143 },
                       { Car:'Baleno', Brand:'Maruti', count:454 },
                       { Car:'Vitara Brezza', Brand:'Maruti', count:545 },
                       { Car:'A3 Cabriolet', Brand:'Audi',count:123 },
                       { car:'RS7 Sportback', Brand:'Audi', count:523 }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: CarDetails ,
    weightValuePath: 'count',
    equalColorValuePath:'Brand',
    legendSettings: {
        visible: true,
        position:'Top',
        border:{color:'black',width:2}
    },
    leafItemSettings: {
        labelPath: 'Car',
        colorMapping:[
            {
               value:'Ford',
               color:'green'
           },
           {
               value:'Audi',
               color:'red'
           },
           {
               value:'Maruti',
               color:'orange'
           }
        ]
     },
}, '#container');

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

**Interactive mode**

The legends can be made interactive with an arrow mark that indicates exact range color in legend when the mouse hovers over the corresponding shape. You can enable this option by setting the mode property in legendSettings value to “Interactive”. The default value of the mode property is “Default” to enable normal legend.

The following code example shows the interactive mode of legends.

{% tab template= "treemap/legend", sourceFiles="index.ts,index.html", es5Template="es5LegendInteractiveMode" %}

```typescript
let CarDetails:Object[] = [{ Car:'Mustang', Brand:'Ford', count:232 },
                       { Car:'EcoSport', Brand:'Ford', count:121 },
                       { Car:'Swift', Brand:'Maruti', count:143 },
                       { Car:'Baleno', Brand:'Maruti', count:454 },
                       { Car:'Vitara Brezza', Brand:'Maruti', count:545 },
                       { Car:'A3 Cabriolet', Brand:'Audi',count:123 },
                       { car:'RS7 Sportback', Brand:'Audi', count:523 }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: CarDetails ,
    weightValuePath: 'count',
    equalColorValuePath:'Brand',
    legendSettings: {
        visible: true,
        mode:'Interactive',
        position:'Top',
        border:{color:'black',width:2}
    },
    leafItemSettings: {
        labelPath: 'Car',
        colorMapping:[
            {
               value:'Ford',
               color:'green'
           },
           {
               value:'Audi',
               color:'red'
           },
           {
               value:'Maruti',
               color:'orange'
           }
        ]
     },
}, '#container');

```

{% endtab %}

## Legend size

You can customize the legend size by modifying the [`height`] and [`width`] properties in the legendSettings. It accepts values in both percentage and pixel. If the value is specified in percentage for height or width, the legend height will be calculated for overall height.

Legend size is shown in the following example.

{% tab template= "treemap/legend", sourceFiles="index.ts,index.html", es5Template="es5LegendSize" %}

```typescript
let CarDetails:Object[] = [{ Car:'Mustang', Brand:'Ford', count:232 },
                       { Car:'EcoSport', Brand:'Ford', count:121 },
                       { Car:'Swift', Brand:'Maruti', count:143 },
                       { Car:'Baleno', Brand:'Maruti', count:454 },
                       { Car:'Vitara Brezza', Brand:'Maruti', count:545 },
                       { Car:'A3 Cabriolet', Brand:'Audi',count:123 },
                       { car:'RS7 Sportback', Brand:'Audi', count:523 }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: CarDetails ,
    weightValuePath: 'count',
    equalColorValuePath:'Brand',
    legendSettings: {
        visible: true,
        height:'50px',
        width:'200px',
        position:'Top',
        border:{color:'black',width:2}
    },
    leafItemSettings: {
        labelPath: 'Car',
        colorMapping:[
            {
               value:'Ford',
               color:'green'
           },
           {
               value:'Audi',
               color:'red'
           },
           {
               value:'Maruti',
               color:'orange'
           }
        ]
     },
}, '#container');

```

{% endtab %}

**Paging support**

The tree map supports the legend paging. Legend paging will be enabled if the legend items cannot placed within provided height and width.

The following code example shows enabling legend paging.

{% tab template= "treemap/legend", sourceFiles="index.ts,index.html", es5Template="es5LegendPaging" %}

```typescript
let CarDetails:Object[] = [{ Car:'Mustang', Brand:'Ford', count:232 },
                       { Car:'EcoSport', Brand:'Ford', count:121 },
                       { Car:'Swift', Brand:'Maruti', count:143 },
                       { Car:'Baleno', Brand:'Maruti', count:454 },
                       { Car:'Vitara Brezza', Brand:'Maruti', count:545 },
                       { Car:'A3 Cabriolet', Brand:'Audi',count:123 },
                       { car:'RS7 Sportback', Brand:'Audi', count:523 }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: CarDetails ,
    weightValuePath: 'count',
    equalColorValuePath:'Brand',
    legendSettings: {
        visible: true,
        height:'50px',
        width:'100px',
        border:{color:'black',width:2}
    },
    leafItemSettings: {
        labelPath: 'Car',
        colorMapping:[
            {
               value:'Ford',
               color:'green'
           },
           {
               value:'Audi',
               color:'red'
           },
           {
               value:'Maruti',
               color:'orange'
           }
        ]
     }
}, '#container');

```

{% endtab %}

## Legend for items excluded from color mapping

Based on the ranges in the data source, get the excluded ranges from color mapping, and then show the legend with excluded range values are bound to the specific legend.

The following code example shows how to set the color for items excluded from color mapping.

{% tab template= "treemap/legend", sourceFiles="index.ts,index.html", es5Template="es5LegendExcludeColorMapping" %}

```typescript

let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    rangeColorValuePath:'count',
    legendSettings:{
        visible:true
    },
    leafItemSettings: {
        labelPath: 'fruit',
        colorMapping:[
            {
               from:500,
               to:2500,
               minOpacity:0.2,
               maxOpacity:0.5,
               color:'orange'
           },
           {
               from:3000,
               to:4000,
               minOpacity:0.5,
               maxOpacity:0.8,
               color:'green'
           },
           {
               color:'red'
           }
        ]
     }
}, '#container');

```

{% endtab %}

## Hide desired legend items

To enable or disable the desired legend for each colormapping,set the `showLegend` property to `true` in `colorMapping`.

The following code example shows to hide the desired legend.

{% tab template= "treemap/legend", sourceFiles="index.ts,index.html", es5Template="es5HideDesiredLegend" %}

```typescript

let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    rangeColorValuePath:'count',
    legendSettings:{
        visible:true
    },
    leafItemSettings: {
        labelPath: 'fruit',
        colorMapping:[
            {
               from:500,
               to:2500,
               color:'orange',
               showLegend: true
           },
           {
               from:3000,
               to:4000,
               color:'green',
               showLegend: false
           },
           {
               color:'red',
               showLegend: true
           }
        ]
     }
}, '#container');

```

{% endtab %}

## Hide legend items based data source value

To enable or disable the legend visibility for each item, bind the field name in the data source to the `showLegendPath` property in `legendSettings`.

The following code example shows how to hide legend items based on data source value.

{% tab template= "treemap/legend", sourceFiles="index.ts,index.html", es5Template="es5HideLegendFromDS" %}

```typescript

let fruits:Object[] = [{ fruit:'Apple', count:5000, visibility: true , color: '#71B081' },
                       { fruit:'Orange', count:3000, visibility: false, color: '#5A9A77' },
                       { fruit:'Grape', count:2300, visibility: true, color: '#498770' },
                       { fruit:'Banana', count:500, visibility: false, color: '#39776C' },
                       { fruit:'Mango', count:4300, visibility: true, color: '#266665' },
                       { fruit:'Papaya', count:1200, visibility: false, color: '#124F5E' }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    colorValuePath: 'color',
    palette: [],
    legendSettings:{
        visible:true,
        showLegendPath:'visibility'
    },
    leafItemSettings: {
        labelPath: 'fruit',
     }
}, '#container');

```

{% endtab %}

## Bind legend item text from data source

To show the legend text based on binding, the field name in the datasource should be set to the `valuePath` property in `legendSettings`.

{% tab template= "treemap/legend", sourceFiles="index.ts,index.html", es5Template="es5LegendTextFromDS" %}

```typescript

let fruits:Object[] = [{ fruit:'Apple', count:5000, visibility: true , color: '#71B081' },
                       { fruit:'Orange', count:3000, visibility: false, color: '#5A9A77' },
                       { fruit:'Grape', count:2300, visibility: true, color: '#498770' },
                       { fruit:'Banana', count:500, visibility: false, color: '#39776C' },
                       { fruit:'Mango', count:4300, visibility: true, color: '#266665' },
                       { fruit:'Papaya', count:1200, visibility: false, color: '#124F5E' }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    colorValuePath: 'color',
    palette: [],
    legendSettings:{
        visible:true,
        valuePath:'fruit'
    },
    leafItemSettings: {
        labelPath: 'fruit',
     }
}, '#container');

```

{% endtab %}

## Hide duplicate legend items

To enable or disable the duplicate legend items, set the  `removeDuplicateLegend` property to `true` in `legendSettings`.

{% tab template= "treemap/legend", sourceFiles="index.ts,index.html", es5Template="es5RemoveDuplicateLegend" %}

```typescript

let fruits:Object[] = [{ fruit:'Apple', count:5000, visibility: true , color: '#71B081' },
                       { fruit:'Grape', count:3000, visibility: false, color: '#5A9A77' },
                       { fruit:'Apple', count:2300, visibility: true, color: '#498770' },
                       { fruit:'Banana', count:500, visibility: false, color: '#39776C' },
                       { fruit:'Grape', count:4300, visibility: true, color: '#266665' },
                       { fruit:'Papaya', count:1200, visibility: false, color: '#124F5E' }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    colorValuePath:'color',
    palette: [],
    legendSettings:{
        visible:true,
        valuePath:'fruit',
        removeDuplicateLegend: true
    },
    leafItemSettings: {
        labelPath: 'fruit',
     }
}, '#container');

```

{% endtab %}

## Legend Responsiveness

Use a responsive legend that switches positions between the right and bottom based on the available height and width. To enable the responsive legend, set the `position` property to `auto` in the `legendSettings` API, and the legend position is changed based on available height and width.

In the following sample, the  responsive legend is shown.

{% tab template= "treemap/colormapping", sourceFiles="index.ts,index.html", es5Template="es5LegendResponsive" %}

```typescript

let fruits:Object[] = [{ fruit:'Apple', count:5000 },
                       { fruit:'Grape', count:3000 },
                       { fruit:'Apple', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    palette:['#71B081','#5A9A77', '#498770', '#39776C', '#266665','#124F5E'],
    width: '700px',
    height: '500px',
    legendSettings:{
        visible:true,
        position:'Auto'
    },
    leafItemSettings: {
        labelPath: 'fruit',
     }
}, '#container');

```

{% endtab %}
