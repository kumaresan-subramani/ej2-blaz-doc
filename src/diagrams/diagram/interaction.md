---
title: "Interaction"
component: "Diagram"
description: "Diagram interaction allows how to select and edit nodes and connectors during runtime."
---

# Interaction

## Selection

Selector provides a visual representation of selected elements. It behaves like a container and allows to update the size, position, and rotation angle of the selected elements through interaction and by using program. Single or multiple elements can be selected at a time.

## Single selection

An element can be selected by clicking that element. During single click, all previously selected items are cleared. The following image shows how the selected elements are visually represented.

![Single Selection](images/single-select.gif)

* While selecting the diagram elements, the following events can be used to do your customization.
* When selecting/unselecting the diagram elements, the [`SelectionChanged`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramEvents~SelectionChanged.html) event gets triggered.

## Selecting a group

When a child element of any group is clicked, its contained group is selected instead of the child element. With consecutive clicks on the selected element, selection is changed from top to bottom in the hierarchy of parent group to its children.

## Multiple selection

Multiple elements can be selected with the following ways:

* Ctrl+Click

During single click, any existing item in the selection list be cleared, and only the item clicked recently is there in the selection list. To avoid cleaning the old selected item, Ctrl key must be on hold when clicking.

![Multiple Selection](images/multi-select-ctrl.gif)

* Selection rectangle/rubber band selection

Clicking and dragging the diagram area allows to create a rectangular region. The elements that are covered under the rectangular region are selected at the end.

![Multiple Rubberband Selection](images/multi-select-rubber-band.gif)

## Select/Unselect elements using program

The server-side methods [`Select`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SfDiagram~Select.html) and [`ClearSelection`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SfDiagram~ClearSelection.html) help to select or clear the selection of the elements at runtime.

Get the current selected items from the [`Nodes`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramSelectedItems~Nodes.html) and [`Connectors`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramSelectedItems~Connectors.html) collection of the [`SelectedItems`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SfDiagram~SelectedItems.html) property of the diagram model.

## Select entire elements in diagram programmatically

The server-side method [`SelectAll`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SfDiagram~SelectAll.html) used to select all the elements such as nodes/connectors in the diagram. Refer to the following link which shows how to use [`SelectAll`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SfDiagram~SelectAll.html) method on the diagram.

## Drag

* An object can be dragged by clicking and dragging it. When multiple elements are selected, dragging any one of the selected elements move every selected element.
* When you drag the elements in the diagram, the [`OnPositionChange`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramEvents~OnPositionChange.html) event gets triggered and to do customization in this event.

![Drag](images/drag.gif)

## Resize

* Selector is surrounded by eight thumbs. When dragging these thumbs, selected items can be resized.
* When one corner of the selector is dragged, opposite corner is in a static position.
* When a node is resized, the [`OnSizeChange`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramEvents~OnSizeChange.html) event gets triggered.

![Resize](images/resize.gif)

>Note:  While dragging and resizing, the objects are snapped towards the nearest objects to make better alignments. For better alignments, refer to `Snapping`.

## Rotate

* A rotate handler is placed above the selector. Clicking and dragging the handler in a circular direction lead to rotate the node.
* The node is rotated with reference to the static pivot point.
* Pivot thumb (thumb at the middle of the node) appears while rotating the node to represent the static point.

![Rotate](images/rotate.gif)

## Connection editing

* Each segment of a selected connector is editable with some specific handles/thumbs.

## End point handles

Source and target points of the selected connectors are represented with two handles. Clicking and dragging those handles help you to adjust the source and target points.

![Drag End Point Handles](images/connector-end-point.gif)

* If you drag the connector end points, then the following events can be used to do your customization.
* When you connect connector with ports/node or disconnect from it, the [`ConnectionChange`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramEvents~OnConnectionChange.html) event gets triggered.

## Straight segment editing

* End point of each straight segment is represented by a thumb that enables to edit the segment.
* Any number of new segments can be inserted into a straight line by clicking, when Shift and Ctrl keys are pressed (Ctrl+Shift+Click).

![Straight Segment Editing Addition](images/straight-segment-add.gif)

* Straight segments can be removed by clicking the segment end point, when Ctrl and Shift keys are pressed (Ctrl+Shift+Click).

![Straight Segment Editing Remove](images/straight-segment-remove.gif)

## Orthogonal thumbs

* Orthogonal thumbs allow you to adjust the length of adjacent segments by clicking and dragging it.
* When necessary, some segments are added or removed automatically, when dragging the segment. This is to maintain proper routing of orthogonality between segments.

