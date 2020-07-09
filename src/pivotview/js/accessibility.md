---
title: "Accessibility"
component: "Pivot Table"
description: "Pivot table provides access to all the features through keyboard, on-screen reader, or other assertive technology devices."
---

# Accessibility

Accessibility is achieved in the pivot table component through WAI-ARIA standard and keyboard navigation. The pivot table features can be effectively accessed through assistive technologies such as screen readers.

## WAI-ARIA

WAI-ARIA (Accessibility Initiative – Accessible Rich Internet Applications) defines a way to increase the accessibility of web pages, dynamic content, and user interface components developed with Ajax, HTML, JavaScript,and related technologies. ARIA provides additional semantics to describe the role, state, and functionality of web components.

The following ARIA attributes are used in the pivot table:

* grid (role)
* row (role)
* gridcell (role)
* aria-selected (attribute)
* aria-expanded (attribute)
* aria-sort (attribute)
* aria-busy (attribute)
* aria-invalid (attribute)
* aria-grabbed (attribute)
* aria-owns (attribute)
* aria-label (attribute)

## Keyboard Navigation

All the pivot table actions can be controlled via keyboard keys. The applicable key combinations and its relative functionalities are listed below.

Interaction Keys |Description
-----|-----
<kbd>Home</kbd> |Goes to the first cell.
<kbd>End</kbd> |Goes to the last cell.
<kbd>Ctrl + Home</kbd> |Goes to the first row.
<kbd>Ctrl + End</kbd> |Goes to the last row.
<kbd>DownArrow</kbd> |Moves the cell focus downward.
<kbd>UpArrow</kbd> |Moves the cell focus upward.
<kbd>LeftArrow</kbd> |Moves the cell focus left side.
<kbd>RightArrow</kbd> |Moves the cell focus right side.
<kbd>Enter</kbd> | If current cell is in value sort state, then it performs value sorting. If the current cell is an expand/collapse cell then it performs expand/collapse operation (drill operation).
<kbd>Tab</kbd> | If the current is in focus, then moves the cell selection right side. If no cells are focused, then it moves to the next active element in the browser page.
<kbd>Shift + Tab</kbd> | If the current is in focus, then moves the cell selection left side. If no cells are focused, then it moves to the previous active element in the browser page.
<kbd>Delete</kbd> |Removes selected field from the Grouping Bar/Pivot Field List.