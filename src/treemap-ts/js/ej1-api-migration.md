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
|Datasource| **Property:** *dataSource*<br/><br/> var population_data = [{ <br/> &nbsp; Continent: "Asia", <br/> &nbsp; Population: 1749046000 }], <br/> $("#container").ejTreeMap({ <br/> dataSource: population_data })|**Property:** *dataSource*<br/><br/> var population_data = [{ Continent: "Asia", <br/> &nbsp; Population: 1749046000 }], <br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; dataSource: population_data <br/> }); <br/> treemap.appendTo('#container');|

## Appearance

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Layout| **Property:** *itemsLayoutMode*<br/><br/> $("#container").ejTreeMap({ <br/> itemsLayoutMode: "sliceanddiceauto" })|**Property:** *layoutType*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; layoutType: 'SliceAndDiceAuto' <br/> }); <br/> treemap.appendTo('#container');|
|Weight Value Path| **Property:** *weightValuePath*<br/><br/> $("#container").ejTreeMap({ <br/> weightValuePath: "Population" })|**Property:** *weightValuePath*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; weightValuePath: 'Population' <br/> }); <br/> treemap.appendTo('#container');|
|Range Color Value Path| **Property:** *colorValuePath*<br/><br/> $("#container").ejTreeMap({ <br/> colorValuePath: "Continent" })|**Property:** *rangeColorValuePath*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; rangeColorValuePath: 'Continent' <br/> }); <br/> treemap.appendTo('#container');|
|Equal Color Value Path| Not Applicable|**Property:** *equalColorValuePath*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; equalColorValuePath: 'Asia' <br/> }); <br/> treemap.appendTo('#container');|
|Height| **Property:** *height*<br/><br/> $("#container").ejTreeMap({ <br/> height: 50 })|**Property:** *height*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; height: '50px' <br/> }); <br/> treemap.appendTo('#container');|
|Width| **Property:** *width*<br/><br/> $("#container").ejTreeMap({ <br/> width: 400 })|**Property:** *width*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; width: '400px' <br/> }); <br/> treemap.appendTo('#container');|
|Theme| Not Applicable|**Property:** *theme*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; theme: 'Highcontrast' <br/> }); <br/> treemap.appendTo('#container');|
|Localization| **Property:** *locale*<br/><br/> $("#container").ejTreeMap({ <br/> locale: "en-US" })|**Property:** *locale*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; locale: 'en-US' <br/> }); <br/> treemap.appendTo('#container');|
|Palette Colors| **Property:** *paletteColorMapping.colors*<br/><br/> $("#container").ejTreeMap({ <br/> paletteColorMapping: { colors: ['red','green'] } })|**Property:** *palette*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; palette:  ['#C33764', '#AB3566'] <br/> }); <br/> treemap.appendTo('#container');|
|Margin| Not Applicable|**Property:** *margin*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; margin: { left: 5, top: 8 } <br/> }); <br/> treemap.appendTo('#container');|
|Resize| **Property:** *enableResize*<br/><br/> $("#container").ejTreeMap({ <br/> enableResize: true })|Not Applicable|
|Responsive| **Property:** *isResponsive*<br/><br/> $("#container").ejTreeMap({ <br/> isResponsive: true })|Not Applicable|

