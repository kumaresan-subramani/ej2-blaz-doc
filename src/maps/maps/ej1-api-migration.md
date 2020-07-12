---
title: "Migration from Essential JS 1"
component: "Maps"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components especially, maps component."
---

# Migration from Essential JS 1

This article describes the API migration process of Maps component from Essential JS 1 to Essential JS 2.

## Size Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Height| Not Applicable |**Property:** *height*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; height : '300px' <br/> }); <br/> maps.appendTo('#container');|
|Width| Not Applicable |**Property:** *width*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; width : '600px' <br/> }); <br/> maps.appendTo('#container');|

## Title and Subtitle Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Title Text| Not Applicable |**Property:** *title.text*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; titleSettings:{ text : 'Members of the UN Security Council' } <br/> }); <br/> maps.appendTo('#container')|
|Subtitle Text| Not Applicable |**Property:** *title.subtitle.text*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; titleSettings:{ subtitleSettings:{ text : 'In 2017' } <br/> } }); <br/> maps.appendTo('#container');|
|Title Alignment| Not Applicable |**Property:** *title.alignment*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; titleSettings:{ alignment : 'Center' } <br/> }); <br/> maps.appendTo('#container');|
|Subtitle Alignment| Not Applicable |**Property:** *title.subtitle.alignment*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; titleSettings:{ subtitleSettings:{ alignment : 'Center' } <br/> } }); <br/> maps.appendTo('#container');|

<!-- markdownlint-disable MD034 -->

## Layer Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Type | Not Applicable | **Property:** *layers.type*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ type:'Layer' }] <br/> }); <br/> maps.appendTo('#container')|
| Layer Type | **Property:** *layers.layerType*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ layerType:'geometry' }] <br/> }); | **Property:** *layers.layerType*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ layerType:'Geometry' }] <br/> }); <br/> maps.appendTo('#container')|
| Visible | Not Applicable | **Property:** *layers.visible*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ visible:true }] <br/> }); <br/> maps.appendTo('#container')|
| Bing Map Type | **Property:** *layers.bingMapType*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bingMapType:'aerial' }] <br/> }); | **Property:** *layers.bingMapType*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bingMapType:'Aerial' }] <br/> }); <br/> maps.appendTo('#container')|
| Bing Map Key | **Property:** *layers.key*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ key:'' }] <br/> }); | **Property:** *layers.key*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ key:'' }] <br/> }); <br/> maps.appendTo('#container')|
| URL Template | **Property:** *layers.urltemplate*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ urltemplate:'http://a.tile.openstreetmap.org/level/tileX/tileY.png' }] <br/> }); | **Property:** *layers.urlTemplate*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ urlTemplate:'http://a.tile.openstreetmap.org/level/tileX/tileY.png' }] <br/> }); <br/> maps.appendTo('#container')|
| Shape Data | **Property:** *layers.shapeData*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ shapeData:'WorldMap' }] <br/> }); | **Property:** *layers.shapeData*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapeData:'WorldMap' }] <br/> }); <br/> maps.appendTo('#container')|
| Data Source | **Property:** *layers.dataSource*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ dataSource:'PopulationData' }] <br/> }); | **Property:** *layers.dataSource*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ dataSource:'PopulationData' }] <br/> }); <br/> maps.appendTo('#container')|
| Query | Not Applicable | **Property:** *layers.query*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ query:'' }] <br/> }); <br/> maps.appendTo('#container')|
| Shape Data Path | **Property:** *layers.shapeDataPath*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ shapeDataPath:'Continent' }] <br/> });  | **Property:** *layers.shapeDataPath*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapeDataPath:'Continent' }] <br/> }); <br/> maps.appendTo('#container')|
| Shape Property Path | **Property:** *layers.shapePropertyPath*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ shapePropertyPath:'Continent' }] <br/> });  | **Property:** *layers.shapePropertyPath*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapePropertyPath:'Continent' }] <br/> }); <br/> maps.appendTo('#container')|
| Layer Animation | Not Applicable | **Property:** *layers.animationDuration*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ animationDuration: 100 }] <br/> }); <br/> maps.appendTo('#container')|

## Shape Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Shape Fill | **Property:** *layers.shapeSettings.fill*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ shapeSettings:{ fill:'#626171' } }] <br/> }); | **Property:** *layers.shapeSettings.fill*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapeSettings:{ fill: '#626171' } }] <br/> }); <br/> maps.appendTo('#container')|
| Shape Palette | **Property:** *layers.shapeSettings.colorPalette*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ shapeSettings:{ colorPalette:'customPalette' } }] <br/> }); | **Property:** *layers.shapeSettings.palette*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapeSettings:{ palette: ['red','green'] } }] <br/> }); <br/> maps.appendTo('#container')|
| Shape Point Radius | Not Applicable | **Property:** *layers.shapeSettings.circleRadius*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapeSettings:{ circleRadius: 10 } }] <br/> }); <br/> maps.appendTo('#container')|
| Shape Color Value Path | **Property:** *layers.shapeSettings.colorValuePath*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ shapeSettings:{ colorValuePath:'Country' } }] <br/> }); | **Property:** *layers.shapeSettings.colorValuePath*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapeSettings:{ colorValuePath:'Country'  } }] <br/> }); <br/> maps.appendTo('#container')|
| Shape Value Path | **Property:** *layers.shapeSettings.valuePath*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ shapeSettings:{ valuePath:'population' } }] <br/> }); | **Property:** *layers.shapeSettings.valuePath*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapeSettings:{ valuePath:'population' } }] <br/> }); <br/> maps.appendTo('#container')|
| Shape DashArray | Not Applicable | **Property:** *layers.shapeSettings.dashArray*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapeSettings:{ dashArray:'1,2' } }] <br/> }); <br/> maps.appendTo('#container')|
| Shape Opacity | Not Applicable | **Property:** *layers.shapeSettings.opacity*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapeSettings:{ opacity:'0.5' } }] <br/> }); <br/> maps.appendTo('#container')|
| Range Color Mapping | **Property:** *layers.shapeSettings.colorMappings.rangeColorMapping*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ shapeSettings:{ colorMappings:{ rangeColorMapping:[{ from:'10', to:'40', color: "#D84444" }] } } }] <br/> })  | **Property:** *layers.shapeSettings.colorMapping*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapeSettings:{ colorMapping:[{ from:10, to; 30, color: "#D84444" }] } }] <br/> }); <br/> maps.appendTo('#container')|
| Equal Color Mapping | **Property:** *layers.shapeSettings.colorMappings.equalColorMapping*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ shapeSettings:{ colorMappings:{ equalColorMapping:[{ { value: "Romney", color: "#D84444" } }] } } }] <br/> })  | **Property:** *layers.shapeSettings.colorMapping*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ shapeSettings:{  colorMapping: [{ value: 'Romney', color: '#D84444' }] } }] <br/> }); <br/> maps.appendTo('#container')|

