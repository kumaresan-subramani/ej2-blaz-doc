---
title: "Multiline"
component: "Textbox"
description: "Explains about multiple lines of text like address, description and feedback are allows to fill in multiline textbox and it can be editable or can copy the text."
---
# Multiline TextBox

This feature allows the textbox to accept one or more lines of text like address, description, comments, and more.

## Create multiline textbox

You can convert the default textbox into the multiline textbox by setting the [multiline](../api/textbox/#multiline) API value as true or pass HTML5 textarea as element to the textbox.

> The multiline textbox allows you to resize it in vertical direction alone.

{% tab template="textbox/textarea", es5Template="textarea-template", sourceFiles="app.ts,index.html" %}

```typescript
import { TextBox } from '@syncfusion/ej2-inputs';

// Initialize TextBox component
let textareaObject: TextBox = new TextBox({
    placeholder: 'Enter your address',
    value: 'Mr. Dodsworth Dodsworth, System Analyst, Studio 103, The Business Center'
});

// Render initialized TextBox
textareaObject.appendTo('#default');
```

{% endtab %}

## Implementing floating label

You can achieve the floating label behavior in the multiline textbox by setting [floatLabelType](../api/textbox/#floatlabeltype) as 'Auto'. The placeholder text act as floating label to the multiline textbox. You can provide the placeholder text to the multiline textbox either by using the [placeholder](../api/textbox/#placeholder) property or placeholder attribute.

{% tab template="textbox/float", es5Template="float-template", sourceFiles="app.ts,index.html" %}

```typescript
import { TextBox } from '@syncfusion/ej2-inputs';

// Initialize TextBox component with floating type as auto
let floatTypeAuto: TextBox = new TextBox({
    placeholder: 'Enter your address',
    floatLabelType: 'Auto'
});
// Render initialized floating type as auto TextBox
floatTypeAuto.appendTo('#multiline-auto');

// Initialize TextBox component with floating type as always
let floatTypeAlways: TextBox = new TextBox({
    placeholder: 'Enter your address',
    floatLabelType: 'Always'
});
// Render initialized floating type as always TextBox
floatTypeAlways.appendTo('#multiline-always');

// Initialize TextBox component with floating type as never
let floatTypeNever: TextBox = new TextBox({
    placeholder: 'Enter your address',
    floatLabelType: 'Never'
});
// Render initialized floating type as never TextBox
floatTypeNever.appendTo('#multiline-never');
```

{% endtab %}

## Auto resizing

By default, you can manually resize the multiline textbox. But you can also create an `auto resizing` multiline textbox with both the initial and dynamic value change. It can be done by calculating the height of the textarea in the created event for initial value update and in the input event for dynamic value update of the auto resize multiline textbox, as explained in the following code sample.

{% tab template="textbox/autoresize", es5Template="autoresize-template", sourceFiles="app.ts,index.html" %}

```typescript

import { TextBox } from '@syncfusion/ej2-inputs';

// Initialize TextBox component
let autoResize: TextBox = new TextBox({
    placeholder: 'Enter your address',
    floatLabelType: 'Auto',
    value: "Mr. Dodsworth Dodsworth, System Analyst, Studio 103, The Business Center",
    created: (args: any)=> {
        autoResize.addAttributes({rows: "1"});
        autoResize.element.style.height = "auto";
        autoResize.element.style.height = (autoResize.element.scrollHeight-7) +"px";
    },
    input: (args: any)=> {
        args.event.currentTarget.style.height = "auto";
        args.event.currentTarget.style.height = (args.event.currentTarget.scrollHeight)+"px";
    }
});

// Render initialized TextBox
autoResize.appendTo('#default');
```

{% endtab %}

## Disable resizing

By default, the multiline textbox is rendered with resizable. You can disable the resize of the multiline textbox by applying the following CSS styles.

```CSS
    textarea.e-input,
    .e-float-input textarea,
    .e-float-input.e-control-wrapper textarea,
    .e-input-group textarea,
    .e-input-group.e-control-wrapper textarea {
        resize: none;
    }
```

{% tab template="textbox/disable", es5Template="disable-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { TextBox } from '@syncfusion/ej2-inputs';

// Initialize TextBox component
let disableResize: TextBox = new TextBox({
    placeholder: 'Enter your address',
    floatLabelType: 'Auto'
});

// Render initialized TextBox
disableResize.appendTo('#default');
```

{% endtab %}

## Limit the text length

By default, the text length of the multiline textbox is unlimited. You can limit the text length by setting the `maxLength` attribute using the [addAttributes](../api/textbox/#addattributes) method.

{% tab template="textbox/maxlength", es5Template="maxlength-template", sourceFiles="app.ts,index.html" %}

```typescript
import { TextBox } from '@syncfusion/ej2-inputs';
import { Button } from '@syncfusion/ej2-buttons';

// Initialize TextBox component
let maxLength: TextBox = new TextBox({
    placeholder: 'Enter your address',
    floatLabelType: 'Auto'
});

// Render initialized TextBox
maxLength.appendTo('#default');

// Initialize TextBox component
let addAttr: TextBox = new TextBox({
    placeholder: 'Enter your address',
    floatLabelType: 'Auto'
});

// Render initialized TextBox
addAttr.appendTo('#attr');

// Initialize Button component
let button: Button = new Button({
});
// Render initialized Button
button.appendTo('#button');

document.getElementById('button').onclick = (): void => {
    addAttr.addAttributes({maxlength: 15});
}

```

{% endtab %}

## Count characters

You can show the number of characters entered inside the textarea by calculating the character count in the input event of multiline textbox. The character count is updated while entering or deleting any character inside the textarea. The character count shows how many characters can be entered or left to be entered.

{% tab template="textbox/count", es5Template="count-template", sourceFiles="app.ts,index.html" %}

```typescript
import { TextBox } from '@syncfusion/ej2-inputs';

// Initialize TextBox component
let countChar: TextBox = new TextBox({
    placeholder: 'Enter your address',
    floatLabelType: 'Auto',
    input: (args: any)=> {
        let word, addresscountRem, addressCount;
        word = args.value;
        addressCount = word.length;
        addresscountRem = document.getElementById('numbercount');
        addresscountRem.textContent = addressCount+"/25";
    }
});

// Render initialized TextBox
countChar.appendTo('#default');

```

{% endtab %}
