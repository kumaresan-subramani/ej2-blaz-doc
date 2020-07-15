---
title: "Set the read-only TextBox"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Set the read-only TextBox

You can make the TextBox as `read-only` by setting the `readonly` attribute to the input element.

{% tab template= "textbox/getting-started-html", sourceFiles="index.html,index.ts", es5Template="basic-template" %}

```html

        <input class="e-input" type="text" placeholder="Enter Name" value="John" readonly/>

        <div class="e-float-input">
            <input type='text' required readonly value="John"/>
            <span class="e-float-line"></span>
            <label class="e-float-text e-label-top">Enter Name</label>
        </div>

```

{% endtab %}