## Marker Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Marker Data Source | **Property:** *layers.markers*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ markers:[{ "Name": "USA", "latitude": 38.8833, "longitude": -77.0167 }] }] <br/> })  | **Property:** *layers.markerSettings.dataSource*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ dataSource: [{ "Name": "USA", "latitude": 38.8833, "longitude": -77.0167 }] } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Template | **Property:** *layers.markerTemplate*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ markerTemplate:"Template" }] <br/> })  | **Property:** *layers.markerSettings.template*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ template:'Template' } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Visible | Not Applicable | **Property:** *layers.markerSettings.visible*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ visible:true } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Fill | Not Applicable | **Property:** *layers.markerSettings.fill*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ fill:'#FF471A' } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Height | Not Applicable | **Property:** *layers.markerSettings.height*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ height:20 } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Width | Not Applicable | **Property:** *layers.markerSettings.width*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ width:20 } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Shape | Not Applicable | **Property:** *layers.markerSettings.shape*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ shape:'Balloon' } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker ImageURL | Not Applicable | **Property:** *layers.markerSettings.imageUrl*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ imageUrl:'http://js.syncfusion.com/demos/web/Images/map/pin.png' } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Opacity | Not Applicable | **Property:** *layers.markerSettings.opacity*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ opacity:0.5 } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Legend Text | Not Applicable | **Property:** *layers.markerSettings.legendText*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ legendText:'China' } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Offset | Not Applicable | **Property:** *layers.markerSettings.offset*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ offset:new Point(20, 20) } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Animation Duration | Not Applicable | **Property:** *layers.markerSettings.animationDuration*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ animationDuration:2000 } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Animation Delay | Not Applicable | **Property:** *layers.markerSettings.animationDelay*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ animationDelay:100 } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker DashArray | Not Applicable | **Property:** *layers.markerSettings.dashArray*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{ dashArray:'2,3' } }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Selection | Not Applicable | **Property:** *layers.markerSettings.selectionSettings*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{  <br/> &nbsp; &nbsp; &nbsp;selectionSettings : { enable:true,fill:'#D2691E',opacity:1,enableMultiSelect:false } <br/> }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Highlight | Not Applicable | **Property:** *layers.markerSettings.highlightSettings*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{  <br/> &nbsp; &nbsp; &nbsp;highlightSettings : { enable:true,fill:'#D2691E',opacity:1 } <br/> }] <br/> }); <br/> maps.appendTo('#container')|
| Marker Tooltip | Not Applicable | **Property:** *layers.markerSettings.tooltipSettings*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ markerSettings:{  <br/> &nbsp; &nbsp; &nbsp;tooltipSettings : { visible:true,fill:'#363F4C',template:'TooltipTemplate', valuePath:'State', format:'${State}<br/>${District}' } <br/> }] <br/> }); <br/> maps.appendTo('#container')|

