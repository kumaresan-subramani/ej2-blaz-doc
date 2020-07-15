---
title: "Syncfusion JavaScript Range Slider API Migration"
component: "Slider"
description: "Learn how to migrate JavaScript Range Slider from Essential JS 1 to Essential JS 2 using API, methods and events."
---

# Migration from Essential JS 1

This article describes the API migration process of Slider component from Essential JS 1 to Essential JS 2

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Max value | **Property:**  *maxValue* <br />  var sliderObj = new ej.Slider($("#slider"),{ <br /> maxValue: 60 <br /> }); | **Property:** *max* <br /> let slider: Slider = new Slider({ <br /> max : 100 <br /> }); <br /> slider.appendTo('#test'); |
| Min value | **Property:**  *minValue* <br /> var sliderObj = new ej.Slider($("#slider"),{<br /> minValue: 60 <br /> }); | **Property:** *min* <br /> let slider: Slider = new Slider({ <br /> min : 10 <br /> }); <br /> slider.appendTo('#test'); |
| Step | **Property:** *incrementStep, largeStep, smallStep, showSmallTicks* <br /> $("#slider").ejSlider({<br /> incrementStep: 20, <br />smallStep: 5, <br />largeStep: 40, <br />showSmallTicks: true <br /> });| **Property:** *ticks* <br /> let slider: Slider = new Slider({<br /> ticks: { placement: 'After', largeStep: 20, smallStep: 10, showSmallTicks: true }, <br /> }); <br />slider.appendTo('#test'); |
| Type | **Property:** *sliderType* <br /> var sliderObj = new ej.Slider($("#slider"),{<br />sliderType: ej.SliderType.Default <br /> }); | **Property:** *type* <br /> let slider: Slider = new Slider({ <br />type: 'Range' <br /> }); <br /> slider.appendTo('#test'); |
| Tooltip | **Property:** *showTooltip* <br /> var sliderObj = new ej.Slider($("#slider"),{<br /> showTooltip: true <br /> }); | **Property:** *tooltip* <br /> let slider: Slider = new Slider({ <br /> tooltip: { placement: 'Before', isVisible: true, showOn: 'Always' },<br /> }); <br /> slider.appendTo('#test'); |
| RTL | **Property:** *enableRTL* <br /> var sliderObj = new ej.Slider($("#slider"),{<br /> enableRTL: false <br /> }); | **Property:** *enableRtl* <br /> let slider: Slider = new Slider({<br /> enableRtl: false <br /> }); <br /> slider.appendTo('#test'); |
| Custom values | **Not Applicable** | **Property:** *customValues* <br /> let slider: Slider = new Slider({<br /> customValues: ['Mon', 'Tue', 'Wed'], <br />}); <br /> slider.appendTo('#test'); |
| Limit the slider movement | **Not Applicable** | **Property:** *limits* <br /> let slider: Slider = new Slider({ <br /> type: 'MinRange', <br /> limits: { enabled: true, minStart: 10, minEnd: 40 } <br />}); <br /> slider.appendTo('#test'); |
| Disable | **Method:** *disable* <br /> var sliderObj = $("#slider").data("ejSlider"); <br /> slider.disable(); | **Property:** *enabled* <br />let slider: Slider = new Slider({<br />value: 30<br />});<br />slider.appendTo('#test');<br />slider.enabled =false;<br /> |
| Enable | **Method:** *enable* <br /> var sliderObj = $("#slider").data("ejSlider"); <br /> slider.enable(); | **Property:** *enabled* <br />let slider: Slider = new Slider({<br />value: 30,<br />enabled:false<br />});<br />slider.appendTo('#test');<br />slider.enabled = true;<br /> |
| Set Value | **Method:** *setValue(value ,[enableAnimation])* <br /> var sliderObj = $("#slider").data("ejSlider");  <br /> slider.setValue(10); | **Property:** *value* <br /> let slider: Slider = new Slider({ }); <br />slider.appendTo('#test');<br />slider.value = 30;<br /> |
| Get Value | **Method:** *getValue()* <br /> var sliderObj = $("#slider").data("ejSlider");  <br /> slider.getValue(); | **Property:** *value* <br />let slider: Slider = new Slider({<br />Value:30<br />});<br />slider.appendTo('#test');<br />slider.value;<br /> |
| Destroy | **Not Applicable** | **Method:** *destroy()* <br /> let slider: Slider = new Slider({}); <br /> slider.appendTo('#test'); <br /> slider. destroy(); |
| Change | **Event:** *change* <br /> var sliderObj = new ej.Slider($("#slider"),{ <br />change: function (args) {} <br /> }); | **Event:** *changed* <br /> let slider: Slider = new Slider({<br /> changed: function(e: Event): void { } <br /> });  <br /> slider.appendTo('#test'); |
| Create | **Event:** *create* <br /> var sliderObj = new ej.Slider($("#slider"),{ <br /> create: function (args) {} <br /> }); | **Event:** *created* <br /> let slider: Slider = new Slider({<br /> created: function(e: Event): void { } <br /> });  <br /> slider.appendTo('#test'); |
| Destroy | **Event:** *destroy* <br /> var sliderObj = new ej.Slider($("#slider"),{ <br /> destroy: function (args) {} <br /> }); | **Method:** *destroy()* <br /> let slider: Slider = new Slider({<br />value:30<br />});<br />slider.appendTo('#test);<br />slider.destroy();<br /> |
| Slide | **Event:** *slide* <br /> var sliderObj = new ej.Slider($("#slider"),{<br /> slide: function (args) {} <br /> }); | **Event:** *change* <br /> let slider: Slider = new Slider({<br />change: function(e: Event): void { }<br />});<br />slider.appendTo('#test); |
| Start | **Event:** *start* <br /> var sliderObj = new ej.Slider($("#slider"),{ <br /> start: function (args) {} <br /> }); | **Event:** *created* <br /> let slider: Slider = new Slider({<br /> created: function(e: Event): void { }<br />});<br />slider.appendTo('#test); |
| Stop | **Event:** *stop* <br /> var sliderObj = new ej.Slider($("#slider"),{ <br /> stop: function (args) {} <br /> }); | **Event:** *changed* <br /> let slider: Slider = new Slider({<br />changed: function(e: Event): void { }<br />});<br />slider.appendTo('#test);<br />|
| Rendered Ticks | **Not Applicable** | **Event:** *renderedTicks* <br /> let slider: Slider = new Slider({ <br /> renderedTicks: function(e: Event): void { }  <br /> }); <br /> slider.appendTo('#test); |