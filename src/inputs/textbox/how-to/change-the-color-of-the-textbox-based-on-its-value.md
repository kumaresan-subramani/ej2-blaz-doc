---
title: "Change the color of the TextBox based on its value"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Change the color of the TextBox based on its value

You can change the color of the TextBox by validating its value using regular expression in the `keyup` event for predicting the numeric values as demonstrated in the following code sample.

{% tab template= "textbox/text-color", sourceFiles="index.html,index.ts,index.css", es5Template="textcolor-template" %}

```html

           <label>Normal Input</label>
                <div class="e-input-group">
                    <input class="e-input" type="text" placeholder="Enter numeric values" onkeyup="onKeyup(this)" />
                </div>
          <label> Floating Input </label>
                <div class="e-float-input">
                    <input type="text" onkeyup="onKeyup(this)" required />
                    <span class="e-float-line"> </span>
                    <label class="e-float-text">Enter numeric values</label>
                </div>

```

{% endtab %}