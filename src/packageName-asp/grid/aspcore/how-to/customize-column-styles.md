---
title: "Customize Column Styles"
component: "Grid"
description: "Learn how to Customize Column Styles."
---

# Customize Column Styles

You can customise the appearance of the header and content of a particular column using the [`customAttributes`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~CustomAttributes.html) property.

To customize the grid column, follow the given steps:

**Step 1**:

Create a CSS class with custom style to override the default style for rowcell and headercell.

```css
.e-grid .e-rowcell.customcss{
    background-color: #ecedee;
    color: 'red';
    font-family: 'Bell MT';
    font-size: 20px;
}

.e-grid .e-headercell.customcss{
    background-color: #2382c3;
    color: white;
    font-family: 'Bell MT';
    font-size: 20px;
}

```

**Step 2**:

Add the custom CSS class to the specified column by using the [`customAttributes`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~CustomAttributes.html) property.

```typescript
<e-grid-column field="Freight" headerText="Freight" width="150"  customAttributes=@(new { @class="customcss" } )></e-grid-column>

```

{% aspTab template="grid/how-to/custom-column-style", sourceFiles="custom-column-style.cs" %}

{% endaspTab %}
