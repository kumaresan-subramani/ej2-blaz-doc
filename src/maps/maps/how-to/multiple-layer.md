# Adding multiple layers in map

The multilayer support allows loading multiple shape files in a single container and enables maps to display more information.

Initialize the map component with SubLayer option by using the `type` property. The shape layer is the core layer of the map. Multiple layers can be added in a shape layer as sublayers as mentioned in the following code example. To know more about multiple layers, please refer to the [`API`](../../api/maps/layerSettings/) documentation.

{% tab template= "maps/default-map", sourceFiles="index.ts,index.html" , es5Template="layers" %}

```typescript
import { usa_map } from './usa.ts';
import { california } from './california.ts';
import { texas } from './texas.ts';
import { Maps } from '@syncfusion/ej2-maps';

// initialize Maps component
let map: Maps = new Maps({
        layers: [
        {
            shapeData: usa_map,
            shapeSettings: {
                fill: '#E5E5E5',
                border: {
                    color: 'black',
                    width: 0.1
                }
            }
        },
        {
            shapeData: texas,
            type: 'SubLayer',
            shapeSettings: {
                fill: 'rgba(141, 206, 255, 0.6)',
                border: {
                    color: '#1a9cff',
                    width: 0.25
                }
            }
        },
        {
            shapeData: california,
            type: 'SubLayer',
            shapeSettings: {
                fill: 'rgba(141, 206, 255, 0.6)',
                border: {
                    color: '#1a9cff',
                    width: 0.25
                }
            }
        }
    ]
}, '#element');
```

{% endtab %}
