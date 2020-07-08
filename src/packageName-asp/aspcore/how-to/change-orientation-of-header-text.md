---
title: "Change the Orientation of Header Text"
component: "Grid"
description: "Learn how to Change the Orientation of Header Text."
---

# Change the Orientation of Header Text

You can change the orientation of the header text by using the [`customAttributes`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~CustomAttributes.html) property.

Ensure the following steps:

**Step 1**:

Create a CSS class with orientation style for the grid header cell.

```css
.orientationcss .e-headercelldiv {
    transform: rotate(90deg);
}

```

**Step 2**:

Add the custom CSS class to a particular column by using the [`customAttributes`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~CustomAttributes.html) property.

```typescript
    <e-grid-column field="ShipCity" headerText="Ship City" width="150" customAttributes="@(new { @class="orientationcss" })"></e-grid-column>

```

**Step 3**:

Resize the header cell height by using the following code.

```typescript
function setHeaderHeight(args) {
    var textWidth = document.querySelector(".orientationcss > div").scrollWidth;//Obtain the width of the headerText content.
    var headerCell = document.querySelectorAll(".e-headercell");
    for(var i = 0; i < headerCell.length; i++) {
        headerCell.item(i).style.height = textWidth + 'px'; //Assign the obtained textWidth as the height of the headerCell.
    }
}

```

{% aspTab template="grid/how-to/orientation", sourceFiles="orientation.cs" %}

{% endaspTab %}
