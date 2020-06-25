---
title: "Migration from Essential JS 1"
component: "TreeMap"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components especially, treemap component."
---

# Migration from Essential JS 1

This article describes the API migration process of Accordion component from Essential JS 1 to Essential JS 2.

## Data Binding

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Datasource| **Property:** *dataSource*<br/><br/> `<EJ.TreeMap id="treemap" dataSource={[{State:"United States", GDP:17946, percentage:11.08, Rank:1}]} weightValuePath='GDP' leafItemSettings={leaf}></EJ.TreeMap>`<br/>`var leaf={labelPath: 'State'}`|**Property:** *dataSource*<br/><br/> `<TreeMapComponent id="treemap" dataSource={[{State:"United States", GDP:17946, percentage:11.08, Rank:1}]} weightValuePath='GDP' leafItemSettings={labelPath: 'State'}></TreeMapComponent>,`|

## Appearance

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Layout| **Property:** *itemsLayoutMode*<br/><br/> `<EJ.TreeMap id="treemap" itemsLayoutMode= "sliceanddiceauto"></EJ.TreeMap>`|**Property:** *layoutType*<br/><br/> `<TreeMapComponent id="treemap" layoutType= 'SliceAndDiceAuto'></TreeMapComponent>`|
|Weight Value Path| **Property:** *weightValuePath*<br/><br/> `<EJ.TreeMap id="treemap" weightValuePath= "Population" ></EJ.TreeMap>`|**Property:** *weightValuePath*<br/><br/>`<TreeMapComponent id="treemap" weightValuePath= 'Population'></TreeMapComponent>`|
|Range Color Value Path| **Property:** *colorValuePath*<br/><br/> `<EJ.TreeMap id="treemap" colorValuePath= "Continent"></EJ.TreeMap>`|**Property:** *rangeColorValuePath*<br/><br/> `<TreeMapComponent id="treemap"  rangeColorValuePath= 'Continent' ></TreeMapComponent>`|
|Equal Color Value Path| Not Applicable|**Property:** *equalColorValuePath*<br/><br/> `<TreeMapComponent id="treemap" equalColorValuePath= 'Asia' ></TreeMapComponent>`|
|Height| **Property:** *height*<br/><br/> `<EJ.TreeMap id="treemap" height= 50 ></EJ.TreeMap>`|**Property:** *height*<br/><br/> `<TreeMapComponent id="treemap"   height= '50px'  ></TreeMapComponent>`|
|Width| **Property:** *width*<br/><br/> `<EJ.TreeMap id="treemap" width= 400></EJ.TreeMap>`|**Property:** *width*<br/><br/> `<TreeMapComponent id="treemap" width='400px'  ></TreeMapComponent>`|
|Theme| Not Applicable|**Property:** *theme*<br/><br/> `<TreeMapComponent id="treemap" theme= 'Highcontrast' ></TreeMapComponent>`|
|Localization| **Property:** *locale*<br/><br/> `<EJ.TreeMap id="treemap" locale= "en-US"></EJ.TreeMap>`|**Property:** *locale*<br/><br/> `<TreeMapComponent id="treemap"  locale='en-US' ></TreeMapComponent>`|
|Palette Colors| **Property:** *paletteColorMapping.colors*<br/><br/> `<EJ.TreeMap id="treemap" paletteColorMapping="paletteColorMapping"></EJ.TreeMap>`<br/>`var paletteColorMapping={ colors: ['red','green'] }`|**Property:** *palette*<br/><br/>`<TreeMapComponent  palette={['#C33764', '#AB3566']} id="treemap" ></TreeMapComponent>`|
|Margin| Not Applicable|**Property:** *margin*<br/><br/> `<TreeMapComponent id="treemap" ></TreeMapComponent>`|
|Resize| **Property:** *enableResize*<br/><br/>`<EJ.TreeMap id="treemap" enableResize: true></EJ.TreeMap>`|Not Applicable|
|Responsive| **Property:** *isResponsive*<br/><br/> `<EJ.TreeMap id="treemap" isResponsive= true></EJ.TreeMap>`|Not Applicable|

