---
title: "Formats"
component: "NumericTextBox"
description: "Custom formats in numeric textbox"
---

# Number Formats

You can format the value of NumericTextBox using [`format`](../api/numerictextbox#format) property.
The value will be displayed in the specified format when the component is in focused out state. The format string
supports both the [standard numeric format string](../common/internationalization#supported-format-string/)
and [custom numeric format string](../common/internationalization#custom-number-formatting-and-parsing/).

## Standard formats

From the [standard numeric formats](../common/internationalization#supported-format-string/), you can use the numeric related
format specifiers such as `n`,`p` and `c` in the NumericTextBox component. By using these format specifiers, you can achieve the percentage
and currency textbox behavior also.

The below example demonstrates percentage and currency formats.

{% tab template="numeric-textbox/standard-format", sourceFiles="app.ts,index.html,styles.css", es5Template="numeric-standard-template"  %}

```typescript

import {NumericTextBox} from '@syncfusion/ej2-inputs';

/* 'p' specifier */

let percent: NumericTextBox = new NumericTextBox({
    // sets percentage with 2 numbers of decimal places format
    format: 'p2',
    value: 0.5,
    min: 0,
    max: 1,
    step: 0.01,
    placeholder: 'Percentage format',
    floatLabelType: 'Auto'
});

percent.appendTo('#percent');

/* 'c' specifier */

let currency: NumericTextBox = new NumericTextBox({
    // sets currency with 2 numbers of decimal places format
    format: 'c2'
    value: 10,
    placeholder: 'Currency format',
    floatLabelType: 'Auto'
});

currency.appendTo('#currency');

```

{% endtab %}

## Custom formats

From the [custom numeric format string](../common/internationalization#custom-number-formatting-and-parsing/), you can provide any custom format by
combining one or more custom specifiers.

The below examples demonstrate format the value by using currency format string `#` and `0`.

{% tab template="numeric-textbox/custom-format", sourceFiles="app.ts,index.html,styles.css", es5Template="numeric-custom-template"  %}

```typescript

import {NumericTextBox} from '@syncfusion/ej2-inputs';

/* '#' specifier */

let numeric: NumericTextBox = new NumericTextBox({
    // sets the format using custom format string `#`
    format: '###.##',
    value: 10,
    placeholder: 'Custom format string #',
    floatLabelType: 'Auto'
});

numeric.appendTo('#numeric');

/* '0' specifier */

let numeric1: NumericTextBox = new NumericTextBox({
    // sets the format using custom format string `0`
    format: '000.00',
    value: 10,
    placeholder: 'Custom format string 0',
    floatLabelType: 'Auto'
});

numeric1.appendTo('#numeric1');

```

{% endtab %}