## Bubble Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Visible | **Property:** *layers.bubbleSettings.visible*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bubbleSettings: { showBubble:true }  }] <br/> })   | **Property:** *layers.bubbleSettings.visible*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{ visible:true  }] <br/> }); <br/> maps.appendTo('#container')|
| ValuePath | **Property:** *layers.bubbleSettings.valuePath*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bubbleSettings: { valuePath:'Population' }  }] <br/> })   | **Property:** *layers.bubbleSettings.valuePath*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{ valuePath:'Population'  }] <br/> }); <br/> maps.appendTo('#container')|
| MinValue | **Property:** *layers.bubbleSettings.minValue*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bubbleSettings: { minValue:20 }  }] <br/> })   | **Property:** *layers.bubbleSettings.minRadius*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{ minRadius:10  }] <br/> }); <br/> maps.appendTo('#container')|
| MaxValue | **Property:** *layers.bubbleSettings.maxValue*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bubbleSettings: { maxValue:30 }  }] <br/> })   | **Property:** *layers.bubbleSettings.maxRadius*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{ maxRadius:20  }] <br/> }); <br/> maps.appendTo('#container')|
| Bubble Type | Not Applicable | **Property:** *layers.bubbleSettings.bubbleType*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{ bubbleType:'Circle'  }] <br/> }); <br/> maps.appendTo('#container')|
| Color | **Property:** *layers.bubbleSettings.color*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bubbleSettings: { color:'green' }  }] <br/> }) | **Property:** *layers.bubbleSettings.fill*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{ fill:'red'  }] <br/> }); <br/> maps.appendTo('#container')|
| Opacity | **Property:** *layers.bubbleSettings.bubbleOpacity*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bubbleSettings: { bubbleOpacity:0.5 }  }] <br/> }) | **Property:** *layers.bubbleSettings.opacity*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{ opacity:0.5  }] <br/> }); <br/> maps.appendTo('#container')|
| Color Value Path | **Property:** *layers.bubbleSettings.colorValuePath*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bubbleSettings: { colorValuePath:'Population' }  }] <br/> }) | **Property:** *layers.bubbleSettings.colorValuePath*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{ colorValuePath:'Population'  }] <br/> }); <br/> maps.appendTo('#container')|
| Enable Tooltip | **Property:** *layers.bubbleSettings.showTooltip*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bubbleSettings: { showTooltip:true }  }] <br/> }) | **Property:** *layers.bubbleSettings.tooltipSettings.visible*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{  <br/> &nbsp; &nbsp; &nbsp;tooltipSettings : { visible:true } <br/> }] <br/> }); <br/> maps.appendTo('#container')|
| Tooltip Template | **Property:** *layers.bubbleSettings.tooltipTemplate*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bubbleSettings: { tooltipTemplate:'Template' }  }] <br/> }) | **Property:** *layers.bubbleSettings.tooltipSettings.template*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{  <br/> &nbsp; &nbsp; &nbsp;tooltipSettings : { template:'TooltipTemplate' } <br/> }] <br/> }); <br/> maps.appendTo('#container')|
| Bubble Selection | Not Applicable | **Property:** *layers.bubbleSettings.selectionSettings*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{  <br/> &nbsp; &nbsp; &nbsp;selectionSettings : { enable:true,fill:'#D2691E',opacity:1,enableMultiSelect:false } <br/> }] <br/> }); <br/> maps.appendTo('#container')|
| Bubble Highlight | Not Applicable | **Property:** *layers.bubbleSettings.highlightSettings*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{  <br/> &nbsp; &nbsp; &nbsp;highlightSettings : { enable:true,fill:'#D2691E',opacity:1 } <br/> }] <br/> }); <br/> maps.appendTo('#container')|
| Range Color Mapping | **Property:** *layers.bubbleSettings.colorMappings.rangeColorMapping*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bubbleSettings:{ colorMappings:{ rangeColorMapping:[{ from:'10', to:'40', color: "#D84444" }] } } }] <br/> })  | **Property:** *layers.bubbleSettings.colorMapping*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{ colorMapping:[{ from:10, to; 30, color: "#D84444" }] } }] <br/> }); <br/> maps.appendTo('#container')|
| Equal Color Mapping | **Property:** *layers.bubbleSettings.colorMappings.equalColorMapping*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ bubbleSettings:{ colorMappings:{ equalColorMapping:[{ { value: "Romney", color: "#D84444" } }] } } }] <br/> })  | **Property:** *layers.bubbleSettings.colorMapping*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ bubbleSettings:{  colorMapping: [{ value: 'Romney', color: '#D84444' }] } }] <br/> }); <br/> maps.appendTo('#container')|

## DataLabel Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Visible | **Property:** *layers.labelSettings.showLabels*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ labelSettings: { showLabels:true }  }] <br/> }) | **Property:** *layers.dataLabelSettings.visible*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ dataLabelSettings:{ visible:true  }] <br/> }); <br/> maps.appendTo('#container')|
| Label Path | **Property:** *layers.labelSettings.labelPath*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ labelSettings: { labelPath:'Continent' }  }] <br/> }) | **Property:** *layers.dataLabelSettings.labelPath*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ dataLabelSettings:{ labelPath:'Continent'  }] <br/> }); <br/> maps.appendTo('#container')|
| Enable Smart Label | **Property:** *layers.labelSettings.enableSmartLabel*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ labelSettings: { enableSmartLabel:true }  }] <br/> }) | Not Applicable |
| Smart Label Size | **Property:** *layers.labelSettings.smartLabelSize*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ labelSettings: { smartLabelSize:20 }  }] <br/> }) | Not Applicable |
| Label Length | **Property:** *layers.labelSettings.labelLength*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ labelSettings: { labelLength:20 }  }] <br/> }) | Not Applicable |
| Opacity | Not Applicable | **Property:** *layers.dataLabelSettings.opacity*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ dataLabelSettings:{ opacity:0.5  }] <br/> }); <br/> maps.appendTo('#container')|
| Smart Label Mode | Not Applicable | **Property:** *layers.dataLabelSettings.smartLabelMode*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ dataLabelSettings:{ smartLabelMode:'Trim'  }] <br/> }); <br/> maps.appendTo('#container')|
| InterSectAction | Not Applicable | **Property:** *layers.dataLabelSettings.intersectionAction*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ dataLabelSettings:{ intersectionAction:'Trim'  }] <br/> }); <br/> maps.appendTo('#container')|
| Template | Not Applicable | **Property:** *layers.dataLabelSettings.template*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ dataLabelSettings:{ template:'LabelTemplate'  }] <br/> }); <br/> maps.appendTo('#container')|

