---
title: "Validation"
component: "Textbox"
description: "Covers how to apply different validation styles to the text box (input) control such as error, warning, and success with a ripple effect."
---

# Validation

The TextBox supports three types of validation styles namely `error`, `warning`, and `success`. These states are
enabled by adding corresponding classes `.e-error`, `.e-warning`, or `.e-success` to the input parent element.

{% tab template= "textbox/icon-samples", sourceFiles="index.html,index.ts,index.css", es5Template="icon-template" %}

```html

   <div class="e-input-group e-warning">
     <input class="e-input" type="text" placeholder="Input with warning" />
   </div>

   <div class="e-input-group e-error">
     <input class="e-input" type="text" placeholder="Input with error" />
   </div>

   <div class="e-input-group e-success">
     <input class="e-input" type="text" placeholder="Input with success" />
   </div>

```

{% endtab %}