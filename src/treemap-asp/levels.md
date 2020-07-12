# Levels

You can give 'n' number of levels to the tree map. Each level can be separated using the [`groupPath`] property.

The following customization options are available to customize the tree map levels.

<!-- markdownlint-disable MD036 -->

**Group path**

The [`groupPath`] property is used to separate each level in tree map. The GroupPath accepts a field in dataSource.

{% aspTab template="treemap/levels/group_path", sourceFiles="group_path.cs" %}

{% endaspTab %}

<!-- markdownlint-disable MD036 -->

**Group gap**

The [`groupGap`] property is used to separate an item from every group or another item to differentiate the levels mentioned in the tree map.

{% aspTab template="treemap/levels/group_gap", sourceFiles="group_gap.cs" %}

{% endaspTab %}

<!-- markdownlint-disable MD036 -->

**Header format and alignment**

You can customize header using the [`headerFormat`] property in which fields are mapping from the dataSource. You can also align header using the [`headerAlignment`] property.

{% aspTab template="treemap/levels/header_format", sourceFiles="header_format.cs" %}

{% endaspTab %}

**Header height and style**

You can customize the font color, family, weight, and size using the [`headerStyle`] property. Based on font size, the header height can be given using the [`headerHeight`] property.

{% aspTab template="treemap/levels/header_height", sourceFiles="header_height.cs" %}

{% endaspTab %}

**Header template and position**

The treemap header supports to customize header of each item using the [`headerTemplate`] property. It uses Essential JS2 [`Template engine`] to render the elements. You can position the template using the [`templatePosition`] property.

The template concepts are illustrated in the following example.

{% aspTab template="treemap/levels/template", sourceFiles="template.cs" %}

{% endaspTab %}