## Legend Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Visible | **Property:** *layers.legendSettings.showLegend*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { showLegend:true }  }] <br/> }) | **Property:** *legendSettings.visible*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { visible:true }} <br/> }); <br/> maps.appendTo('#container')|
| Toggle Visibility | **Property:** *layers.legendSettings.toggleVisibility*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { toggleVisibility:true }  }] <br/> }) | **Property:** *legendSettings.toggleVisibility*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { toggleVisibility:true }} <br/> }); <br/> maps.appendTo('#container')|
| Legend Location X | **Property:** *layers.legendSettings.positionX*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { positionX:250 }  }] <br/> }) | **Property:** *legendSettings.location*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { location:new Point(250,0) }} <br/> }); <br/> maps.appendTo('#container')|
| Legend Location Y | **Property:** *layers.legendSettings.positionY*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { positionY:350 } }] <br/> }) | **Property:** *legendSettings.location*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { location:new Point(0,350)}} <br/> }); <br/> maps.appendTo('#container')|
| Legend Type | **Property:** *layers.legendSettings.type*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { type:'Layers' }}] <br/> }) | **Property:** *legendSettings.type*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { type:'Layers'}} <br/> }); <br/> maps.appendTo('#container') |
| Label Orientation | **Property:** *layers.legendSettings.labelOrientation*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { labelOrientation:'Vertical' }} <br/> }) | Not Applicable |
| Legend Title | **Property:** *layers.legendSettings.title*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { title:'Union territories of India' }  } <br/> }) | **Property:** *legendSettings.title*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { title:'Union territories of India'}} <br/> }); <br/> maps.appendTo('#container') |
| Legend Mode | **Property:** *layers.legendSettings.mode*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { mode:'Default' }  }] <br/> }) | **Property:** *legendSettings.mode*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { mode:'Default'}} <br/> }); <br/> maps.appendTo('#container') |
| Legend Position | **Property:** *layers.legendSettings.position*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { position:'TopLeft' }}] <br/> }) | **Property:** *legendSettings.position*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { position:'Top'}} <br/> }); <br/> maps.appendTo('#container') |
| Legend DockOnMap | **Property:** *layers.legendSettings.dockOnMap*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { dockOnMap:true } } <br/> }) | Not Applicable |
| Legend Alignment | **Property:** *layers.legendSettings.dockPosition*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { dockPosition:'Right' }  }] <br/> }) | **Property:** *legendSettings.alignment*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { alignment:'Center'}} <br/> }); <br/> maps.appendTo('#container') |
| Legend Left Label | **Property:** *layers.legendSettings.leftLabel*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { leftLabel:'1000M' }  } <br/> }) | Not Applicable |
| Legend Right Label | **Property:** *layers.legendSettings.rightLabel*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { rightLabel:'3000M' }  }] <br/> }) | Not Applicable |
| Legend Shape | **Property:** *layers.legendSettings.icon*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { icon:'Circle' }  }] <br/> }) | **Property:** *legendSettings.shape*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { shape:'Circle'}} <br/> }); <br/> maps.appendTo('#container') |
| Legend Shape Height | **Property:** *layers.legendSettings.iconHeight*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { iconHeight: 20 }  }] <br/> }) | **Property:** *legendSettings.shapeHeight*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { shapeHeight:20 }} <br/> }); <br/> maps.appendTo('#container') |
| Legend Shape Width | **Property:** *layers.legendSettings.iconWidth*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { iconWidth: 20 }  } <br/> }) | **Property:** *legendSettings.shapeWidth*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { shapeWidth:20 }} <br/> }); <br/> maps.appendTo('#container') |
| Height | **Property:** *layers.legendSettings.height*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { height: 50 }  }] <br/> }) | **Property:** *legendSettings.width*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { height:'50' }} <br/> }); <br/> maps.appendTo('#container') |
| Width | **Property:** *layers.legendSettings.width*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { width: 150 }  }] <br/> }) | **Property:** *legendSettings.width*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { width:'150' }} <br/> }); <br/> maps.appendTo('#container') |
| Show Labels | **Property:** *layers.legendSettings.showLabels*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:[{ legendSettings: { showLabels: true }  }] <br/> }) | Not Applicable |
| Background | Not Applicable | **Property:** *legendSettings.background*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { background:'transparent' }} <br/> }); <br/> maps.appendTo('#container') |
| Label Position | Not Applicable | **Property:** *legendSettings.labelPosition*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { labelPosition:'After' }} <br/> }); <br/> maps.appendTo('#container') |
| Label Display Mode | Not Applicable | **Property:** *legendSettings.labelDisplayMode*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { labelDisplayMode:'Trim' }} <br/> }); <br/> maps.appendTo('#container') |
| Label Display Mode | Not Applicable | **Property:** *legendSettings.labelDisplayMode*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { labelDisplayMode:'Trim' }} <br/> }); <br/> maps.appendTo('#container') |
| Legend Orientation | Not Applicable | **Property:** *legendSettings.orientation*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { orientation:'Horizontal' }} <br/> }); <br/> maps.appendTo('#container') |
| Legend Item Fill | Not Applicable | **Property:** *legendSettings.fill*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { fill:'red' }}] <br/> }); <br/> maps.appendTo('#container') |
| Legend Shape Padding | Not Applicable | **Property:** *legendSettings.shapePadding*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { shapePadding:20 }} <br/> }); <br/> maps.appendTo('#container') |
| Legend Shape Border Color | Not Applicable | **Property:** *legendSettings.shapeBorder.color*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { shapeBorder:{ color:'green' } }} <br/> }); <br/> maps.appendTo('#container') |
| Legend Shape Border Width | Not Applicable | **Property:** *legendSettings.shapeBorder.width*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { shapeBorder:{ width:2 } }} <br/> }); <br/> maps.appendTo('#container') |
| Inverter Pointer | Not Applicable | **Property:** *legendSettings.invertedPointer*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { invertedPointer: true }} <br/> }); <br/> maps.appendTo('#container') |
| Item Text Style | Not Applicable | **Property:** *legendSettings.textStyle*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { textStyle: { size:'12px' } }} <br/> }); <br/> maps.appendTo('#container') |
| Title Style | Not Applicable | **Property:** *legendSettings.textStyle*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; legendSettings: { textStyle: { size:'12px' } }} <br/> }); <br/> maps.appendTo('#container') |

