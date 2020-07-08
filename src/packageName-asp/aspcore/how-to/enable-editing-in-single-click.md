---
title: "Enable editing in single click"
component: "Grid"
description: "Learn how to enable single click editing in the Essential JS 2 DataGrid control."
---

# Enable editing in single click

## Normal Editing

You can make a row editable on a single click with **Normal** mode of editing in Grid, by using the **startEdit** and **endEdit** methods.

Bind the **mousedown** event for Grid and in the event handler call the **startEdit** and **endEdit**, based on the clicked target element.

{% aspTab template="grid/how-to/single-click-inline-edit", sourceFiles="single-click-normal-edit.cs" %}

{% endaspTab %}

## Batch Editing

You can make a cell editable on a single click with **Batch** mode of editing in Grid, by using the **editCell** method.

Bind the **mousedown** event for Grid and in the event handler call the **editCell** method, based on the clicked target element.

{% aspTab template="grid/how-to/single-click-batch-edit", sourceFiles="single-click-batch-edit.cs" %}

{% endaspTab %}