## Leaf Items

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Border Color| **Property:** *leafItemSettings.borderBrush*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; leafItemSettings: { showLabels: true, <br/> &nbsp; borderBrush: "blue" } <br/> })|**Property:** *leafItemSettings.border*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { border: { color: 'white' } } <br/> }); <br/> treemap.appendTo('#container');|
|Border Width| **Property:** *leafItemSettings.borderThickness*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; leafItemSettings: { showLabels: true, <br/> &nbsp; borderThickness: 5 } <br/> })|**Property:** *leafItemSettings.border*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { border: { width: 5 } } <br/> }); <br/> treemap.appendTo('#container');|
|Gap Value| **Property:** *leafItemSettings.gap*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; leafItemSettings: { showLabels: true, <br/> &nbsp; gap: 5 } <br/> })|**Property:** *leafItemSettings.gap*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { gap: 5 } <br/> }); <br/> treemap.appendTo('#container');|
|Leaf Item Label| **Property:** *leafItemSettings.itemTemplate*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; leafItemSettings: { showLabels: true, <br/> &nbsp; itemTemplate: "template" } <br/> })|**Property:** *leafItemSettings.labelTemplate*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { labelTemplate: 'template' } <br/> }); <br/> treemap.appendTo('#container');|
|Leaf Label Path| **Property:** *leafItemSettings.labelPath*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; leafItemSettings: { showLabels: true, <br/> &nbsp; labelPath: "GameName" } <br/> })|**Property:** *leafItemSettings.labelPath*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { labelPath: 'GameName' } <br/> }); <br/> treemap.appendTo('#container');|
|Leaf Label Position| **Property:** *leafItemSettings.labelPosition*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; leafItemSettings: { showLabels: true, <br/> &nbsp; labelPosition: "topcenter" } <br/> })|**Property:** *leafItemSettings.labelPosition*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { labelPosition: 'Center' } <br/> }); <br/> treemap.appendTo('#container');|
|Leaf Label Color| Not Applicable|**Property:** *leafItemSettings.fill*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { fill: 'red' } <br/> }); <br/> treemap.appendTo('#container');|
|Random Colors| Not Applicable|**Property:** *leafItemSettings.autoFill*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { autoFill: true } <br/> }); <br/> treemap.appendTo('#container');|
|Format| Not Applicable|**Property:** *leafItemSettings.labelFormat*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { labelFormat: '${Continent}-${Population}' } <br/> }); <br/> treemap.appendTo('#container');|
|Labels Visibility| **Property:** *leafItemSettings.showLabels*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; leafItemSettings: { showLabels: true } <br/> })|**Property:** *leafItemSettings.showLabels*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { showLabels: false } <br/> }); <br/> treemap.appendTo('#container');|
|Opacity| Not Applicable|**Property:** *leafItemSettings.opacity *<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { opacity: 0.7 } <br/> }); <br/> treemap.appendTo('#container');|
|Padding| Not Applicable|**Property:** *leafItemSettings.padding *<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { padding: 5 } <br/> }); <br/> treemap.appendTo('#container');|
|Font Customization| Not Applicable|**Property:** *leafItemSettings.labelStyle*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { labelStyle: { size: '12px', color: 'red', opacity: 0.5 } } <br/> }); <br/> treemap.appendTo('#container');|
|Position of Template| Not Applicable|**Property:** *leafItemSettings.templatePosition*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { templatePosition: 'Center' } <br/> }); <br/> treemap.appendTo('#container');|

