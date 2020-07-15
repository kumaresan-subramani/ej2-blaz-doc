---
title: "Sizing"
component: "Textbox"
description: "Explains how to render text box with different sizes such as small and normal, which is applicable for both touch and mouse mode."
---

# Sizing

You can render the TextBox in two different sizes.

Property   | Description
------------ | -------------
  Normal     | By default, the TextBox is rendered with normal size.
  Small      | You need to add `e-small` class to the input element, or else add to the input container.

{% tab template= "textbox/icon-samples", sourceFiles="index.html,index.ts,index.css", es5Template="icon-template" %}

```html

      <h4> Normal Size </h4>

      <div class="e-input-group">
        <input class="e-input" type="text" placeholder="Enter Name" />
      </div>

      <div class="e-float-input">
        <input type='text' required />
        <span class="e-float-line"></span>
        <label class="e-float-text">Enter Name</label>
      </div>

      <div class="e-input-group">
        <input class="e-input" type="text" placeholder="Enter Date" />
        <span class="e-input-group-icon e-input-popup-date"></span>
      </div>

      <h4> Small Size </h4>

      <div class="e-input-group e-small">
        <input class="e-input" type="text" placeholder="Enter Name" />
      </div>

      <div class="e-float-input e-small">
        <input type='text' required />
        <span class="e-float-line"></span>
        <label class="e-float-text">Enter Name</label>
      </div>

      <div class="e-input-group e-small">
        <input class="e-input" type="text" placeholder="Enter Date" />
        <span class="e-input-group-icon e-input-popup-date"></span>
      </div>

```

{% endtab %}
