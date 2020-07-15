---
title: "Add floating label to TextBox programmatically"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Add floating label to TextBox programmatically

The `Floating Label TextBox` floats label above the TextBox after focusing, or entering a value in the TextBox.

Floating label supports the types of actions as given below.

Type     | Description
------------ | -------------
  Auto       | The floating label will float above the input after focusing, or entering a value in the input.
  Always     | The floating label will always float above the input.
  Never      | By default, never float the label in the input when the placeholder is available.

* Create a TypeScript file and import the `Input` modules from `ej2-inputs` library as shown below.

```typescript
import {Input} from '@syncfusion/ej2-inputs';
```

* Pass the `HTML Input` element and `floatLabelType` property as `Auto` to the `createInput` method.

* Set the `placeholder` value to the input element via `element attribute` or pass the parameter to the `createInput` method.

The `watermark label` will be updated based on the specified `placeholder` value of the `Floating Label TextBox`.

* You can add the `icons` on the input by passing `buttons` property value with the
class name `e-input-group-icon` as parameter to the `createInput` method.

{% tab template= "textbox/floating-label", sourceFiles="index.ts,index.html,index.css", es5Template="float-label-template" %}

```typescript

import { Input, InputObject } from  '@syncfusion/ej2-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let inputObj: InputObject;

let element: HTMLInputElement = <HTMLInputElement>document.createElement('input');
document.getElementById('input-container').appendChild(element);
Input.createInput({
    element: element,
    floatLabelType: "Auto",
    properties:{
        placeholder:'Enter Name'
    }
});

let element2: HTMLInputElement = <HTMLInputElement>document.createElement('input');
document.getElementById('input-container-01').appendChild(element2);
Input.createInput({
    element: element2,
    floatLabelType: "Always",
    properties:{
        placeholder:'Enter Name'
    }
});

let element3: HTMLInputElement = <HTMLInputElement>document.createElement('input');
document.getElementById('input-container-02').appendChild(element3);
Input.createInput({
    element: element3,
    floatLabelType: "Never",
    properties:{
        placeholder:'Enter Name'
    }
});

// Render float label TextBox with icon

let element4: HTMLInputElement = <HTMLInputElement>document.createElement('input');
document.getElementById('input-container-03').appendChild(element4);
Input.createInput({
    element: element4,
    floatLabelType: "Auto",
    buttons: ['e-input-group-icon e-input-down'],
    properties:{
        placeholder:'Enter Value'
    }
});

```

{% endtab %}