## Leaf Items

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Border Color| **Property:** *leafItemSettings.borderBrush*<br/><br/>`<EJ.TreeMap id="treemap" leafItemSettings ={leafItem} showLabels={true}></EJ.TreeMap>`<br/>`var leafItem={borderBrush: "blue" }`|**Property:** *leafItemSettings.border*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ border: { color: 'white' } }></TreeMapComponent>`|
|Border Width| **Property:** *leafItemSettings.borderThickness*<br/><br/> `<EJ.TreeMap id="treemap" leafItemSettings ={leafItem} showLabels={true}></EJ.TreeMap>`<br/>`var leafItem={  borderThickness: 5}`|**Property:** *leafItemSettings.border*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ border: { width: 5 } }></TreeMapComponent>`|
|Gap Value| **Property:** *leafItemSettings.gap*<br/><br/> `<EJ.TreeMap id="treemap" leafItemSettings ={leafItem} showLabels={true}></EJ.TreeMap>`<br/>`var leafItem={   gap: 5}`|**Property:** *leafItemSettings.gap*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={  gap: 5 }></TreeMapComponent>`|
|Leaf Item Label| **Property:** *leafItemSettings.itemTemplate*<br/><br/> `<EJ.TreeMap id="treemap" leafItemSettings ={leafItem} showLabels={true}></EJ.TreeMap>`<br/>`var leafItem={  itemTemplate: "template"}`|**Property:** *leafItemSettings.labelTemplate*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ labelTemplate: 'template' }></TreeMapComponent>`|
|Leaf Label Path| **Property:** *leafItemSettings.labelPath*<br/><br/> `<EJ.TreeMap id="treemap" leafItemSettings ={leafItem} showLabels={true}></EJ.TreeMap>`<br/>`var leafItem={  labelPath: "GameName" }`|**Property:** *leafItemSettings.labelPath*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ labelPath: 'GameName' }></TreeMapComponent>`|
|Leaf Label Position| **Property:** *leafItemSettings.labelPosition*<br/><br/> `<EJ.TreeMap id="treemap" leafItemSettings ={leafItem} showLabels={true}></EJ.TreeMap>`<br/>`var leafItem={ labelPosition: "topcenter"}`|**Property:** *leafItemSettings.labelPosition*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ labelPosition: 'Center' }></TreeMapComponent>`|
|Leaf Label Color| Not Applicable|**Property:** *leafItemSettings.fill*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={  fill: 'red'}></TreeMapComponent>`|
|Random Colors| Not Applicable|**Property:** *leafItemSettings.autoFill*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ autoFill: true }></TreeMapComponent>`|
|Format| Not Applicable|**Property:** *leafItemSettings.labelFormat*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={  labelFormat: '${Continent}-${Population}' }></TreeMapComponent>`|
|Labels Visibility| **Property:** *leafItemSettings.showLabels*<br/><br/>`<EJ.TreeMap id="treemap" showLabels={true}></EJ.TreeMap>`|**Property:** *leafItemSettings.showLabels*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ showLabels: false }></TreeMapComponent>`|
|Opacity| Not Applicable|**Property:** *leafItemSettings.opacity *<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ opacity: 0.7 }></TreeMapComponent>`|
|Padding| Not Applicable|**Property:** *leafItemSettings.padding *<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={   padding: 5}></TreeMapComponent>`|
|Font Customization| Not Applicable|**Property:** *leafItemSettings.labelStyle*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ labelStyle: { size: '12px', color: 'red', opacity: 0.5 } }></TreeMapComponent>`|
|Position of Template| Not Applicable|**Property:** *leafItemSettings.templatePosition*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={  templatePosition: 'Center'}></TreeMapComponent>`|

