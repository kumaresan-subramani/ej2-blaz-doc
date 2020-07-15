---
title: "Change the floating label color of the TextBox"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Change the floating label color of the TextBox

You can change the floating label color of the TextBox for both `success` and `warning` validation states by applying the following CSS styles.

```CSS

    /* For Success state */
    .e-float-input.e-success label.e-float-text,
    .e-float-input.e-success input:focus ~ label.e-float-text,
    .e-float-input.e-success input:valid ~ label.e-float-text {
      color: #22b24b;
    }

    /* For Warning state */
    .e-float-input.e-warning label.e-float-text,
    .e-float-input.e-warning input:focus ~ label.e-float-text,
   .e-float-input.e-warning input:valid ~ label.e-float-text {
      color: #ffca1c;
    }

```

{% tab template= "textbox/validation-state", sourceFiles="index.html,index.ts,index.css", es5Template="validation-template" %}

```html

       <div class="e-input-group e-float-input e-success">
        <input type="text" required>
        <span class="e-float-line"></span>
        <label class="e-float-text">Success</label>
       </div>
       <div class="e-input-group e-float-input e-warning">
         <input type="text" required>
         <span class="e-float-line"></span>
         <label class="e-float-text">Warning</label>
        </div>

```

{% endtab %}