# User Interactions

Options like zooming, panning, single click and double click, highlight and map selection enables the effective interaction on Map elements.

## Zooming

The zooming feature enables you to zoom in and out the Map to show in-depth information. It is controlled by the `zoomFactor` property of the `zoomSettings` of the map. When the zoomFactor is increased, the Map is zoomed in. When the zoomFactor is decreased, then the Map is zoomed out.

### Enable Zooming

To enable the zooming feature, set the `zoomSettings.enable` as true in maps. Zooming feature needs the `Zoom` module injection to perform zooming actions, use module injection to inject zoom into Maps by using `Maps.Inject(Zoom)` method.

### Enable panning

To enable the panning feature, set the [`enablePanning`](../api/maps/zoomSettings/#enablepanning) property of [`zoomSettings`](../api/maps/zoomSettings) to **true**.

```typescript
import { world_map } from './world-map.ts';
import { Maps, Zoom } from '@syncfusion/ej2-maps';
Maps.Inject(Zoom);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
    }],
    zoomSettings:{
        enable:true,
        enablePanning:true
    }
});

```

### Various type of zooming

Zooming can be performed by various types. click zooming, double click zooming, toolbar zooming
rectangular zooming, mouse wheel zooming and pinch zooming.

Refer the [`API`](../api/maps/zoomSettingsModel) links for Zooming.

```typescript
import { usmap } from 'usa.ts';
import { Maps, Zoom } from '@syncfusion/ej2-maps';
Maps.Inject(Zoom);
let map: Maps = new Maps({
    zoomSettings: {
        enable: true,
    },
    layers: [{
        shapeData: usmap,
    }]
});
map.appendTo('#element');
```

## Selection

Each shape in the Map can be selected and deselected during interaction with the shapes.

By tapping on the specific legend, the shapes which are bounded to the selected legend is also selected and vice versa.

The layer `selectionSettings.fill` property is used to change the selected layer shape color. The `selectionSettings.border.color` and `selectionSettings.border.width` properties are used to customize the selected shape border.

You can select the shape by tapping the shape. The Single selection is enabled by the `selectionSettings.enable` property of shape layer. When `selectionSettings.enable` is set to false, the shapes cannot be selected.

Refer the [`API`](../api/maps/selectionSettingsModel) and code snippet for Selection.

**Note:** Selection is separate module, need to inject to work on Selection.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html,index.css" , isDefaultActive=true , es5Template = "selection" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Selection } from '@syncfusion/ej2-maps';
Maps.Inject(Selection);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        selectionSettings: {
            enable: true,
            fill: 'green',
            border: { color: 'white', width: 2}
        }
    }]
});
map.appendTo('#element');
```

{% endtab %}

## Highlight

Each shape in the Map can be highlighted during mouse over on the shapes.

Hovering on the specific legend, the shapes which are bounded to the selected legend is also highlighted and vice versa.

The layer `highlightSettings.fill` property is used to change the highlighted layer shape color. The `highlightSettings.border.color` and `highlightSettings.border.width` properties are used to customize the highlighted shape border.

You can highlight the shape by mouse over on the shape. The highlight is enabled by the `highlightSettings.enable` property of shape layer. When `highlightSettings.enable` is set to false, the shapes cannot be highlighted.

**Note:** Highlight is separate module, need to inject to work on Highlight.

Refer the [`API`](../api/maps/highlightSettingsModel) and code snippet for Highlight.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html,index.css" , isDefaultActive=true , es5Template = "highlight" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Highlight } from '@syncfusion/ej2-maps';
Maps.Inject(Highlight);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        highlightSettings: {
            enable: true,
            fill: 'green',
            border: { color: 'white', width: 2}
        }
    }]
});
map.appendTo('#element');
```

 {% endtab %}

## Tooltip

Tooltip used to get more information about layer or bubble or marker on mouse over or touch end event performing on that. Tooltip is a separate module, So it needs module injection to work maps tooltip. Using Maps.Inject(MapsTooltip) method you can inject maps tooltip module into maps.

Tooltip can be enabled separately for layer or bubble or marker by using `tooltipSettings.visible` as **true**. Tooltip `valuePath` value need to set to display dataSource which field as tooltip text.
Below code snippet illustrate the tooltip enabled for layer to show shape data name field.

Refer the [`API`](../api/maps/tooltipSettingsModel) for Tooltip feature.

**Step: 1** Import the usmap geo json data from already created WorldMap.ts file and assign to `shapeData`.

**Step: 2** Import MapsTooltip module from `ej2-maps` package and Inject to Maps.

**Step: 3** Enable tooltip for layer using `tooltipSettings.visible` as true and bind `valuePath` value as 'name'.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html,index.css" , isDefaultActive=true , es5Template = "tooltip" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, MapsTooltip } from '@syncfusion/ej2-maps';
Maps.Inject(MapsTooltip);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        tooltipSettings: {
            visible: true,
            valuePath: 'name'
        }
    }]
});
map.appendTo('#element');
```

{% endtab %}

## See Also

* [Center position zooming](../maps/how-to/zooming)
* [Tooltip for marker](../maps/how-to/marker-type)
* [Navigating to particular country](../maps/how-to/navigation-line)