## Zooming Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable| Not Applicable | **Property:** *zoomSettings.enableZoom*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ enable:true } <br/> }); <br/> maps.appendTo('#container')|
|Minimum Zoom| **Property:** *zoomSettings.minValue*<br/><br/> $("#container").ejMap({ <br/> &nbsp; zoomSettings:{ minValue:2 } <br/> }); | **Property:** *zoomSettings.minZoom*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ minZoom:2 } <br/> }); <br/> maps.appendTo('#container')|
|Maximum Zoom| **Property:** *zoomSettings.maxValue*<br/><br/> $("#container").ejMap({ <br/> &nbsp; zoomSettings:{ maxValue:50 } <br/> }); | **Property:** *zoomSettings.maxZoom*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ maxZoom:5 } <br/> }); <br/> maps.appendTo('#container')|
|Mouse Wheel Zoom| **Property:** *zoomSettings.enableMouseWheelZoom*<br/><br/> $("#container").ejMap({ <br/> &nbsp; zoomSettings:{ enableMouseWheelZoom:true } <br/> }); | **Property:** *zoomSettings.maxZoom*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ mouseWheelZoom:true } <br/> }); <br/> maps.appendTo('#container')|
| Double Click Zoom | Not Applicable | **Property:** *zoomSettings.doubleClickZoom*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ doubleClickZoom:true } <br/> }); <br/> maps.appendTo('#container')|
| Pinch Zoom | Not Applicable | **Property:** *zoomSettings.pinchZooming*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ pinchZooming:true } <br/> }); <br/> maps.appendTo('#container')|
| Single Click Zoom | **Property:** *zoomSettings.enableZoomOnSelection*<br/><br/> $("#container").ejMap({ <br/> &nbsp; zoomSettings:{ enableZoomOnSelection:true } <br/> });  | **Property:** *zoomSettings.zoomOnClick*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ zoomOnClick:true } <br/> }); <br/> maps.appendTo('#container')|
| Zoom Factor | **Property:** *zoomSettings.factor*<br/><br/> $("#container").ejMap({ <br/> &nbsp; zoomSettings:{ factor:2 } <br/> });  | **Property:** *zoomSettings.zoomFactor*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ zoomFactor:2 } <br/> }); <br/> maps.appendTo('#container')|
| Toolbars | Not Applicable | **Property:** *zoomSettings.toolbars*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ toolbars:['ZoomIn'] } <br/> }); <br/> maps.appendTo('#container')|
| Toolbar Orientation | Not Applicable | **Property:** *zoomSettings.toolBarOrientation*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ toolBarOrientation:'Horizontal' } <br/> }); <br/> maps.appendTo('#container')|
| Toolbar Vertical Alignment | Not Applicable | **Property:** *zoomSettings.verticalAlignment*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ verticalAlignment:'Center' } <br/> }); <br/> maps.appendTo('#container')|
| Toolbar Horizontal Alignment | Not Applicable | **Property:** *zoomSettings.horizontalAlignment*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ horizontalAlignment:'Center' } <br/> }); <br/> maps.appendTo('#container')|
| Toolbar Highlight Color | Not Applicable | **Property:** *zoomSettings.highlightColor*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ highlightColor:'#e61576' } <br/> }); <br/> maps.appendTo('#container')|
| Toolbar Selection Color | Not Applicable | **Property:** *zoomSettings.selectionColor*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ selectionColor:'#e61576' } <br/> }); <br/> maps.appendTo('#container')|
| Toolbar Fill Color | Not Applicable | **Property:** *zoomSettings.color*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; zoomSettings:{ color:'#e61576' } <br/> }); <br/> maps.appendTo('#container')|

## Highlight And Selection Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Highlight Fill | **Property:** *layers.shapeSettings.highlightColor*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:{ shapeSettings:{ highlightColor:'green' } } <br/> }); | **Property:** *fill*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ highlightSettings:{ fill:'green' }}] <br/> }); <br/> maps.appendTo('#container')|
| Enable Highlight | **Property:** *layers.enableMouseHover*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:{ enableMouseHover:true } <br/> }); | **Property:** *enable*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ highlightSettings:{ enable:true }}] <br/> }); <br/> maps.appendTo('#container')|
| Highlight Border Color | **Property:** *layers.shapeSettings.highlightStroke*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:{ shapeSettings:{ highlightStroke:'red' } } <br/> }); | **Property:** *layers.highlightSettings.border.color*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ highlightSettings:{ border:{ color: 'green'} }}] <br/> }); <br/> maps.appendTo('#container')|
| Highlight Border Width | **Property:** *layers.shapeSettings.highlightBorderWidth*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:{ shapeSettings:{ highlightBorderWidth:'2' } } <br/> }); | **Property:** *layers.highlightSettings.border.width*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ highlightSettings:{ border:{ width: 2 } }}] <br/> }); <br/> maps.appendTo('#container')|
| Highlight Opacity | Not Applicable | **Property:** layers.*layers.highlightSettings.opacity*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ highlightSettings:{ opacity: 0.5 }}] <br/> }); <br/> maps.appendTo('#container')|
| Selection Fill | **Property:** *layers.shapeSettings.selectionColor*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:{ shapeSettings:{ selectionColor:'blue' } } <br/> }); | **Property:** *layers.selectionSettings.fill*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{selectionSettings:{ fill:'#D2691E' }}] <br/> }); <br/> maps.appendTo('#container')|
| Selection Enable | **Property:** *layers.enableSelection*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:{ enableSelection:true } <br/> }); | **Property:** *layers.selectionSettings.enable*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{selectionSettings:{ enable:true }}] <br/> }); <br/> maps.appendTo('#container')|
| Selection Border Width | **Property:** *layers.selectionSettings.selectionStrokeWidth*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:{ selectionSettings:{ selectionStrokeWidth:'2' } <br/> }); | **Property:** *layers.selectionSettings.border.width*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{selectionSettings:{ border:{ width:2 } }}] <br/> }); <br/> maps.appendTo('#container')|
| Selection Border Color | **Property:** *layers.selectionSettings.selectionStroke*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:{ layers:[{selectionSettings:{ selectionStroke:'red' }}] <br/> }); | **Property:** *layers.selectionSettings.border.color*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; ;layers:[{selectionSettings:{ border:{ color:'blue' } }}] <br/> }); <br/> maps.appendTo('#container')|
| Selection Opacity | Not Applicable | **Property:** *layers.selectionSettings.opacity*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{selectionSettings:{ opacity:2 }}] <br/> }); <br/> maps.appendTo('#container')|