## Legend

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Legend Alignment| **Property:** *legendSettings.alignment*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; legendSettings: { alignment: "far" } <br/> })|**Property:** *legendSettings.alignment*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { alignment: 'Near' } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Visibility| **Property:** *showLegend*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; showLegend: false <br/> })|**Property:** *legendSettings.visible*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { visible: true } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Position| **Property:** *legendSettings.dockPosition*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; legendSettings: { dockPosition: "bottom" } <br/> })|**Property:** *legendSettings.position*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { position: 'Top' } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Height| **Property:** *legendSettings.height*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; legendSettings: { height: 40 } <br/> })|**Property:** *legendSettings.height*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { height: '40px' } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Width| **Property:** *legendSettings.width*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; legendSettings: { width: 100 } <br/> })|**Property:** *legendSettings.width*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { width: '100px' } <br/> }); <br/> treemap.appendTo('#container');|
|Shape Height| **Property:** *legendSettings.iconHeight*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; legendSettings: { iconHeight: 15 } <br/> })|**Property:** *legendSettings.shapeHeight*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { shapeHeight: '40px' } <br/> }); <br/> treemap.appendTo('#container');|
|Shape Width| **Property:** *legendSettings.iconWidth*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; legendSettings: { iconWidth: 8 } <br/> })|**Property:** *legendSettings.shapeWidth*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { shapeWidth: '40px' } <br/> }); <br/> treemap.appendTo('#container');|
|Padding| Not Applicable|**Property:** *legendSettings.shapePadding*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { shapePadding: 10 } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Title| **Property:** *legendSettings.title*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; legendSettings: { title: "Population" } <br/> })|**Property:** *legendSettings.title*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { title: 'Legend' } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Shape| Not Applicable|**Property:** *legendSettings.shape*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { shape: 'Rectangle' } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Mode| **Property:** *legendSettings.mode*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; legendSettings: { mode: "interactive" } <br/> })|**Property:** *legendSettings.mode*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { mode: 'Interactive' } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Text Customization| Not Applicable|**Property:** *legendSettings.textStyle*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { textStyle: { <br/> &nbsp; &nbsp; size: '10px', opacity: 0.5, color: 'red' } } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Title Customization| Not Applicable|**Property:** *legendSettings.titleStyle*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { titleStyle: { <br/> &nbsp; &nbsp; size: '10px', opacity: 0.5, color: 'red' } } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Shape Border| Not Applicable|**Property:** *legendSettings.shapeBorder*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { shapeBorder: { <br/> &nbsp; &nbsp; width: 2, color: 'red' } } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Template| **Property:** *legendSettings.template*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; legendSettings: { template: "template" } <br/> })| Not Applicable|
|Left Label| **Property:** *legendSettings.leftLabel*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; legendSettings: { mode: "interactive", leftLabel: "10Million" } <br/> })| Not Applicable|
|Right Label| **Property:** *legendSettings.rightLabel*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; legendSettings: { mode: "interactive", rightLabel: "100Million" } <br/> })| Not Applicable|
|Legend Shape Image| Not Applicable|**Property:** *legendSettings.imageUrl*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { imageUrl: "image.png" } <br/> }); <br/> treemap.appendTo('#container');|
|Position in Intractive Legend| Not Applicable|**Property:** *legendSettings.labelPosition*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { labelPosition: "Center" } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Location| Not Applicable|**Property:** *legendSettings.location*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { location: { x: 10, y: 20 } } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Orientation| Not Applicable|**Property:** *legendSettings.orientation*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; legendSettings: { orientation: "Horizontal" } <br/> }); <br/> treemap.appendTo('#container');|