## Legend

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Legend Alignment| **Property:** *legendSettings.alignment*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>`<br/>`var legend={  alignment: "far" }`|**Property:** *legendSettings.alignment* <br/><br/> `<TreeMapComponent id="treemap"  legendSettings={alignment: 'Near' }></TreeMapComponent>`|
|Legend Visibility| **Property:** *showLegend*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>`<br/>`var legend={ showLegend: false }`|**Property:** *legendSettings.visible*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={visible: true }></TreeMapComponent>`|
|Legend Position| **Property:** *legendSettings.dockPosition*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>`<br/>`var legend={ dockPosition: "bottom" }`|**Property:** *legendSettings.position*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={ position: 'Top' }></TreeMapComponent>`|
|Legend Height| **Property:** *legendSettings.height*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>`<br/>`var legend={  height: 40}`|**Property:** *legendSettings.height*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={ height: '40px' }></TreeMapComponent>`|
|Legend Width| **Property:** *legendSettings.width*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>`<br/>`var legend={  width: 100}`|**Property:** *legendSettings.width*<br/><br/>`<TreeMapComponent id="treemap"  legendSettings={ width: '100px' }</TreeMapComponent>`|
|Shape Height| **Property:** *legendSettings.iconHeight*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>` <br/>`var legend={ iconHeight: 15  }`|**Property:** *legendSettings.shapeHeight*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={ shapeHeight: '40px' }></TreeMapComponent>`|
|Shape Width| **Property:** *legendSettings.iconWidth*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>`<br/>`var legend={iconWidth: 8  }`|**Property:** *legendSettings.shapeWidth*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={shapeWidth: '40px' }></TreeMapComponent>`|
|Padding| Not Applicable|**Property:** *legendSettings.shapePadding*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={ shapePadding: 10}></TreeMapComponent>`|
|Legend Title| **Property:** *legendSettings.title*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>`<br/>`var legend={ iconWidth: 8 }`|**Property:** *legendSettings.title*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={title: 'Legend' }></TreeMapComponent>`|
|Legend Shape| Not Applicable|**Property:** *legendSettings.shape*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={shape: 'Rectangle' }></TreeMapComponent>`|
|Legend Mode| **Property:** *legendSettings.mode*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>`<br/>`var legend={ mode: "interactive"}`|**Property:** *legendSettings.mode*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={ mode: 'Interactive' }></TreeMapComponent>`|
|Legend Text Customization| Not Applicable|**Property:** *legendSettings.textStyle*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={textStyle: { size: '10px', opacity: 0.5, color: 'red' } }></TreeMapComponent>`|
|Legend Title Customization| Not Applicable|**Property:** *legendSettings.titleStyle*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={ titleStyle: { size: '10px', opacity: 0.5, color: 'red' } }></TreeMapComponent>`|
|Legend Shape Border| Not Applicable|**Property:** *legendSettings.shapeBorder*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={shapeBorder: { width: 2, color: 'red' } }></TreeMapComponent>`|
|Legend Template| **Property:** *legendSettings.template*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>`<br/>`var legend={ template: "template" }`| Not Applicable|
|Left Label| **Property:** *legendSettings.leftLabel*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>`<br/>`var legend={ mode: "interactive", leftLabel: "10Million" }`| Not Applicable|
|Right Label| **Property:** *legendSettings.rightLabel*<br/><br/> `<EJ.TreeMap id="treemap" legendSettings = {legend} ></EJ.TreeMap>`<br/>`var legend={ mode: "interactive", rightLabel: "100Million"}`| Not Applicable|
|Legend Shape Image| Not Applicable|**Property:** *legendSettings.imageUrl*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={ imageUrl: "image.png" }></TreeMapComponent>`|
|Position in Interactive Legend| Not Applicable|**Property:** *legendSettings.labelPosition*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={labelPosition: "Center" }></TreeMapComponent>`|
|Legend Location| Not Applicable|**Property:** *legendSettings.location*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={ location: { x: 10, y: 20 } }></TreeMapComponent>`|
|Legend Orientation| Not Applicable|**Property:** *legendSettings.orientation*<br/><br/> `<TreeMapComponent id="treemap"  legendSettings={orientation: "Horizontal" }></TreeMapComponent>`|

