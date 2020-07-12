# TreeMapModel

Interface for a class TreeMap

## Properties

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

### background `string`

Specifies the background.

### border [`BorderModel`](./api-borderModel.html)

Specifies the border of tree map.

### dataSource `DataManager` &#124;  [`TreeMapAjax`](./api-treeMapAjax.html) &#124;  `Object[]`

Specifies the dataSource.

### description `string`

Description for maps.

### enableDrillDown `boolean`

To enable or disable the drillDown.

### enablePersistence `boolean`

Enable or disable persisting component's state between page reloads.

### enableRtl `boolean`

Enable or disable rendering component in right to left direction.

### equalColorValuePath `string`

Specifies the colorValuePath

### format `string`

To apply internationalization for treemap

### height `string`

Specifies the height by given pixel or percentage.

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

### margin [`MarginModel`](./api-marginModel.html)

Specifies the margin to move the render area.

### palette `string[]`

Specifies the palette colors.

### query `Query`

Specifies the query for filter the data.

### rangeColorValuePath `string`

Specifies the colorValuePath

### selectionSettings [`SelectionSettingsModel`](./api-selectionSettingsModel.html)

To specifies the selection settings.

### tabIndex `number`

TabIndex value for treemap.

### theme `string`

Specifies the theme.

### titleSettings [`TitleSettingsModel`](./api-titleSettingsModel.html)

Specifies the title for tree map.

### tooltipSettings [`TooltipSettingsModel`](./api-tooltipSettingsModel.html)

Specifies the tooltip settings.

### useGroupingSeparator `boolean`

To enable the separator

### weightValuePath `string`

Specifies the weight value path

### width `string`

Specifies the width by given pixel or percentage.