![Orthogonal Segment Edit](images/orthogonal-segment-edit.gif)

## Drag and drop nodes over other elements

Diagram provides support to drop a node/connector over another node/connector. The [`OnDrop`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramEvents~OnDrop.html) event is raised to notify that an element is dropped over another one and it is disabled, by default. It can enabled with the constraints property.

## User handles

* User handles are used to add some frequently used commands around the selector. To create user handles, define and add them to the [`UserHandles`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle.html) collection of the [`SelectedItems`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SfDiagram~SelectedItems.html) property.
* The name property of user handle is used to define the name of the user handle and its further used to find the user handle at runtime and do any customization.

## Alignment

User handles can be aligned relative to the node boundaries. It has [`Margin`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Margin.html), [`Offset`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Offset.html), [`Side`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Side.html), [`HorizontalAlignment`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~HorizontalAlignment.html), and [`VerticalAlignment`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~VerticalAlignment.html) settings. It is quite tricky when all four alignments are used together but gives more control over alignment.

## Offset

The [`Offset`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Offset.html) property of [`UserHandles`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle.html) is used to align the user handle based on fractions. 0 represents top/left corner, 1 represents bottom/right corner, and 0.5 represents half of width/height.

## Side

The [`Side`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Side.html) property of [`UserHandles`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle_members.html) is used to align the user handle by using the [`Top`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Top.html), [`Bottom`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Bottom.html), [`Left`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Left.html), and [`Right`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Right.html) options.

## Horizontal and vertical alignments

The [`HorizontalAlignment`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~HorizontalAlignment.html) property of [`UserHandles`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle.html) is used to set how the user handle is horizontally aligned at the position based on the [`Offset`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Offset.html). The [`VerticalAlignment`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~VerticalAlignment.html) property is used to set how user handle is vertically aligned at the position.

## Margin

Margin is an absolute value used to add some blank space in any one of its four sides. The [`UserHandles`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle.html) can be displaced with the [`Margin`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Margin.html) property.

## Appearance

The appearance of the user handle can be customized by using the [`Size`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Size.html), [`BorderColor`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~BorderColor.html), [`BackgroundColor`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~BackgroundColor.html), [`Visible`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~Visible.html), [`PathData`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~PathData.html), and [`PathColor`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle~PathColor.html) properties of the [`UserHandles`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.DiagramUserHandle.html).

## Zoom pan

* When a large diagram is loaded, only certain portion of the diagram is visible. The remaining portions are clipped. Clipped portions can be explored by scrolling the scrollbars or panning the diagram.
* Diagram can be zoomed in or out by using Ctrl + mouse wheel.

![Zoom Pan](images/Zoom-pan.gif)

## Keyboard

Diagram provides support to interact with the elements with key gestures. By default, some in-built commands are bound with a relevant set of key combinations.

The following table illustrates those commands with the associated key values.

| Shortcut Key | Command | Description|
|--------------|---------|------------|
| Ctrl + A | `SelectAll` | Select all nodes/connectors in the diagram.|
| Ctrl + C | Copy | Copy the diagram selected elements.|
| Ctrl + V | Paste | Pastes the copied elements.|
| Ctrl + X | Cut | Cuts the selected elements.|
| Ctrl + Z | Undo | Reverses the last editing action performed on the diagram.|
| Ctrl + Y | Redo | Restores the last editing action when no other actions have occurred since the last undo on the diagram.|
| Delete | Delete | Deletes the selected elements.|
| Ctrl/Shift + Click on object |  | Multiple selection (Selector binds all selected nodes/connectors).|
| Up Arrow | Nudge(“up”) | `NudgeUp`: Moves the selected elements towards up by one pixel.|
| Down Arrow | Nudge(“down”) | `NudgeDown`: Moves the selected elements towards down by one pixel.|
| Left Arrow | Nudge(“left”) | `NudgeLeft`: Moves the selected elements towards left by one pixel.|
| Right Arrow | Nudge(“right”) | `NudgeRight`: Moves the selected elements towards right by one pixel.|
| Ctrl + MouseWheel | Zoom | Zoom (Zoom in/Zoom out the diagram).|
| F2 | `StartLabelEditing` | Starts to edit the label of selected element.|
| Esc | `EndLabelEditing` | Sets the label mode as view and stops editing.|

## See Also

* [How to control the diagram history](./undo-redo)
* [How to create overview control to the diagram](./overview)