## Levels

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Random Colors| Not Applicable|**Property:** *levels.autoFill*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ autoFill: true }] <br/> }); <br/> treemap.appendTo('#container');|
|Level Background Color| **Property:** *levels.groupBackground*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; levels: [{ groupBackground: "white" }] <br/> })| **Property:** *levels.fill*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ fill: 'white' }] <br/> }); <br/> treemap.appendTo('#container');|
|Level Border Color| **Property:** *levels.groupBorderColor*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; levels: [{ groupBorderColor: "#58585B" }] <br/> })| **Property:** *levels.border.color*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ border: { color: "#58585B" } }] <br/> }); <br/> treemap.appendTo('#container');|
|Level Border Width| **Property:** *levels.groupBorderThickness*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; levels: [{ groupBorderThickness: 2 }] <br/> })| **Property:** *levels.border.width*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ border: { width: 2 } }] <br/> }); <br/> treemap.appendTo('#container');|
|Group Gap| **Property:** *levels.groupGap*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; levels: [{ groupGap: 2 }] <br/> })| **Property:** *levels.groupGap*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ groupGap: 2 }] <br/> }); <br/> treemap.appendTo('#container');|
|Group Padding| **Property:** *levels.groupPadding*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; levels: [{ groupPadding: 1 }] <br/> })| **Property:** *levels.groupPadding*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ groupPadding: 1 }] <br/> }); <br/> treemap.appendTo('#container');|
|Group Path| **Property:** *levels.groupPath*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; levels: [{ groupPath: "pathname" }] <br/> })| **Property:** *levels.groupPath*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ groupPath: 'pathname' }] <br/> }); <br/> treemap.appendTo('#container');|
|Height of Header Level| **Property:** *levels.headerHeight*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; levels: [{ headerHeight: 20 }] <br/> })| **Property:** *levels.headerHeight*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ headerHeight: 20 }] <br/> }); <br/> treemap.appendTo('#container');|
|Header Template| **Property:** *levels.headerTemplate*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; levels: [{ headerTemplate: "template" }] <br/> })| **Property:** *levels.headerTemplate*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ headerTemplate: 'template' }] <br/> }); <br/> treemap.appendTo('#container');|
|Opacity of Color| Not Applicable| **Property:** *levels.opacity*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ opacity: 0.5 }] <br/> }); <br/> treemap.appendTo('#container');|
|Header Visibility| **Property:** *levels.showHeader*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; levels: [{ showHeader: false }] <br/> })| **Property:** *levels.showHeader*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ showHeader: false }] <br/> }); <br/> treemap.appendTo('#container');|
|Template Position| **Property:** *levels.labelPosition*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; levels: [{ labelPosition: "topleft" }] <br/> })| **Property:** *levels.templatePosition*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ templatePosition: 'Center' }] <br/> }); <br/> treemap.appendTo('#container');|
|Header Style| Not Applicable| **Property:** *levels.headerStyle*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ headerStyle: { color: 'red', size: '16px', opacity: 0.7 } }] <br/> }); <br/> treemap.appendTo('#container');|
|Header Format| Not Applicable| **Property:** *levels.headerFormat*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ headerFormat: '${Continent}' }] <br/> }); <br/> treemap.appendTo('#container');|
|Header Alignment| Not Applicable| **Property:** *levels.headerAlignment*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; levels: [{ headerAlignment: 'Center' }] <br/> }); <br/> treemap.appendTo('#container');|

## Selection

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Selection| **Property:** *selectionMode*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; selectionMode: "default" <br/> })| **Property:** *selectionSettings.mode*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; selectionSettings: { enable: true, mode: 'Item' } <br/> }); <br/> treemap.appendTo('#container');|
|Selection Color| Not Applicable| **Property:** *selectionSettings.fill*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; selectionSettings: { enable: true, fill: 'blue' } <br/> }); <br/> treemap.appendTo('#container');|
|Selection Color Opacity| Not Applicable| **Property:** *selectionSettings.opacity*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; selectionSettings: { enable: true, fill: 'blue', opacity: 0.6 } <br/> }); <br/> treemap.appendTo('#container');|
|Border for selection| Not Applicable| **Property:** *selectionSettings.border*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; selectionSettings: { border: { color: 'red', width: 2 } } <br/> }); <br/> treemap.appendTo('#container');|

