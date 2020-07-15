---
title: "Drop-down list with tooltip"
component: "DropDownList"
description: "This section explains on how to render the tooltip on each list item of the Syncfusion JavaScript drop-down list control."
---

# DropDownList options with tooltip

You can achieve this behavior by using `ej2-tooltip` component. When the mouse hover on the DropDownList option that tooltip display some details related to hovered list item.

{% tab template="dropdownlist/how-to/tooltip",es5Template="tooltip", sourceFiles ='app.ts,index.html,styles.css' %}

```typescript

import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { Tooltip } from '@syncfusion/ej2-popups';

 //Initialize DropDownList component
let listObj: DropDownList = new DropDownList({
    // define the array of JSON data
    dataSource: [
        { id: '1', text: 'Australia', content: 'National sports is Cricket' },
        { id: '2', text: 'Bhutan', content: 'National sports is Archery' },
        { id: '3', text: 'China', content: 'National sports is Table Tennis' },
        { id: '4', text: 'Cuba', content: 'National sports is Baseball' },
        { id: '5', text: 'India', content: 'National sports is Hockey' },
        { id: '6', text: 'Spain', content: 'National sports is Football' },
        { id: '7', text: 'United States', content: 'National sports is Baseball' }
    ],
    // map the appropriate column to fields property
    fields: { text: 'text', tooltip: 'id' },
    // set the placeholder to the DropDownList input
    placeholder: 'Select a country',
    // bind the DropDownList close event
    close: () => { tooltip.close(); }
});
listObj.appendTo('#ddltooltip');

//Initialize Tooltip component
let tooltip: Tooltip = new Tooltip({
    // default content of tooltip
    content: 'Loading...',
    // set target element to tooltip
    target: '.e-list-item',
    // set position of tooltip
    position: 'top center',
    // bind beforeRender event
    beforeRender: onBeforeRender
});
tooltip.appendTo('body');

function onBeforeRender(args: TooltipEventArgs): void {
    // get the target element
    let listElement = document.getElementById('ddltooltip');
    let result: Object[] = listElement.ej2_instances[0].dataSource;
    let i: number;
    for ( i = 0; i < result.length; i++) {
        if (result[i].text === args.target.textContent) {
            this.content = result[i].content;
            this.dataBind();
            break;
        }
    }
}

```

{% endtab %}