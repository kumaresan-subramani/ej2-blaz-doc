# Leaf Item

The leaf item defines a visualized data element. Leaf item does not contain child nodes, but contains parent node if it specifies the levels in tree map. Leaf nodes can be customized.

## Leaf label

Label is represented by item name or value. Label will be appeared by specifying the [`labelPath`] property. You can customize the label style using the [`labelStyle`] property.

{% aspTab template="treemap/leafitem/leaflabel", sourceFiles="leaflabel.cs" %}

{% endaspTab %}

<!-- markdownlint-disable MD036 -->

**Label position and format**

You can position the label using the [`labelPosition`] property and format the text by specifying data values using the [`labelFormat`] property.

{% aspTab template="treemap/leafitem/format", sourceFiles="format.cs" %}

{% endaspTab %}

<!-- markdownlint-disable MD036 -->

**Label template and position**

You can display both text and image in leaf node using the [`template`] property, which can be placed anywhere in node using the [`templatePosition`] property.

{% aspTab template="treemap/leafitem/template", sourceFiles="template.cs" %}

{% endaspTab %}

<!-- markdownlint-disable MD036 -->

## Item gap

The [`gap`] property is used to separate an item from another item. Each item rectangle is split into equal space with specified gap.

{% aspTab template="treemap/leafitem/gap", sourceFiles="gap.cs" %}

{% endaspTab %}