## Hightlight

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Highlight Group Selection Mode| **Property:** *highlightGroupOnSelection*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; highlightGroupOnSelection: true <br/> })| **Property:** *highlightSettings.mode*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; highlightSettings: { enable: true, mode: 'All' } <br/> }); <br/> treemap.appendTo('#container');|
|Highlight Selection Mode| **Property:** *highlightOnSelection*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; highlightOnSelection: true <br/> })| **Property:** *highlightSettings.mode*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; highlightSettings: { enable: true, mode: 'Item' } <br/> }); <br/> treemap.appendTo('#container');|
|Highlight Group Border Color| **Property:** *highlightGroupBorderBrush*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; highlightGroupBorderBrush: 'gray' <br/> })| **Property:** *highlightSettings.border.color*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; highlightSettings: { enable: true, mode: 'All', <br/> &nbsp; &nbsp; border: { color: 'gray' } } <br/> }); <br/> treemap.appendTo('#container');|
|Highlight Group Border Width| **Property:** *highlightGroupBorderThickness*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; highlightGroupBorderThickness: 3 <br/> })| **Property:** *highlightSettings.border.width*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; highlightSettings: { enable: true, mode: 'All', <br/> &nbsp; &nbsp; border: { width: 3 } } <br/> }); <br/> treemap.appendTo('#container');|
|Highlight Selection Border Color| **Property:** *highlightBorderBrush*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; highlightBorderBrush: 'gray' <br/> })| **Property:** *highlightSettings.border.color*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; highlightSettings: { enable: true, mode: 'Item', <br/> &nbsp; &nbsp; border: { color: 'gray' } } <br/> }); <br/> treemap.appendTo('#container');|
|Highlight Selection Border Width| **Property:** *highlightBorderThickness*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; highlightBorderThickness: 3 <br/> })| **Property:** *highlightSettings.border.width*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; highlightSettings: { enable: true, mode: 'Item', <br/> &nbsp; &nbsp; border: { width: 3 } } <br/> }); <br/> treemap.appendTo('#container');|
|Highlight Color| Not Applicable| **Property:** *highlightSettings.fill*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; highlightSettings: { enable: true, fill: 'red' } <br/> }); <br/> treemap.appendTo('#container');|
|Highlight Color Opacity| Not Applicable| **Property:** *highlightSettings.opacity*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; highlightSettings: { enable: true, fill: 'red', opacity: 0.5 } <br/> }); <br/> treemap.appendTo('#container');|

## Range ColorMapping

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|From value| **Property:** *rangeColorMapping.from*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; rangeColorMapping: [{ from: 1000 }] <br/> })| **Property:** *leafItemSettings.colorMapping.from*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { colorMapping: [{ from: 1000 }] } <br/> }); <br/> treemap.appendTo('#container');|
|To value| **Property:** *rangeColorMapping.to*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; rangeColorMapping: [{ to: 100000 }] <br/> })| **Property:** *leafItemSettings.colorMapping.to*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { colorMapping: [{ to: 100000 }] } <br/> }); <br/> treemap.appendTo('#container');|
|Color| **Property:** *rangeColorMapping.color*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; rangeColorMapping: [{ color: "#77D8D8" }] <br/> })| **Property:** *leafItemSettings.colorMapping.color*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { colorMapping: [{ color: "#77D8D8" }] } <br/> }); <br/> treemap.appendTo('#container');|
|Legend Label| **Property:** *rangeColorMapping.legendLabel*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; rangeColorMapping: [{ legendLabel: "Growth" }] <br/> })| **Property:** *leafItemSettings.colorMapping.label*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { colorMapping: [{ label: "Growth" }] } <br/> }); <br/> treemap.appendTo('#container');|

## Desaturation ColorMapping

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|From value| **Property:** *desaturationColorMapping.from*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; desaturationColorMapping: [{ from: 1000 }] <br/> })| **Property:** *leafItemSettings.colorMapping.from*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { colorMapping: [{ from: 1000 }] } <br/> }); <br/> treemap.appendTo('#container');|
|To value| **Property:** *desaturationColorMapping.to*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; desaturationColorMapping: [{ to: 10000 }] <br/> })| **Property:** *leafItemSettings.colorMapping.to*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { colorMapping: [{ to: 10000 }] } <br/> }); <br/> treemap.appendTo('#container');|
|Color| **Property:** *desaturationColorMapping.color*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; desaturationColorMapping: [{ color: "#77D8D8" }] <br/> })| **Property:** *leafItemSettings.colorMapping.color*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { colorMapping: [{ color: "#77D8D8" }] } <br/> }); <br/> treemap.appendTo('#container');|
|Value| Not Applicable| **Property:** *leafItemSettings.colorMapping.value*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { colorMapping: [{ value: "Population" }] } <br/> }); <br/> treemap.appendTo('#container');|
|Minimum Opacity| Not Applicable| **Property:** *leafItemSettings.colorMapping.minOpacity*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { colorMapping: [{ minOpacity: 0.7 }] } <br/> }); <br/> treemap.appendTo('#container');|
|Maximum Opacity| Not Applicable| **Property:** *leafItemSettings.colorMapping.maxOpacity*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; leafItemSettings: { colorMapping: [{ maxOpacity: 1 }] } <br/> }); <br/> treemap.appendTo('#container');|