## Navigation Line Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Visible | Not Applicable | **Property:** *layers.navigationLineSettings.visible*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ visible:true } }]   <br/> }); <br/> maps.appendTo('#container') |
| Width | Not Applicable | **Property:** *layers.navigationLineSettings.width*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ width:2 } }]   <br/> }); <br/> maps.appendTo('#container') |
| Longitude | Not Applicable | **Property:** *layers.navigationLineSettings.longitude*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ longitude: [-97.8717041015625, -89.6649169921875] } }]   <br/> }); <br/> maps.appendTo('#container') |
| Latitude | Not Applicable | **Property:** *layers.navigationLineSettings.latitude*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ latitude: [22.403410892712124, 21.282336521195344] } }]   <br/> }); <br/> maps.appendTo('#container') |
| DashArray | Not Applicable | **Property:** *layers.navigationLineSettings.dashArray*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ dashArray:"1,2" } }]   <br/> }); <br/> maps.appendTo('#container') |
| Color | Not Applicable | **Property:** *layers.navigationLineSettings.color*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ color:"green" } }]   <br/> }); <br/> maps.appendTo('#container') |
| Angle | Not Applicable | **Property:** *layers.navigationLineSettings.angle*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ angle:180 } }]   <br/> }); <br/> maps.appendTo('#container') |
| Arrow Position | Not Applicable | **Property:** *layers.navigationLineSettings.arrow.position*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ arrow:{ position:"start" } } }]   <br/> }); <br/> maps.appendTo('#container') |
| Show Arrow | Not Applicable | **Property:** *layers.navigationLineSettings.arrow.showArrow*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ arrow:{ showArrow:true } } }]   <br/> }); <br/> maps.appendTo('#container') |
| Arrow size | Not Applicable | **Property:** *layers.navigationLineSettings.arrow.size*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ arrow:{ size:2 } } }]   <br/> }); <br/> maps.appendTo('#container') |
| Arrow Color | Not Applicable | **Property:** *layers.navigationLineSettings.arrow.color*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ arrow:{ color:'red' } } }]   <br/> }); <br/> maps.appendTo('#container') |
| Arrow Offset | Not Applicable | **Property:** *layers.navigationLineSettings.arrow.offSet*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ navigationLineSettings:{ arrow:{ offSet:10 } } }]   <br/> }); <br/> maps.appendTo('#container') |

## Tooltip Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Tooltip Enable | **Property:** *layers.showTooltip*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:{ layers:[{ showTooltip: true }] <br/> }); | **Property:** *layers.tooltipSettings.visible*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ tooltipSettings:{ visible: true }] <br/> }); <br/> maps.appendTo('#container')|
| Tooltip Template | **Property:** *layers.tooltipTemplate*<br/><br/> $("#container").ejMap({ <br/> &nbsp; layers:{ layers:[{ tooltipTemplate: "Template" }] <br/> }); | **Property:** *layers.tooltipSettings.visible*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp;layers:[{ tooltipSettings:{ visible: true }] <br/> }); <br/> maps.appendTo('#container')|
| Value Path | Not Applicable | **Property:** *layers.tooltipSettings.valuePath*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ tooltipSettings:{ valuePath:'Population' }] <br/> }); <br/> maps.appendTo('#container')|
| Format | Not Applicable | **Property:** *layers.tooltipSettings.format*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ tooltipSettings:{ format:'${State}<br/>${Population}' }] <br/> }); <br/> maps.appendTo('#container')|
| Border Color | Not Applicable | **Property:** *layers.tooltipSettings.border.color*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ tooltipSettings:{ border :{ color:'red' }  }] <br/> }); <br/> maps.appendTo('#container')|
| Border Width | Not Applicable | **Property:** *layers.tooltipSettings.border.width*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ tooltipSettings:{ border :{ width:'' }  }] <br/> }); <br/> maps.appendTo('#container')|
| Text Style | Not Applicable | **Property:** *layers.tooltipSettings.textStyle*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layers:[{ tooltipSettings:{ textStyle: { size:'15px', color:'red', fontFamily:'arial', fontWeight:'bold', fontStyle:'normal', opacity:0.8 }}] <br/> }); <br/> maps.appendTo('#container')|