## Levels

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Random Colors| Not Applicable|**Property:** *levels.autoFill*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective autoFill=true></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Level Background Color| **Property:** *levels.groupBackground*<br/><br/> `<EJ.TreeMap id="treemap" levels = {levels}></EJ.TreeMap>`<br/>`var levels=[groupBackground: "white"  ]`| **Property:** *levels.fill*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective fill= 'white'></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Level Border Color| **Property:** *levels.groupBorderColor*<br/><br/> `<EJ.TreeMap id="treemap" levels = {levels}></EJ.TreeMap>`<br/>`var levels=[groupBorderColor: "#58585B" ]`| **Property:** *levels.border.color*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective  border= { color: "#58585B" } ></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Level Border Width| **Property:** *levels.groupBorderThickness*<br/><br/> `<EJ.TreeMap id="treemap" levels = {levels}></EJ.TreeMap>`<br/>`var levels=[groupBorderThickness: 2 ]`| **Property:** *levels.border.width*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective border= { width: 2 }></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Group Gap| **Property:** *levels.groupGap*<br/><br/> `<EJ.TreeMap id="treemap" levels = {levels}></EJ.TreeMap>`<br/>`var levels=[groupGap: 2 ]`| **Property:** *levels.groupGap*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective  groupGap= 2></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Group Padding| **Property:** *levels.groupPadding*<br/><br/> `<EJ.TreeMap id="treemap" levels = {levels}></EJ.TreeMap>`<br/>`var levels=[groupPadding: 1  ]`| **Property:** *levels.groupPadding*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective groupPadding={1} ></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Group Path| **Property:** *levels.groupPath*<br/><br/> `<EJ.TreeMap id="treemap" levels = {levels}></EJ.TreeMap>`<br/>`var levels=[groupPath: "pathname"  ]`| **Property:** *levels.groupPath*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective groupPath= 'pathname'></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Height of Header Level| **Property:** *levels.headerHeight*<br/><br/> `<EJ.TreeMap id="treemap" levels = {levels}></EJ.TreeMap>`<br/>`var levels=[  headerHeight: 20 ]`| **Property:** *levels.headerHeight*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective headerHeight={20} ></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Header Template| **Property:** *levels.headerTemplate*<br/><br/> `<EJ.TreeMap id="treemap" levels = {levels}></EJ.TreeMap>`<br/>`var levels=[ headerTemplate: "template" ]`| **Property:** *levels.headerTemplate*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective headerTemplate= 'template' ></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Opacity of Color| Not Applicable| **Property:** *levels.opacity*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective opacity={0.5}></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Header Visibility| **Property:** *levels.showHeader*<br/><br/> `<EJ.TreeMap id="treemap" levels = {levels}></EJ.TreeMap>`<br/>`var levels=[showHeader: false  ]`| **Property:** *levels.showHeader*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective showHeader={false}></LevelDirective></LevelsDirective> </TreeMapComponent>`|
|Template Position| **Property:** *levels.labelPosition*<br/><br/> `<EJ.TreeMap id="treemap" levels = {levels}></EJ.TreeMap>`<br/>`var levels=[ labelPosition: "topleft" ]`| **Property:** *levels.templatePosition*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective templatePosition= 'Center' ></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Header Style| Not Applicable| **Property:** *levels.headerStyle*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective headerStyle= { color: 'red', size: '16px', opacity: 0.7 } ></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Header Format| Not Applicable| **Property:** *levels.headerFormat*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective headerFormat= '${Continent}' ></LevelDirective></LevelsDirective></TreeMapComponent>`|
|Header Alignment| Not Applicable| **Property:** *levels.headerAlignment*<br/><br/> `<TreeMapComponent id="treemap"><LevelsDirective><LevelDirective headerAlignment= 'Center' ></LevelDirective></LevelsDirective></TreeMapComponent>`|

## Selection

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Selection| **Property:** *selectionMode*<br/><br/> `<EJ.TreeMap id="treemap" selectionMode="default"> </EJ.TreeMap>`| **Property:** *selectionSettings.mode*<br/><br/> `<TreeMapComponent id="treemap" selectionSettings={ enable: true, mode: 'Item'}></TreeMapComponent>`<br/>`<Inject services={[TreeMapSelection]}/>`|
|Selection Color| Not Applicable| **Property:** *selectionSettings.fill*<br/><br/> `<TreeMapComponent id="treemap" selectionSettings={ enable: true, fill: 'blue'  }></TreeMapComponent>`<br/>`<Inject services={[TreeMapSelection]}/>`|
|Selection Color Opacity| Not Applicable| **Property:** *selectionSettings.opacity*<br/><br/> `<TreeMapComponent id="treemap" selectionSettings={  enable: true, fill: 'blue', opacity: 0.6}></TreeMapComponent>`<br/>`<Inject services={[TreeMapSelection]}/>`|
|Border for selection| Not Applicable| **Property:** *selectionSettings.border*<br/><br/> `<TreeMapComponent id="treemap" selectionSettings={ border: { color: 'red', width: 2 } }></TreeMapComponent>`<br/>`<Inject services={[TreeMapSelection]}/>`|

