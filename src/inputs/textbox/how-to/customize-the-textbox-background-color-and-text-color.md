---
title: "Customize the textbox background-color and text-color"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Customize the textbox background-color and text-color

You can customize the textbox styles such as background-color, text-color and border-color by overriding its default styles.

> To change the styles of the `floating label`, you must override the style to the input element.

{% tab template= "textbox/textbox-customize", sourceFiles="index.html,index.ts,index.css", es5Template="textbox-customize-template" %}

```html

        <label>Normal Input</label>
            <div class="e-input-group">
                <input class="e-input" type="text" placeholder="First Name" />
            </div>
        <label> Floating Input </label>
            <div class="e-float-input">
                <input type="text" required />
                <span class="e-float-line"> </span>
                <label class="e-float-text">Last Name</label>
            </div>

```

{% endtab %}