## Annotation Cutomization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Content | Not Applicable | **Property:** *legendSettings.annotations.content*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; annotations: { content:'<div>USA Population 2018</div>' }} <br/> }); <br/> maps.appendTo('#container') |
| Location X | Not Applicable | **Property:** *legendSettings.annotations.x*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; annotations: { x:'250px' }} <br/> }); <br/> maps.appendTo('#container') |
| Location Y | Not Applicable | **Property:** *legendSettings.annotations.y*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; annotations: { y:'150px' }} <br/> }); <br/> maps.appendTo('#container') |
| Vertical Alignment | Not Applicable | **Property:** *legendSettings.annotations.verticalAlignment*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; annotations: { verticalAlignment:'Center' }} <br/> }); <br/> maps.appendTo('#container') |
| Horizontal Alignment | Not Applicable | **Property:** *legendSettings.annotations.horizontalAlignment*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; annotations: { horizontalAlignment:'Center' }} <br/> }); <br/> maps.appendTo('#container') |
| Zindex | Not Applicable | **Property:** *legendSettings.annotations.zIndex*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; annotations: { zIndex:'-1' }} <br/> }); <br/> maps.appendTo('#container') |

## Maps Other Properties Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Projection Type | Not Applicable | **Property:** *projectionType*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; projectionType: 'Mercator' <br/> }); <br/> maps.appendTo('#container') |
| Background | **Property:** *background*<br/><br/> $("#container").ejMap({ <br/> &nbsp; background:'red' <br/> }); | **Property:** *background*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; background: 'red' <br/> }); <br/> maps.appendTo('#container') |
| Enable Group Separator | **Property:** *enableGroupSeparator*<br/><br/> $("#container").ejMap({ <br/> &nbsp; enableGroupSeparator:true <br/> }); | **Property:** *useGroupingSeparator*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; useGroupingSeparator: true <br/> }); <br/> maps.appendTo('#container') |
| Base Layer Index | **Property:** *baseMapIndex*<br/><br/> $("#container").ejMap({ <br/> &nbsp; baseMapIndex:0 <br/> }); | **Property:** *baseLayerIndex*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; baseLayerIndex: 0 <br/> }); <br/> maps.appendTo('#container') |
| locale | **Property:** *locale*<br/><br/> $("#container").ejMap({ <br/> &nbsp; locale:'en-us' <br/> }); | Not Applicable |
| Responsive | **Property:** *isResponsive*<br/><br/> $("#container").ejMap({ <br/> &nbsp; isResponsive:true <br/> }); | Not Applicable |
| Enable Pan | **Property:** *enablePan*<br/><br/> $("#container").ejMap({ <br/> &nbsp; enablePan:true <br/> }); | Not Applicable |
| Enable Navigation | **Property:** *navigationControl.enableNavigation*<br/><br/> $("#container").ejMap({ <br/> &nbsp; navigationControl:{ enableNavigation:true } <br/> }); | Not Applicable |
| Navigation Orientation | **Property:** *navigationControl.orientation*<br/><br/> $("#container").ejMap({ <br/> &nbsp; navigationControl:{ orientation:'vertical' } <br/> }); | Not Applicable |
| Navigation Dock Position | **Property:** *navigationControl.dockPosition*<br/><br/> $("#container").ejMap({ <br/> &nbsp; navigationControl:{ dockPosition:'centerleft' } <br/> }); | Not Applicable |
| Navigation Absolute Position | **Property:** *navigationControl.absolutePosition*<br/><br/> $("#container").ejMap({ <br/> &nbsp; navigationControl:{ absolutePosition:{ x: 100, y : 100 } } <br/> }); | Not Applicable |
| Dragging Selection | **Property:** *draggingOnSelection*<br/><br/> $("#container").ejMap({ <br/> &nbsp; draggingOnSelection : true <br/> }); | Not Applicable |
| Resize | **Property:** *enableResize*<br/><br/> $("#container").ejMap({ <br/> &nbsp; enableResize : true <br/> }); | Not Applicable |
| Enable Animation | **Property:** *enableAnimation*<br/><br/> $("#container").ejMap({ <br/> &nbsp; enableAnimation : true <br/> }); | Not Applicable |
| Enable Layer Animation | **Property:** *enableLayerChangeAnimation*<br/><br/> $("#container").ejMap({ <br/> &nbsp; enableLayerChangeAnimation : true <br/> }); | Not Applicable |
| Center Position | **Property:** *centerPosition*<br/><br/> $("#container").ejMap({ <br/> &nbsp; centerPosition:[90.52734374999999,30.41078179084589] <br/> }); | **Property:** *centerPosition*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; centerPosition:{ latitude: 30.41078179084589,longitude: 90.52734374999999 } <br/> }); <br/> maps.appendTo('#container') |