## Highlight

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Highlight Group Selection Mode| **Property:** *highlightGroupOnSelection*<br/><br/> `<EJ.TreeMap id="treemap" highlightGroupOnSelection= {true} ></EJ.TreeMap>`| **Property:** *highlightSettings.mode*<br/><br/> `<TreeMapComponent id="treemap"  highlightSettings={ enable: true, mode: 'All'}></TreeMapComponent>`<br/>`<Inject services={[TreeMapHighlight]}/>`|
|Highlight Selection Mode| **Property:** *highlightOnSelection*<br/><br/> `<EJ.TreeMap id="treemap" highlightOnSelection= {true}></EJ.TreeMap>`| **Property:** *highlightSettings.mode*<br/><br/> `<TreeMapComponent id="treemap"  highlightSettings={enable: true, mode: 'Item'  }></TreeMapComponent>`<br/>`<Inject services={[TreeMapHighlight]}/>`|
|Highlight Group Border Color| **Property:** *highlightGroupBorderBrush*<br/><br/> `<EJ.TreeMap id="treemap"  highlightGroupBorderBrush= 'gray'></EJ.TreeMap>`| **Property:** *highlightSettings.border.color*<br/><br/> `<TreeMapComponent id="treemap"  highlightSettings={ enable: true, mode: 'All',border: { color: 'gray' } }></TreeMapComponent>`<br/>`<Inject services={[TreeMapHighlight]}/>`|
|Highlight Group Border Width| **Property:** *highlightGroupBorderThickness*<br/><br/> `<EJ.TreeMap id="treemap" highlightGroupBorderThickness= {3} ></EJ.TreeMap>`| **Property:** *highlightSettings.border.width*<br/><br/> `<TreeMapComponent id="treemap"  highlightSettings={enable: true, mode: 'All',    border: { width: 3 } }></TreeMapComponent>`<br/>`<Inject services={[TreeMapHighlight]}/>`|
|Highlight Selection Border Color| **Property:** *highlightBorderBrush*<br/><br/> `<EJ.TreeMap id="treemap" highlightBorderBrush= 'gray' ></EJ.TreeMap>`| **Property:** *highlightSettings.border.color*<br/><br/>`<TreeMapComponent id="treemap"  highlightSettings={ enable: true, mode: 'Item',  border: { color: 'gray' }}></TreeMapComponent>`<br/>`<Inject services={[TreeMapHighlight]}/>`|
|Highlight Selection Border Width| **Property:** *highlightBorderThickness*<br/><br/> `<EJ.TreeMap id="treemap" highlightBorderThickness= {3}></EJ.TreeMap>`| **Property:** *highlightSettings.border.width*<br/><br/>`<TreeMapComponent id="treemap"  highlightSettings={ enable: true, mode: 'Item',    border: { width: 3 } }></TreeMapComponent>`<br/>`<Inject services={[TreeMapHighlight]}/>`|
|Highlight Color| Not Applicable| **Property:** *highlightSettings.fill*<br/><br/> `<TreeMapComponent id="treemap"  highlightSettings={ enable: true, fill: 'red' }></TreeMapComponent>`<br/>`<Inject services={[TreeMapHighlight]}/>`|
|Highlight Color Opacity| Not Applicable| **Property:** *highlightSettings.opacity*<br/><br/> `<TreeMapComponent id="treemap"  highlightSettings={ enable: true, fill: 'red', opacity: 0.5 }></TreeMapComponent>`<br/>`<Inject services={[TreeMapHighlight]}/>`|

## Range ColorMapping

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|From value| **Property:** *rangeColorMapping.from*<br/><br/> `<EJ.TreeMap id="treemap" rangeColorMapping="range"></EJ.TreeMap>`<br/>`var range=[{ from: 1000 } ]`| **Property:** *leafItemSettings.colorMapping.from*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={colorMapping: [{ from: 1000 }]  }></TreeMapComponent>`|
|To value| **Property:** *rangeColorMapping.to*<br/><br/> `<EJ.TreeMap id="treemap" rangeColorMapping="range"></EJ.TreeMap>`<br/>`var range=[{ to: 100000 } ]`| **Property:** *leafItemSettings.colorMapping.to*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ colorMapping: [{ to: 100000 }] }></TreeMapComponent>`|
|Color| **Property:** *rangeColorMapping.color*<br/><br/>`<EJ.TreeMap id="treemap" rangeColorMapping="range"></EJ.TreeMap>`<br/>`var range=[{ color: "#77D8D8" } ]`| **Property:** *leafItemSettings.colorMapping.color*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ colorMapping: [{ color: "#77D8D8" }]  }></TreeMapComponent>`|
|Legend Label| **Property:** *rangeColorMapping.legendLabel*<br/><br/>`<EJ.TreeMap id="treemap" rangeColorMapping="range"></EJ.TreeMap>`<br/>`var range=[{ legendLabel: "Growth" } ]`| **Property:** *leafItemSettings.colorMapping.label*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ colorMapping: [{ label: "Growth" }]  }></TreeMapComponent>`|