## Tooltip

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Tooltip| **Property:** *showTooltip*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; showTooltip: true <br/> })| **Property:** *tooltipSettings.visible*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; tooltipSettings: { visible: true } <br/> }); <br/> treemap.appendTo('#container');|
|Tooltip Template| **Property:** *tooltipTemplate*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; tooltipTemplate: 'template' <br/> })| **Property:** *tooltipSettings.template*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; tooltipSettings: { template: 'template' } <br/> }); <br/> treemap.appendTo('#container');|
|Tooltip Border| Not Applicable| **Property:** *tooltipSettings.border*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; tooltipSettings: { border: { color: 'red', width: 2 } } <br/> }); <br/> treemap.appendTo('#container');|
|Tooltip Color| Not Applicable| **Property:** *tooltipSettings.fill*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; tooltipSettings: { fill: 'gray' } <br/> }); <br/> treemap.appendTo('#container');|
|Tooltip Format| Not Applicable| **Property:** *tooltipSettings.format*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; tooltipSettings: { format: '${Population}' } <br/> }); <br/> treemap.appendTo('#container');|
|Tooltip Marker Shape| Not Applicable| **Property:** *tooltipSettings.markerShapes*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; tooltipSettings: { markerShapes: 'Circle' } <br/> }); <br/> treemap.appendTo('#container');|
|Tooltip Color Opacity| Not Applicable| **Property:** *tooltipSettings.opacity*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; tooltipSettings: { opacity: 0.5 } <br/> }); <br/> treemap.appendTo('#container');|
|Tooltip Text Style| Not Applicable| **Property:** *tooltipSettings.textStyle*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; tooltipSettings: { textStyle: { <br/> &nbsp; &nbsp; Color: 'red', opacity: 0.5, size: '12px' } } <br/> }); <br/> treemap.appendTo('#container');|

## Drilldown

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Drilldown| **Property:** *enableDrillDown*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; enableDrillDown: true <br/> })| **Property:** *enableDrillDown*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; enableDrillDown: true <br/> }); <br/> treemap.appendTo('#container');|
|Drilldown Level| **Property:** *drillDownLevel*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; drillDownLevel: 1 <br/> })| **Property:** *InitialDrillSettings.groupIndex*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; InitialDrillSettings: { groupIndex: 1 } <br/> }); <br/> treemap.appendTo('#container');|

## Methods

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Treemap Refresh Method| **Method:** *refresh*<br/><br/> $("#container").ejTreeMap({ "refresh" })| **Method:** *refresh*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; treemap.refresh(); }); <br/> treemap.appendTo('#container');|
|Method to Drilldown| **Method:** *drillDown*<br/><br/> $("#container").ejTreeMap({ "drillDown" })|Not Applicable|
|Append to Method| Not Applicable| **Method:** *appendTo*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> }); <br/> treemap.appendTo('#container');|
|Add Event Listener Method| Not Applicable| **Method:** *addEventListener*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; treemap.addEventListener(); <br/> }); <br/> treemap.appendTo('#container');|
|Treemap Destroy Method| Not Applicable| **Method:** *destroy*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; treemap.destroy(); <br/> }); <br/> treemap.appendTo('#container');|
|Treemap Exporting Method| Not Applicable| **Method:** *export*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; treemap.export('png','treemap'); <br/> }); <br/> treemap.appendTo('#container');|
|Get the Module Name| Not Applicable| **Method:** *getModuleName*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; this.getModuleName(); <br/> }); <br/> treemap.appendTo('#container');|
|Printing the Treemap| Not Applicable| **Method:** *print*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; treemap.print(); <br/> }); <br/> treemap.appendTo('#container');|
|Resizing the Treemap| Not Applicable| **Method:** *resizeOnTreeMap*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; treemap.resizeOnTreeMap(); <br/> }); <br/> treemap.appendTo('#container');|
|Inject Method (Tooltip)| Not Applicable| **Method:** *resizeOnTreeMap*<br/><br/> TreeMap.Inject(TreeMapTooltip); <br/> var treemap = new ej.treemap.TreeMap({ }); <br/> treemap.appendTo('#container');|
|Remove Event Listener Method| Not Applicable| **Method:** *removeEventListener*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; treemap.removeEventListener(); <br/> }); <br/> treemap.appendTo('#container');|