## Events

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Shape Selected | **Property:** *shapeSelected*<br/><br/> $("#container").ejMap({ <br/> &nbsp; shapeSelected:'MapShapeSelected' <br/> });  | **Property:** *shapeSelected*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; shapeSelected:'MapShapeSelected' <br/> }); <br/> maps.appendTo('#container') |
| Marker Selected | **Property:** *markerSelected*<br/><br/> $("#container").ejMap({ <br/> &nbsp; markerSelected:'MapMarkerSelected' <br/> });  | **Property:** *markerClick*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; markerClick:'MapMarkerSelected' <br/> }); <br/> maps.appendTo('#container') |
| Marker Move | **Property:** *markerEnter*<br/><br/> $("#container").ejMap({ <br/> &nbsp; markerEnter:'MapMarkerMove' <br/> });  | **Property:** *markerMouseMove*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; markerMouseMove:'MapMarkerMove' <br/> }); <br/> maps.appendTo('#container') |
| Marker Leave | **Property:** *markerLeave*<br/><br/> $("#container").ejMap({ <br/> &nbsp; markerLeave:'MapMarkerLeave' <br/> }); | Not Applicable |
| Legend Item Rendering | **Property:** *legendItemRendering*<br/><br/> $("#container").ejMap({ <br/> &nbsp; legendItemRendering:'MapLegendItemRendering' <br/> });  | Not Applicable |
| Display Text Rendering | **Property:** *displayTextRendering*<br/><br/> $("#container").ejMap({ <br/> &nbsp; displayTextRendering:'MapDisplayTextRendering' <br/> });  | **Property:** *dataLabelRendering*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; dataLabelRendering:'MapDataLabelRendering' <br/> }); <br/> maps.appendTo('#container')  |
| Legend Item Click | **Property:** *legendItemClick*<br/><br/> $("#container").ejMap({ <br/> &nbsp; legendItemClick:'MapLegendItemClick' <br/> });  | Not Applicable |
| Bubble Rendering | **Property:** *bubbleRendering*<br/><br/> $("#container").ejMap({ <br/> &nbsp; bubbleRendering:'MapBubbleRendering' <br/> });  | **Property:** *bubbleRendering*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; bubbleRendering:'MapBubbleRendering' <br/> }); <br/> maps.appendTo('#container')  |
| Shape Rendering | **Property:** *shapeRendering*<br/><br/> $("#container").ejMap({ <br/> &nbsp; shapeRendering:'MapShapeRendering' <br/> });  | **Property:** *shapeRendering*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; shapeRendering:'MapShapeRendering' <br/> }); <br/> maps.appendTo('#container')  |
| Zoomed In | **Property:** *zoomedIn*<br/><br/> $("#container").ejMap({ <br/> &nbsp; zoomedIn:'MapZooming' <br/> }); | Not Applicable |
| Render Completed | **Property:** *onRenderComplete*<br/><br/> $("#container").ejMap({ <br/> &nbsp; onRenderComplete:'MapRenderCompleted' <br/> }); | **Property:** *loaded*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; loaded:'MapRenderCompleted' <br/> }); <br/> maps.appendTo('#container')  |
| Panned | **Property:** *panned*<br/><br/> $("#container").ejMap({ <br/> &nbsp; panned:'MapPanned' <br/> }); | Not Applicable |
| zoomed Out | **Property:** *zoomedOut*<br/><br/> $("#container").ejMap({ <br/> &nbsp; zoomedOut:'MapZoomedOut' <br/> }); | Not Applicable |
| Mouse Over | **Property:** *mouseover*<br/><br/> $("#container").ejMap({ <br/> &nbsp; mouseover:'MapMouseOver' <br/> }); | Not Applicable |
| Mouse Leave | **Property:** *mouseleave*<br/><br/> $("#container").ejMap({ <br/> &nbsp; mouseover:'MapMouseLeave' <br/> }); | Not Applicable |
| Click | **Property:** *click*<br/><br/> $("#container").ejMap({ <br/> &nbsp; click:'ClickOnMap' <br/> }); | **Property:** *click*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; click:'ClickOnMap' <br/> }); <br/> maps.appendTo('#container') |
| Double Click | **Property:** *doubleClick*<br/><br/> $("#container").ejMap({ <br/> &nbsp; doubleClick:'DoubleClickOnMap' <br/> }); | **Property:** *doubleClick*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; doubleClick:'DoubleClickOnMap' <br/> }); <br/> maps.appendTo('#container') |
| Right Click | **Property:** *rightClick*<br/><br/> $("#container").ejMap({ <br/> &nbsp; rightClick:'RightClickOnMap' <br/> }); | **Property:** *rightClick*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; rightClick:'RightClickOnMap' <br/> }); <br/> maps.appendTo('#container') |
| Initial Load | **Property:** *onLoad*<br/><br/> $("#container").ejMap({ <br/> &nbsp; onLoad:'loadOnMap' <br/> }); | **Property:** *load*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; load:'loadOnMap' <br/> }); <br/> maps.appendTo('#container') |
| Before Print | Not Applicable | **Property:** *beforePrint*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; beforePrint:'MapBeforePrint' <br/> }); <br/> maps.appendTo('#container') |
| Resize | Not Applicable | **Property:** *resize*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; resize:'ResizeOnMap' <br/> }); <br/> maps.appendTo('#container') |
| Tooltip Render | Not Applicable | **Property:** *tooltipRender*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; tooltipRender:'MapTooltipRender' <br/> }); <br/> maps.appendTo('#container') |
| Item Selection | Not Applicable | **Property:** *itemSelection*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; itemSelection:'MapItemSelection' <br/> }); <br/> maps.appendTo('#container') |
| Item Highlight | Not Applicable | **Property:** *itemHighlight*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; itemHighlight:'MapItemHighlight' <br/> }); <br/> maps.appendTo('#container') |
| Shape Highlight | Not Applicable | **Property:** *shapeHighlight*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; shapeHighlight:'MapShapeHighlight' <br/> }); <br/> maps.appendTo('#container') |
| Layer Rendering | Not Applicable | **Property:** *layerRendering*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; layerRendering:'MapLayerRendering' <br/> }); <br/> maps.appendTo('#container') |
| Marker Rendering | Not Applicable | **Property:** *markerRendering*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; markerRendering:'MapMarkerRendering' <br/> }); <br/> maps.appendTo('#container') |
| Bubble Mouse Move | Not Applicable | **Property:** *bubbleMouseMove*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; bubbleMouseMove:'MouseMoveOnBubble' <br/> }); <br/> maps.appendTo('#container') |
| Bubble Mouse Move | Not Applicable | **Property:** *annotationRendering*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; annotationRendering:'MapAnnotationRendering' <br/> }); <br/> maps.appendTo('#container') |
| Animation Complete | Not Applicable | **Property:** *animationComplete*<br/><br/> let maps: Maps = new Maps({ <br/> &nbsp; animationComplete:'MapAnimationComplete' <br/> }); <br/> maps.appendTo('#container') |