# Bubble

Bubbles in the Maps control represent the underlying data values of the map. Bubbles are scattered throughout the map shapes that contains bound values.

Bubbles are included when data binding and the `bubbleSettings` is set to the shape layers.

To add bubbles to the map, bind data source to the layer `bubbleSettings` and set the `valuePath` as population. Following example illustrates bubble enable for the World map with **datasource**.
To render bubble in maps need to inject `Bubble` module using `Maps.Inject(Bubble)` method.

```typescript
export let world_map = // paste the World map from WorldMap.json Geo json file.
```

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "bubble" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Bubble } from '@syncfusion/ej2-maps';
Maps.Inject(Bubble);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        bubbleSettings: [{
            visible: true,
            minRadius: 20,
            dataSource: [
                { name: 'India', population: '38332521' },
                { name: 'New Zealand', population: '19651127' },
                { name: 'Pakistan', population: '3090416' }
            ],
            maxRadius: 40,
            valuePath: 'population'
        }]
    }]
});
map.appendTo('#element');
```

{% endtab %}

## Bubble Sizing

Using the `minRadius` and `maxRadius` properties in `bubbleSettings`, you can render the bubbles in different sizes based on the `valuePath` and `dataSource` values

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "bubbleSizing" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Bubble } from '@syncfusion/ej2-maps';
Maps.Inject(Bubble);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        bubbleSettings: [{
            visible: true,
            minRadius: 5,
            dataSource: [
                { name: 'India', population: '38332521' },
                { name: 'New Zealand', population: '19651127' },
                { name: 'Pakistan', population: '3090416' }
            ],
            maxRadius: 80,
            valuePath: 'population'
        }]
    }]
});
map.appendTo('#element');
```

{% endtab %}

## Multiple bubble groups

You can specify multiple types of bubble groups using the `bubbleSettings` property and customize it according to your requirement.

In the following code example, the gender-wise population ratio is demonstrated with two different bubble groups.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "bubbleGroup" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Bubble } from '@syncfusion/ej2-maps';
Maps.Inject(Bubble);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        bubbleSettings: [{
            visible: true,
            minRadius: 5,
            valuePath: "femaleRatio"
            colorValuePath: "femaleRatioColor"
            dataSource: [
                {
                    country: "United States", femaleRatio: 50.50442726, maleRatio: 49.49557274, femaleRatioColor: "green", maleRatioColor: "blue"
                },
                {
                    country: "India", femaleRatio: 48.18032713, maleRatio: 51.81967287, femaleRatioColor: "blue", maleRatioColor: "#c2d2d6"
                },
                {
                    country: "Oman", femaleRatio: 34.15597234, maleRatio: 65.84402766, femaleRatioColor: "#09156d", maleRatioColor: "orange"
                },
                {
                    country: "United Arab Emirates", femaleRatio: 27.59638942, maleRatio: 72.40361058, femaleRatioColor: "#09156d", maleRatioColor: "orange"
                }
            ],
            maxRadius: 20,
        },
        {
            visible: true,
            bubbleType: 'Circle'
            opacity: 0.4,
            minRadius: 15,
            valuePath: "maleRatio",
            colorValuePath: "maleRatioColor",
            dataSource: [
                {
                    country: "United States", femaleRatio: 50.50442726, maleRatio: 49.49557274, femaleRatioColor: "green", maleRatioColor: "blue"
                },
                {
                    country: "India", femaleRatio: 48.18032713, maleRatio: 51.81967287, femaleRatioColor: "blue", maleRatioColor: "#c2d2d6"
                },
                {
                    country: "Oman", femaleRatio: 34.15597234, maleRatio: 65.84402766, femaleRatioColor: "#09156d", maleRatioColor: "orange"
                },
                {
                    country: "United Arab Emirates", femaleRatio: 27.59638942, maleRatio: 72.40361058, femaleRatioColor: "#09156d", maleRatioColor: "orange"
                }
            ],
            maxRadius: 25,
        }]
    }]
});
map.appendTo('#element');
```

{% endtab %}

## Enable Legend for Bubble

To enable the legend for the bubble, need to set `legendSettings.visible` as true and `legendSettings.type` as 'Bubbles'. To render the legend in maps need to Inject Legend module using `Maps.Inject(Legend)` method.
Refer the below code snippet to enable the legend for bubbles with each bubble different colors rendering.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "bubble" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Bubble, Legend} from '@syncfusion/ej2-maps';
Maps.Inject(Bubble, Legend);
let map: Maps = new Maps({
    legendSettings: {
      visible: true,
      type: 'Bubbles'
    },
    layers: [{
        shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        bubbleSettings: [{
            visible: true,
            minRadius: 20,
            dataSource: [
                {color: 'green', name: 'India', population: '38332521' },
                {color: 'purple', name: 'New Zealand', population: '19651127' },
                {color: 'blue', name: 'Pakistan', population: '3090416' }
            ],
            maxRadius: 40,
            colorValuePath: 'color',
            valuePath: 'population'
        }]
    }]
});
map.appendTo('#element');
```

{% endtab %}

Refer the [`API`](../api/maps/bubbleSettingsModel/) for Bubble feature.