---
title: "Set the rounded corner"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Set the rounded corner

Render the TextBox with `rounded corner` by adding the `e-corner` class to the input parent element.

>This rounded corner visible only in box model input component

{% tab template= "textbox/round-corner", sourceFiles="index.html,index.ts,index.css", es5Template="icon-template" %}

```html

        <div class="e-input-group e-corner">
            <input class="e-input" type="text" placeholder="Enter Date" />
            <span class="e-input-group-icon e-input-popup-date"></span>
        </div>

        <div class="e-float-input e-input-group e-corner">
            <input type='text' required />
            <span class="e-float-line"> </span>
            <label class="e-float-text">Enter Date </label>
            <span class="e-input-group-icon e-input-popup-date"></span>
        </div>

```

{% endtab %}