## Desaturation ColorMapping

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|From value| **Property:** *desaturationColorMapping.from*<br/><br/>`<EJ.TreeMap id="treemap" desaturationColorMapping="desaturation"> </EJ.TreeMap>`<br/>`var desaturation=[{ from: 1000 } ]`| **Property:** *leafItemSettings.colorMapping.from*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={ colorMapping: [{ from: 1000 }] }></TreeMapComponent>`|
|To value| **Property:** *desaturationColorMapping.to*<br/><br/>`<EJ.TreeMap id="treemap" desaturationColorMapping="desaturation"> </EJ.TreeMap>`<br/>`var desaturation=[{ to: 10000 } ]`| **Property:** *leafItemSettings.colorMapping.to*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={colorMapping: [{ to: 10000 }]}></TreeMapComponent>`|
|Color| **Property:** *desaturationColorMapping.color*<br/><br/>`<EJ.TreeMap id="treemap" desaturationColorMapping="desaturation"> </EJ.TreeMap>`<br/>`var desaturation=[{ color: "#77D8D8" } ]`| **Property:** *leafItemSettings.colorMapping.color*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={colorMapping: [{ color: "#77D8D8" }] }></TreeMapComponent>`|
|Value| Not Applicable| **Property:** *leafItemSettings.colorMapping.value*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={colorMapping: [{ value: "Population" }]}></TreeMapComponent>`|
|Minimum Opacity| Not Applicable| **Property:** *leafItemSettings.colorMapping.minOpacity*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={colorMapping: [{ minOpacity: 0.7 }]}></TreeMapComponent>`|
|Maximum Opacity| Not Applicable| **Property:** *leafItemSettings.colorMapping.maxOpacity*<br/><br/> `<TreeMapComponent id="treemap"  leafItemSettings={colorMapping: [{ maxOpacity: 1 }] }></TreeMapComponent>`|

## Tooltip

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Tooltip| **Property:** *showTooltip*<br/><br/>`<EJ.TreeMap id="treemap" showTooltip={true}></EJ.TreeMap>`| **Property:** *tooltipSettings.visible*<br/><br/> `<TreeMapComponent id="treemap"   tooltipSettings={ visible: true}></TreeMapComponent>`<br/>`<Inject services={[TreeMapTooltip, TreeMapLegend]}/>`|
|Tooltip Template| **Property:** *tooltipTemplate*<br/><br/> `<EJ.TreeMap id="treemap" showTooltip={true} tooltipTemplate='template' ></EJ.TreeMap>`| **Property:** *tooltipSettings.template*<br/><br/> `<TreeMapComponent id="treemap"   tooltipSettings={visible: true,template: 'template'  }></TreeMapComponent>`<br/>`<Inject services={[TreeMapTooltip, TreeMapLegend]}/>`|
|Tooltip Border| Not Applicable| **Property:** *tooltipSettings.border*<br/><br/> `<TreeMapComponent id="treemap"   tooltipSettings={visible: true,border: { color: 'red', width: 2 }  }></TreeMapComponent>`<br/>`<Inject services={[TreeMapTooltip, TreeMapLegend]}/>`|
|Tooltip Color| Not Applicable| **Property:** *tooltipSettings.fill*<br/><br/> `<TreeMapComponent id="treemap"   tooltipSettings={visible: true,  fill: 'gray'}></TreeMapComponent>`<br/>`<Inject services={[TreeMapTooltip, TreeMapLegend]}/>`|
|Tooltip Format| Not Applicable| **Property:** *tooltipSettings.format*<br/><br/> `<TreeMapComponent id="treemap"   tooltipSettings={visible: true, format: '${Population}'}></TreeMapComponent>`<br/>`<Inject services={[TreeMapTooltip, TreeMapLegend]}/>`|
|Tooltip Marker Shape| Not Applicable| **Property:** *tooltipSettings.markerShapes*<br/><br/> `<TreeMapComponent id="treemap"   tooltipSettings={visible: true, markerShapes: 'Circle' }></TreeMapComponent>`<br/>`<Inject services={[TreeMapTooltip, TreeMapLegend]}/>`|
|Tooltip Color Opacity| Not Applicable| **Property:** *tooltipSettings.opacity*<br/><br/> `<TreeMapComponent id="treemap"   tooltipSettings={visible: true,opacity: 0.5 }></TreeMapComponent>`<br/>`<Inject services={[TreeMapTooltip, TreeMapLegend]}/>`|
|Tooltip Text Style| Not Applicable| **Property:** *tooltipSettings.textStyle*<br/><br/> `<TreeMapComponent id="treemap"   tooltipSettings={visible: true,textStyle: {    Color: 'red', opacity: 0.5, size: '12px' }}></TreeMapComponent>`<br/>`<Inject services={[TreeMapTooltip, TreeMapLegend]}/>`|

## Drilldown

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Drilldown| **Property:** *enableDrillDown*<br/><br/> `<EJ.TreeMap id="treemap" enableDrillDown= {true} ></EJ.TreeMap>`| **Property:** *enableDrillDown*<br/><br/>`<TreeMapComponent id="treemap"  enableDrillDown= {true}></TreeMapComponent>`|
|Drilldown Level| **Property:** *drillDownLevel*<br/><br/> `<EJ.TreeMap id="treemap" drillDownLevel= {1}></EJ.TreeMap>`| **Property:** *InitialDrillSettings.groupIndex*<br/><br/> `<TreeMapComponent id="treemap"  InitialDrillSettings= { groupIndex: 1 }></TreeMapComponent>`|

## Methods

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Treemap Refresh Method| **Method:** *refresh*<br/><br/> `var treemap =    $("#container").ejTreeMap("instance");  treemap.refresh();`| **Method:** *refresh*<br/><br/> `var treemap =    document.getElementById('container').ej2_instances[0];  treemap.refresh();`|
|Method to Drilldown| **Method:** *drillDown*<br/><br/> `var treemap =    $("#container").ejTreeMap("instance");  treemap.drillDown();`|Not Applicable|
|Append to Method| Not Applicable| **Method:** *appendTo*<br/><br/> `var treemap =    document.getElementById('container').ej2_instances[0];  treemap.appendTo();`|
|Add Event Listener Method| Not Applicable| **Method:** *addEventListener*<br/><br/> `var treemap =    document.getElementById('container').ej2_instances[0];  treemap.addEventListener();`|
|Treemap Destroy Method| Not Applicable| **Method:** *destroy*<br/><br/> `var treemap =    document.getElementById('container').ej2_instances[0];  treemap.destroy();`|
|Treemap Exporting Method| Not Applicable| **Method:** *export*<br/><br/> `var treemap =    document.getElementById('container').ej2_instances[0];  treemap.export();`|
|Get the Module Name| Not Applicable| **Method:** *getModuleName*<br/><br/> `var treemap =    document.getElementById('container').ej2_instances[0];  treemap.getModuleName();`|
|Printing the Treemap| Not Applicable| **Method:** *print*<br/><br/> `var treemap =    document.getElementById('container').ej2_instances[0];  treemap.print();`|
|Resizing the Treemap| Not Applicable| **Method:** *resizeOnTreeMap*<br/><br/> `var treemap =    document.getElementById('container').ej2_instances[0];  treemap.resizeOnTreeMap();`|
|Inject Method (Tooltip)| Not Applicable| **Method:** *resizeOnTreeMap*<br/><br/> TreeMap.Inject(TreeMapTooltip); <br/> `TreeMap.Inject(TreeMapTooltip);  var treemap =    document.getElementById('container').ej2_instances[0];  treemap.resizeOnTreeMap();`|
|Remove Event Listener Method| Not Applicable| **Method:** *removeEventListener*<br/><br/> `var treemap =    document.getElementById('container').ej2_instances[0];  treemap.removeEventListener();`|

## Events

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Treemap Load Event| Not Applicable| **Event:** *load*<br/><br/> `<TreeMapComponent id="treemap"  load={this.load.bind(this)}></TreeMapComponent>`<br/>`load(args){ }`|
|Treemap Loaded Event| Not Applicable| **Event:** *loaded*<br/><br/> `<TreeMapComponent id="treemap"  loaded={this.loaded.bind(this)}></TreeMapComponent>`<br/>`loaded(args){ }`|
|Event Before Print| Not Applicable| **Event:** *beforePrint*<br/><br/>`<TreeMapComponent id="treemap"  beforePrint={this.beforePrint.bind(this)}></TreeMapComponent>`<br/>`beforePrint(args){ }`|
|Click Event| **Event:** *click*<br/><br/> `<EJ.TreeMap id="treemap" click = {click}></EJ.TreeMap>`<br/>`function click(args){}`| **Event:** *click*<br/><br/> `<TreeMapComponent id="treemap"  click={this.click.bind(this)}></TreeMapComponent>`<br/>`click(args){ }`|
|Drill Start Event| **Event:** *drillStarted*<br/><br/> `<EJ.TreeMap id="treemap" drillStarted = {drillStarted}></EJ.TreeMap>`<br/>`function drillStarted(args){}`| **Event:** *drillStart*<br/><br/> `<TreeMapComponent id="treemap"   drillStart={this. drillStart.bind(this)}></TreeMapComponent>`<br/>`drillStart(args){ }`|
|Drill End Event| Not Applicable| **Event:** *drillEnd*<br/><br/> `<TreeMapComponent id="treemap"  drillEnd={this.drillEnd.bind(this)}></TreeMapComponent>`<br/>`drillEnd(args){ }`|
|Event on Item Click| Not Applicable| **Event:** *itemClick*<br/><br/> `<TreeMapComponent id="treemap"    itemClick={this.  itemClick.bind(this)}></TreeMapComponent>`<br/>`itemClick(args){ }`|
|Treemap Item Select Event| **Event:** *treeMapItemSelected*<br/><br/> `<EJ.TreeMap id="treemap" treeMapItemSelected = {TreeMapItemSelected}></EJ.TreeMap>`<br/>`function treeMapItemSelected(args){}`| **Event:** *itemSelected*<br/><br/> `<TreeMapComponent id="treemap"   itemSelected={this. itemSelected.bind(this)}></TreeMapComponent>`<br/>`itemSelected(args){ }`|
|Treemap Item Rendering Event| **Event:** *itemRendering*<br/><br/> `<EJ.TreeMap id="treemap"  itemRendering = { itemRendering}></EJ.TreeMap>`<br/>`function itemRendering(args){}`| **Event:** *itemRendering*<br/><br/> `<TreeMapComponent id="treemap"   itemRendering={this. itemRendering.bind(this)}></TreeMapComponent>`<br/>`itemRendering(args){ }`|
|Treemap Item Move Event| Not Applicable| **Event:** *itemMove*<br/><br/> `<TreeMapComponent id="treemap"  itemMove={this.itemMove.bind(this)}></TreeMapComponent>`<br/>`itemMove(args){ }`|
|Treemap Item Highlight Event| Not Applicable| **Event:** *itemHighlight*<br/><br/> `<TreeMapComponent id="treemap"  itemHighlight={this.itemHighlight.bind(this)}></TreeMapComponent>`<br/>`itemHighlight(args){ }`|
|Template Header Render Event| **Event:** *headerTemplateRendering*<br/><br/> `<EJ.TreeMap id="treemap" headerTemplateRendering = {headerTemplateRendering}></EJ.TreeMap>`<br/>`function headerTemplateRendering(args){}`| Not Applicable|
|Drilldown Item Select Event| **Event:** *drillDownItemSelected*<br/><br/> `<EJ.TreeMap id="treemap" drillDownItemSelected = {drillDownItemSelected}></EJ.TreeMap>`<br/>`function drillDownItemSelected(args){}`| Not Applicable|
|Refresh Event| **Event:** *refreshed*<br/><br/> `<EJ.TreeMap id="treemap" refreshed = {refreshed}></EJ.TreeMap>`<br/>`function refreshed(args){}`| Not Applicable|
|Group Select Event| **Event:** *treeMapGroupSelected*<br/><br/>`<EJ.TreeMap id="treemap"  treeMapGroupSelected = { treeMapGroupSelected}></EJ.TreeMap>`<br/>`function  treeMapGroupSelected(args){}`| Not Applicable|
|Mouse Event| Not Applicable| **Event:** *mouseMove*<br/><br/> `<TreeMapComponent id="treemap"  mouseMove={this.mouseMove.bind(this)}></TreeMapComponent>`<br/>`mouseMove(args){ }`|
|Resize Event| Not Applicable| **Event:** *resize*<br/><br/> `<TreeMapComponent id="treemap"  resize={this.resize.bind(this)}></TreeMapComponent>`<br/>`resize(args){ }`|
|Tooltip Render Event| Not Applicable| **Event:** *tooltipRendering*<br/><br/> `<TreeMapComponent id="treemap"   tooltipRendering={this.tooltipRendering.bind(this)}></TreeMapComponent>`<br/>`tooltipRendering(args){ }`|
|Double Click Event| **Event:** *doubleClick*<br/><br/>`<EJ.TreeMap id="treemap" doubleClick = {doubleClick}></EJ.TreeMap>`<br/>`function doubleClick(args){}`| Not Applicable|
|Right Click Event| **Event:** *rightClick*<br/><br/> `<EJ.TreeMap id="treemap" rightClick = {rightClick}></EJ.TreeMap>`<br/>`function rightClick(args){}`| Not Applicable|