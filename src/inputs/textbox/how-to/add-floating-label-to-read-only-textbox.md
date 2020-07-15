---
title: "Add floating label to read-only textbox"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Add floating label to read-only textbox

You can achieve floating label for read-only textboxes by adding/removing `e-label-top` and `e-label-bottom` classes to the label element

In this sample, click the update value button to fill the read-only textbox with value and float a label.

{% tab template= "textbox/read-only", sourceFiles="index.html,index.ts,index.css", es5Template="read-only-template" %}

```html

        <div class="row">
            <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
                <div class="e-float-input">
                    <input class="e-input myField" id="myText" name="readonlyAttr"  type="text" readOnly>
                    <span class="e-float-line"></span>
                    <label class="e-float-text">Enter value</label>
                </div>
            </div>
        </div>
        <div class="row">
            <div class="col-xs-10 col-sm-10 col-lg-10 col-md-10">
                <button class="e-btn update_value" id='valuebtn' >Set value</button>
                <button class="e-btn remove_value" id='removebtn' >Remove value</button>
            </div>
        </div>

```

{% endtab %}