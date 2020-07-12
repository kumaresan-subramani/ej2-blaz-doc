# Drill-down

By clicking a continent, you can view all the countries available in that continent using the drill-down feature. For example, the countries in the `Africa` continent have been showcased here. You can showcase all the countries in `Africa` continent by clicking the [shapeSelected](../../api/maps/) event as mentioned in the following code example.
<!-- markdownlint-disable MD031 -->
{% tab template= "maps/default-map", sourceFiles="index.ts,index.html" , es5Template="drill" %}

```typescript
import { world_map } from './world-map.ts';
import { Africa_Continent } from './Africa_Continent.ts';
import { default_data } from './data.ts';
import { Maps,Highlight,IShapeSelectedEventArgs,shapeSelected,Marker} from '@syncfusion/ej2-maps';
Maps.Inject(Highlight,Marker );

export interface ShapeData {
    continent?: string;
}

// initialize Maps component
let map: Maps = new Maps({
    shapeSelected: (args: IShapeSelectedEventArgs): void => {
        let shape: string = (args.shapeData as ShapeData).continent;
        if (shape === 'Africa') {
            map.baseLayerIndex = 1;
            map.refresh();
        }
    },
        layers: [
        {
            layerType: 'Geometry',
            shapeData: world_map,
            shapePropertyPath: 'continent',
            shapeDataPath: 'continent',
            dataSource:default_data,
            shapeSettings: {
                colorValuePath: 'drillColor'
            },
            markerSettings: [       {
                visible: true,
                template: '<div id="marker3" class="markerTemplate">Africa' +
                    '</div>',
                dataSource: [
                    { latitude: 10.97274101999902, longitude: 16.390625 }
                ],
                animationDuration: 0
            }
        ]
        },
        {
            layerType: 'Geometry',
            shapeData: Africa_Continent,
            shapeSettings: {
                fill: '#80306A'
            },
            highlightSettings: {
                enable: true,
                fill: '#80306A'
            }
        }

    ]
},);
map.appendTo('#element');

```
{% endtab %}

```html
<div id="mapdrilldown"></div>
  <style>
     .markerTemplate {
        font-size: 12px;
        color: white;
        text-shadow: 0px 1px 1px black;
        font-weight: 500
    }
    .markerTemplate {
        height: 30px;
        width: 30px;
        display: block;
        margin: auto;
    }
  </style>
```