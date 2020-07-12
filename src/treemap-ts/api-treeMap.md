# TreeMap

Represents the TreeMap control.
```html
<div id="container"/>
<script>
  var treemap = new TreeMap();
  treemap.appendTo("#container");
</script>
```

## Properties

### background `string`

Specifies the background.

### border [`BorderModel`](./api-borderModel.html)

Specifies the border of tree map.

### dataSource `DataManager` &#124;  [`TreeMapAjax`](./api-treeMapAjax.html) &#124;  `Object[]`

Specifies the dataSource.

Defaults to *null*

### description `string`

Description for maps.

Defaults to *null*

### enableDrillDown `boolean`

To enable or disable the drillDown.

### enablePersistence `boolean`

Enable or disable persisting component's state between page reloads.

Defaults to *false*

### enableRtl `boolean`

Enable or disable rendering component in right to left direction.

Defaults to *false*

### equalColorValuePath `string`

Specifies the colorValuePath

### format `string`

To apply internationalization for treemap

Defaults to *null*

### height `string`

Specifies the height by given pixel or percentage.

Defaults to *null*

### highlightSettings [`HighlightSettingsModel`](./api-highlightSettingsModel.html)

To specifies the highlight settings.

### initialDrillDown [`InitialDrillSettingsModel`](./api-initialDrillSettingsModel.html)

Specifies the initial drillDown.

### layoutType `string`

Specifies the rendering of layout type.

### leafItemSettings [`LeafItemSettingsModel`](./api-leafItemSettingsModel.html)

Specifies to access all leaf items in levels.

### legendSettings [`LegendSettingsModel`](./api-legendSettingsModel.html)

Specifies the legend settings.

### levels `LevelSettingsModel[]`

Specifies the item levels.

### locale `string`

Overrides the global culture and localization value for this component. Default global culture is 'en-US'.

Defaults to *undefined*

### margin [`MarginModel`](./api-marginModel.html)

Specifies the margin to move the render area.

### palette `string[]`

Specifies the palette colors.

### query `Query`

Specifies the query for filter the data.

Defaults to *null*

### rangeColorValuePath `string`

Specifies the colorValuePath

### selectionSettings [`SelectionSettingsModel`](./api-selectionSettingsModel.html)

To specifies the selection settings.

### tabIndex `number`

TabIndex value for treemap.

Defaults to *1*

### theme `string`

Specifies the theme.

### titleSettings [`TitleSettingsModel`](./api-titleSettingsModel.html)

Specifies the title for tree map.

### tooltipSettings [`TooltipSettingsModel`](./api-tooltipSettingsModel.html)

Specifies the tooltip settings.

### treeMapHighlightModule [`TreeMapHighlight`](./api-treeMapHighlight.html)

`highlightModule` is used for highlight the items.

### treeMapLegendModule [`TreeMapLegend`](./api-treeMapLegend.html)

`legendModule` is used for render the legend items.

### treeMapSelectionModule [`TreeMapSelection`](./api-treeMapSelection.html)

`selectionModule` is used for select the items.

### treeMapTooltipModule [`TreeMapTooltip`](./api-treeMapTooltip.html)

`tooltipModule` is used to render the treemap tooltip.

### useGroupingSeparator `boolean`

To enable the separator

Defaults to *false*

### weightValuePath `string`

Specifies the weight value path

### width `string`

Specifies the width by given pixel or percentage.

Defaults to *null*

## Methods

### addEventListener

Adds the handler to the given event listener.

Returns *void*

### appendTo

Appends the control within the given HTML element

| Parameter | Type | Description |
|------|------|-------------|
| selector (*optional*) |  `string` &#124;  `HTMLElement` | Target element where control needs to be appended<br> |

Returns *void*

### dataBind

When invoked, applies the pending property changes immediately to the component.

Returns *void*

### destroy

To destroy the treemap control.

Returns *void*

### export

Handles the export method for chart control.

Returns *void*

### getModuleName

Get component name

Returns *string*

### print

Handles the print method for chart control.

Returns *void*

### refresh

Applies all the pending property changes and render the component again.

Returns *void*

### removeEventListener

Removes the handler from the given event listener.

Returns *void*

### resizeOnTreeMap

To handle the window resize event on treemap.

Returns *void*

### Inject

Dynamically injects the required modules to the component.

Returns *void*

## Events

### beforePrint [`EmitType<IPrintEventArgs>`](./api-iPrintEventArgs.html)

Triggers before the prints gets started.

### click [`EmitType<IItemClickEventArgs>`](./api-iItemClickEventArgs.html)

Triggers the click event.

### drillEnd [`EmitType<IDrillEndEventArgs>`](./api-iDrillEndEventArgs.html)

Triggers the drillDown end.

### drillStart [`EmitType<IDrillStartEventArgs>`](./api-iDrillStartEventArgs.html)

Triggers the drillDown start.

### itemClick [`EmitType<IItemClickEventArgs>`](./api-iItemClickEventArgs.html)

Triggers the item click.

### itemHighlight [`EmitType<IItemHighlightEventArgs>`](./api-iItemHighlightEventArgs.html)

Triggers the item highlight.

### itemMove [`EmitType<IItemMoveEventArgs>`](./api-iItemMoveEventArgs.html)

Triggers the item move.

### itemRendering [`EmitType<IItemRenderingEventArgs>`](./api-iItemRenderingEventArgs.html)

Triggers before item rendering.

### itemSelected [`EmitType<IItemSelectedEventArgs>`](./api-iItemSelectedEventArgs.html)

Triggers the item selected.

### load [`EmitType<ILoadEventArgs>`](./api-iLoadEventArgs.html)

Triggers before treemap rendered.

### loaded [`EmitType<ILoadedEventArgs>`](./api-iLoadedEventArgs.html)

Triggers after treemap rendered.

### mouseMove [`EmitType<IMouseMoveEventArgs>`](./api-iMouseMoveEventArgs.html)

Triggers the mouse move event.

### resize [`EmitType<IResizeEventArgs>`](./api-iResizeEventArgs.html)

Triggers the resize event.

### tooltipRendering [`EmitType<ITreeMapTooltipRenderEventArgs>`](./api-iTreeMapTooltipRenderEventArgs.html)

Triggers the tooltip rendering.