## Events

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Treemap Load Event| Not Applicable| **Event:** *load*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; load: function(e: ILoadEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Treemap Loaded Event| Not Applicable| **Event:** *loaded*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; loaded: function(e: ILoadedEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Event Before Print| Not Applicable| **Event:** *beforePrint*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; beforePrint: function(e: IPrintEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Click Event| **Event:** *click*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; click: function (args) { } <br/> })| **Event:** *click*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; click: function(e: IItemClickEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Drill Start Event| **Event:** *drillStarted*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; drillStarted: function (args) { } <br/> })| **Event:** *drillStart*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; drillStart: function(e: IDrillStartEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Drill End Event| Not Applicable| **Event:** *drillEnd*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; drillEnd: function(e: IDrillEndEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Event on Item Click| Not Applicable| **Event:** *itemClick*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; itemClick: function(e: IItemClickEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Treemap Item Select Event| **Event:** *treeMapItemSelected*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; treeMapItemSelected: function (args) { } <br/> })| **Event:** *itemSelected*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; itemSelected: function(e: IItemSelectedEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Treemap Item Rendering Event| **Event:** *itemRendering*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; itemRendering: function (args) { } <br/> })| **Event:** *itemRendering*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; itemRendering: function(e: IItemRenderingEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Treemap Item Move Event| Not Applicable| **Event:** *itemMove*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; itemMove: function(e: IItemMoveEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Treemap Item Highlight Event| Not Applicable| **Event:** *itemHighlight*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; itemHighlight: function(e: IItemHighlightEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Template Header Render Event| **Event:** *headerTemplateRendering*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; headerTemplateRendering: function (args) { } <br/> })| Not Applicable|
|Drilldown Item Select Event| **Event:** *drillDownItemSelected*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; drillDownItemSelected: function (args) { } <br/> })| Not Applicable|
|Refresh Event| **Event:** *refreshed*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; refreshed: function (args) { } <br/> })| Not Applicable|
|Group Select Event| **Event:** *treeMapGroupSelected*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; treeMapGroupSelected: function (args) { } <br/> })| Not Applicable|
|Mouse Event| Not Applicable| **Event:** *mouseMove*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; mouseMove: function(e: IMouseMoveEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Resize Event| Not Applicable| **Event:** *resize*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; resize: function(e: IResizeEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Tooltip Render Event| Not Applicable| **Event:** *tooltipRendering*<br/><br/> var treemap = new ej.treemap.TreeMap({ <br/> &nbsp; tooltipRendering: function(e: ITreeMapTooltipRenderEventArgs): void { } <br/> }); <br/> treemap.appendTo('#container');|
|Double Click Event| **Event:** *doubleClick*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; doubleClick: function (args) { } <br/> })| Not Applicable|
|Right Click Event| **Event:** *rightClick*<br/><br/> $("#container").ejTreeMap({ <br/> &nbsp; rightClick: function (args) { } <br/> })| Not Applicable|