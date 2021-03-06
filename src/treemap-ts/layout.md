# Layout

You can determine the visual representation of nodes belonging to all the tree map levels using the [`layoutType`] property. The available layout types are,

* Squarified
* SliceAndDiceVertical
* SliceAndDiceHorizontal
* SliceAndDiceAuto

## Squarified

Squarified layout displays the nested rectangles based on aspect ratio in tree map. The rectangles will be split based on height and width of parent. The default rendering type of layout is [`Squarified`].

{% tab template= "treemap/layout", sourceFiles="index.ts,index.html", es5Template="es5Squarified" %}

```typescript
import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
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
        weightValuePath: 'GDP'
}, '#container');

```

{% endtab %}

## SliceAndDiceVertical

SliceAndDiceVertical layout creates rectangles with high aspect ratio and displays them sorted vertically.

{% tab template= "treemap/layout", sourceFiles="index.ts,index.html", es5Template="es5SliceVertical" %}

```typescript

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
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
        layoutType : 'SliceAndDiceVertical',
        weightValuePath: 'GDP'
}, '#container');

```

{% endtab %}

## SliceAndDiceHorizontal

SliceAndDiceHorizontal layout creates rectangles with high aspect ratio and displays them sorted horizontally.

{% tab template= "treemap/layout", sourceFiles="index.ts,index.html", es5Template="es5SliceHorizontal" %}

```typescript

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
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
        layoutType : 'SliceAndDiceHorizontal',
        weightValuePath: 'GDP'
}, '#container');

```

{% endtab %}

## SliceAndDiceAuto

SliceAndDiceAuto layout creates rectangles with high aspect ratio and displays them sorted both horizontally and vertically.

{% tab template= "treemap/layout", sourceFiles="index.ts,index.html", es5Template="es5SliceAuto" %}

```typescript

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
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
        layoutType : 'SliceAndDiceAuto',
        weightValuePath: 'GDP'
}, '#container');

```

{% endtab %}