# Data Label

Data labels are used to identify the name of items or groups in the tree map control. Data Labels will be shown by given specified path in the data source field.

The following options are available to customize labels in the tree map control.

## Format

You can customize the labels for each item using the [`labelFormat`] property in leafItemSettings.

The label format is shown in the following code example.

{% aspTab template="treemap/datalabel/format", sourceFiles="format.cs" %}

{% endaspTab %}

## Template

The template supports customizing labels of each leaf node using the [`labelTemplate`] property. It uses Essential JS2 [`Template engine`] to render elements. You can position templates using the [`templatePosition`] property.

The template concepts are shown in the following code example.

{% aspTab template="treemap/datalabel/template", sourceFiles="template.cs" %}

{% endaspTab %}

## InterSectAction

You can avoid overlapping by customizing labels in each item when they exceed their actual size using the [`interSectAction`] property in leafItemSettings.

The intersect action concepts are illustrated in the following code example.

{% aspTab template="treemap/datalabel/intersectaction", sourceFiles="intersectaction.cs" %}

{% endaspTab %}