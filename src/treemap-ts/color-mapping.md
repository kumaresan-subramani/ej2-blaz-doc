# Color Mapping

Color mapping is used to customize each group or item colors based on specified types of color mappings.

The following options are available to customize the group and leaf items in the tree map control.

## Range color mapping

Range color mapping is used to apply color to items by giving specific ranges in the dataSource. You should specify the datasource field in, the [`rangeColorValuePath`] property.

The following code example shows applying range color mapping.

{% tab template= "treemap/colormapping", sourceFiles="index.ts,index.html", es5Template="es5RangeColorMapping" %}

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
     },
}, '#container');

```

{% endtab %}

## Equal color mapping

Equal color mapping is used to fill colors to each item by specifying equal value present in the datasource field that can be specified in the [`equalColorValuePath`] property.

The following code example shows applying equal color mapping.

{% tab template= "treemap/colormapping", sourceFiles="index.ts,index.html", es5Template="es5EqualColorMapping" %}

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

## Desaturation color mapping

Desaturation color mapping is used to apply colors with opacity to items based on the given values for the [`minOpacity`] and [`maxOpacity`] properties in the tree map control.

The following code example shows applying desaturation color mapping.

{% tab template= "treemap/colormapping", sourceFiles="index.ts,index.html",  es5Template="es5DesaturationColorMapping" %}

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
    leafItemSettings: {
        labelPath: 'fruit',
        colorMapping:[
            {
               from:500,
               to:3000,
               minOpacity:0.2,
               maxOpacity:0.5,
               color:'orange'
           },
           {
               from:3000,
               to:5000,
               minOpacity:0.5,
               maxOpacity:0.8,
               color:'green'
           }
        ]
     }
}, '#container');

```

{% endtab %}

## Palette color mapping

Palette color mapping is used to fill the same color to each group or leaf node by given colors in the [`palette`] property in tree map control.

The following code example shows applying  palette color mapping.

{% tab template= "treemap/colormapping", sourceFiles="index.ts,index.html", es5Template="es5PaletteColorMapping" %}

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
    palette:['red','green'],
    weightValuePath: 'count',
    leafItemSettings: {
        labelPath: 'Car'
     }
}, '#container');

```

{% endtab %}

## Desaturation with multiple colors

Multiple colors are used as gradient effect to specific shapes based on the ranges in datasource.

By using color API, you can set n number of colors.

The following code example shows how to use multiple colors.

{% tab template= "treemap/colormapping", sourceFiles="index.ts,index.html", es5Template="es5ColorMappingWithMultipleColors" %}

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
               color:['orange','pink']
           },
           {
               from:3000,
               to:5000,
               color:['green','red','blue']
           }
        ]
     }
}, '#container');

```

{% endtab %}

## Color for items excluded from color mapping

Based on the ranges in the data source, get the excluded ranges from color mapping, and then apply specific color to the items.

The following code example shows how to set the color for items excluded from color mapping.

{% tab template= "treemap/colormapping", sourceFiles="index.ts,index.html", es5Template="es5ColorMappingWithExcludeColor" %}

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
        visible: true
    },
    leafItemSettings: {
        labelPath: 'fruit',
        colorMapping:[
            {
               from:500,
               to:2500,
               color:'orange'
           },
           {
               from:3000,
               to:4000,
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

## Bind the colors to the items from data source

To set color for each items in treemap, bind the field name in the data source to the `rangeColorValuePath`.

The following code example shows to set the color for treemap items.

{% tab template= "treemap/colormapping", sourceFiles="index.ts,index.html", es5Template="es5BindColorFromDS" %}

```typescript

let fruits:Object[] = [{ fruit:'Apple', count:5000, color: 'red'},
                       { fruit:'Mango', count:3000, color:'blue'},
                       { fruit:'Orange', count:2300, color:'green' },
                       { fruit:'Banana', count:500, color:'yellow' },
                       { fruit:'Grape', count:4300, color:'orange' },
                       { fruit:'Papaya', count:1200, color:'pink' },
                       { fruit:'Melon', count:4500, color:'violet' }
                     ];

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
    dataSource: fruits ,
    weightValuePath: 'count',
    colorValuePath:'color',
    leafItemSettings: {
        labelPath: 'fruit',
     }
}, '#container');

```

{% endtab %}