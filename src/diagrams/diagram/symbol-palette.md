---
title: "Symbol Palette"
component: "Diagram"
description: "The symbol palette displays a collection of palettes which shows a set of nodes and connectors."
---

# Symbol Palette

The **SymbolPalette** displays a collection of palettes. The palette shows a set of nodes and connectors. It allows to drag and drop the nodes and connectors into the diagram.

## Create symbol palette

The `Width` and `Height` properties of the symbol palette allows to define the size of the symbol palette.

```csharp
@using Syncfusion.Blazor.Diagrams

@* Initializes the symbol palette *@
<SfSymbolPalette id="palettes"  Height="700px">
</SfSymbolPalette>
```

## Add palettes to SymbolPalette

A palette allows to display a group of related symbols and it textually annotates the group with its header.
A [`Palettes`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SymbolPalettePalette.html) can be added as a collection of symbol groups.

The collection of predefined symbols can be added in palettes using the [`Symbols`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SymbolPalettePalette~Symbols.html) property.

To initialize a palette, define a JSON object with the property [`Id`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SymbolPalettePalette~Id.html) that is unique ID is set to the palettes.

The following code example illustrates how to define a palette and how its added to symbol palette.

```csharp
@using Syncfusion.Blazor.Diagrams
@using Syncfusion.Blazor.Navigations
@using System.Collections.ObjectModel
@* Initializes the symbol palette *@
@* Defines how many palettes can be at expanded mode at a time *@
<SfSymbolPalette Height="600px" SymbolHeight="80" SymbolWidth="80" EnableAnimation="false" ExpandMode="ExpandMode.Multiple">
    <SymbolPalettePalettes>
        @* Adds the palette items to palette *@
        <SymbolPalettePalette Id="basic" Expanded="true" Symbols="@BasicShapes" IconCss="e-ddb-icons e-flow" Title="Basic Shapes">
        </SymbolPalettePalette>
        <SymbolPalettePalette Id="flow" Expanded="true" Symbols="@FlowShapes" IconCss="e-ddb-icons e-flow" Title="Flow Shapes">
        </SymbolPalettePalette>
        <SymbolPalettePalette Id="connector" Expanded="true" Symbols="@Connectors" IconCss="e-ddb-icons e-connector" Title="Connectors">
        </SymbolPalettePalette>
    </SymbolPalettePalettes>
</SfSymbolPalette>

@code{
    // Defines palette's basic-shape collection
    public ObservableCollection<DiagramNode> BasicShapes { get; set; }

    // Defines palette's flow-shape collection
    public ObservableCollection<DiagramNode> FlowShapes { get; set; }

    // Defines palette's connector collection
    public ObservableCollection<DiagramConnector> Connectors { get; set; }

    protected override void OnInitialized()
    {
        //Initialize the basicshapes for the symbol palette
        BasicShapes = new ObservableCollection<DiagramNode>()
    {
            new DiagramNode()
            {
                Id = "Rectangle",
                Shape = new DiagramShape() { Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Rectangle }
            },
            new DiagramNode()
            {
                Id = "Ellipse",
                Shape = new DiagramShape() { Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Ellipse }
            },
            new DiagramNode()
            {
                Id = "Hexagon",
                Shape = new DiagramShape() { Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Hexagon }
            }
        };

        //Initialize the flowshapes for the symbol palette
        FlowShapes = new ObservableCollection<DiagramNode>()
    {
            new DiagramNode()
            {
                Id = "process",
                Shape = new DiagramShape() { Type = Shapes.Flow, FlowShape = Syncfusion.Blazor.Diagrams.FlowShapes.Process }
            },
            new DiagramNode()
            {
                Id = "document",
                Shape = new DiagramShape() {Type = Shapes.Flow, FlowShape = Syncfusion.Blazor.Diagrams.FlowShapes.Document}
            },
            new DiagramNode()
            {
                Id = "predefinedprocess",
                Shape = new DiagramShape() { Type = Shapes.Flow, FlowShape = Syncfusion.Blazor.Diagrams.FlowShapes.PreDefinedProcess}
            }
        };
        //Initializes connector symbols for the symbol palette
        Connectors = new ObservableCollection<DiagramConnector>()
    {
            new DiagramConnector()
            {
                Id = "Link1",
                Type = Segments.Orthogonal,
                SourcePoint = new ConnectorSourcePoint() { X = 0, Y = 0 },
                TargetPoint = new ConnectorTargetPoint() { X = 40, Y = 40 },
                Style = new ConnectorShapeStyle() { StrokeWidth = 1 },
                TargetDecorator = new ConnectorTargetDecorator() { Shape = DecoratorShapes.Arrow }
            },
            new DiagramConnector()
            {
                Id = "Link2",
                Type = Segments.Straight,
                SourcePoint = new ConnectorSourcePoint() { X = 0, Y = 0 },
                TargetPoint = new ConnectorTargetPoint() { X = 40, Y = 40 },
                Style = new ConnectorShapeStyle() { StrokeWidth = 1 },
                TargetDecorator = new ConnectorTargetDecorator() { Shape = DecoratorShapes.Arrow }
            },
            new DiagramConnector()
            {
                Id = "Link3",
                Type = Segments.Bezier,
                SourcePoint = new ConnectorSourcePoint() { X = 0, Y = 0 },
                TargetPoint = new ConnectorTargetPoint() { X = 40, Y = 40 },
                Style = new ConnectorShapeStyle() { StrokeWidth = 1 },
                TargetDecorator = new ConnectorTargetDecorator() { Shape = DecoratorShapes.None }
            }
        };
    }
}
```

## Customize the palette header

Palettes can be annotated with its header texts.

The [`Title`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SymbolPalettePalette~Title.html) displayed as the header text of palette.

The [`Expanded`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SymbolPalettePalette~Expanded.html) property of palette allows to expand/collapse its palette items.

The [`Height`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SymbolPalettePalette~Height.html) property of palette sets the height of the symbol group.

The [`IconCss`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SymbolPalettePalette~IconCss.html) property sets the content of the symbol group.

## Stretch the symbols into the palette

The [`Fit`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SymbolInfo~Fit.html) property defines whether the symbol has to be fit inside the size, that is defined by the symbol palette. For example, when you resize the rectangle in the symbol, ratio of the rectangle size has to be maintained rather changing into square shape. The following code example illustrates how to customize the symbol size.

```csharp
@using Syncfusion.Blazor.Diagrams
@using System.Collections.ObjectModel
@* Initialize Symbol palette with customize symbol size*@
<SfSymbolPalette Height="600px" SymbolHeight="60" SymbolWidth="60" SymbolInfo="@symbolInfo">
    <SymbolPalettePalettes>
        @* Sets the palette header property for the symbols *@
        <SymbolPalettePalette Id="basic" Expanded="true" Symbols="@BasicShapes" IconCss="e-ddb-icons e-flow" Title="Basic Shapes">
        </SymbolPalettePalette>
    </SymbolPalettePalettes>
</SfSymbolPalette>

@code{
    // Defines palette's basic-shape collection
    public ObservableCollection<DiagramNode> BasicShapes { get; set; }
    public SymbolInfo symbolInfo;
    protected override void OnInitialized()
    {
        // Enables to fit the content into the specified palette item size. When it is set as false, the element is rendered with actual node size
        symbolInfo = new SymbolInfo() { Fit = true };
        //Initialize the basicshapes for the symbol palette
        BasicShapes = new ObservableCollection<DiagramNode>()
    {
            new DiagramNode()
            {
                Id = "Rectangle",
                Shape = new DiagramShape() { Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Rectangle }
            }
        };
    }
}

```

## Add/Remove symbols to palette at runtime

* Symbols can be added to palette at runtime by using public method, [`AddPaletteItem`](../api/diagram/palette#addPaletteItem-number).

* Symbols can be removed from palette at runtime by using public method, [`RemovePaletteItem`](../api/diagram/palette#removePaletteItem-number).

## Customize the size of symbols

The size of the individual symbol can be customized. The [`SymbolWidth`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SfSymbolPalette~SymbolWidth.html) and  [`SymbolHeight`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SfSymbolPalette~SymbolHeight.html) properties of node enables you to define the size of the symbols. The following code example illustrates how to change the size of a symbol.

```csharp
@using Syncfusion.Blazor.Diagrams
@using System.Collections.ObjectModel
@* Initialize Symbol palette with customize symbol size*@
<SfSymbolPalette Height="600px" SymbolHeight="60" SymbolWidth="60">
    @* Sets the margin for the symbols *@
    <SymbolMargin Left="15" Bottom="15" Right="15" Top="15"></SymbolMargin>
    <SymbolPalettePalettes>
        <SymbolPalettePalette Id="basic" Expanded="true" Symbols="@BasicShapes" IconCss="e-ddb-icons e-flow" Title="Basic Shapes">
        </SymbolPalettePalette>
    </SymbolPalettePalettes>
</SfSymbolPalette>

@code{
    // Defines palette's basic-shape collection
    public ObservableCollection<DiagramNode> BasicShapes { get; set; }
    protected override void OnInitialized()
    {
        BasicShapes = new ObservableCollection<DiagramNode>()
    {
            new DiagramNode()
            {
                Id = "Rectangle",
                Shape = new DiagramShape() { Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Rectangle }
            },
            new DiagramNode()
            {
                Id="Ellipse" ,
                Shape = new DiagramShape(){ Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Ellipse  }
            },
            new DiagramNode()
            {
                Id="Hexagon" ,
                Shape = new DiagramShape(){ Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Hexagon  }
            }
        };
    }
}

```

The [`SymbolMargin`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SfSymbolPalette~SymbolMargin.html) property is used to create the space around
elements, outside of any defined borders.

## Symbol preview

The symbol preview size of the palette items can be customized using [`SymbolPreview`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SfSymbolPalette~SymbolPreview.html).
The [`Width`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SymbolPaletteSymbolPreview~Width.html) and [`Height`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SymbolPaletteSymbolPreview~Height.html) properties of SymbolPalette enables you to define the preview size to all the symbol palette items.
The [`Offset`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SymbolPaletteSymbolPreview~Offset.html) of the dragging helper relative to the mouse cursor.

The following code example illustrates how to change the preview size of a palette item.

```csharp
@using Syncfusion.Blazor.Diagrams
@using System.Collections.ObjectModel
@* Initialize Symbol palette with customize symbol size*@
<SfSymbolPalette ID="palettes" Height="600px" SymbolHeight=60 SymbolWidth=60>
    @* Sets the margin for the symbols *@
    <SymbolMargin Left="15" Bottom="15" Right="15" Top="15"></SymbolMargin>
    @* Specifies the preview size and position to symbol palette items *@
    <SymbolPaletteSymbolPreview Height="100" Width="100">
        <SymbolPreviewOffset X="0.5" Y="0.5"></SymbolPreviewOffset>
    </SymbolPaletteSymbolPreview>
    <SymbolPalettePalettes>
        <SymbolPalettePalette Id="basic" Expanded="true" Symbols="@BasicShapes" IconCss="e-ddb-icons e-flow" Title="Basic Shapes">
        </SymbolPalettePalette>
    </SymbolPalettePalettes>
</SfSymbolPalette>


@code{
     // Defines palette's basic-shape collection
    public ObservableCollection<DiagramNode> BasicShapes { get; set; }
    protected override void OnInitialized()
    {
       BasicShapes = new ObservableCollection<DiagramNode>()
        {
            new DiagramNode()
            {
                Id = "Rectangle",
                Shape = new DiagramShape() {
                    Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Rectangle
                }
            },
            new DiagramNode()
            {
                Id="Ellipse",
                Shape = new DiagramShape() {
                    Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Ellipse
                }
            },
            new DiagramNode()
            {
                Id="Hexagon",
                Shape = new DiagramShape() {
                    Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Hexagon
                }
            }
        };
    }
}
```

## Default settings

While adding more number of symbols such as nodes and connectors to the palette, define the default settings for those objects through the [`NodeDefaults`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Diagrams.SfSymbolPalette~NodeDefaults.html) and the `ConnectorDefaults` properties of diagram allows to define the default settings for nodes and connectors.

```csharp
@using Syncfusion.Blazor.Diagrams
@using System.Collections.ObjectModel
@using Syncfusion.Blazor.Navigations;
@* Initialize Symbol palette with customize symbol size*@
<SfSymbolPalette Height="600px" ExpandMode="ExpandMode.Multiple" NodeDefaults="@PaletteNodeDefaults">
    <SymbolPalettePalettes>
        @* Sets the palette header property for the symbols *@
        <SymbolPalettePalette Id="basic" Expanded="true" Symbols="@BasicShapes" IconCss="e-ddb-icons e-flow" Title="Basic Shapes">
        </SymbolPalettePalette>
        <SymbolPaletteSymbolPreview Height="100" Width="100">
            <SymbolPreviewOffset X="0.5" Y="0.5"></SymbolPreviewOffset>
        </SymbolPaletteSymbolPreview>
        <SymbolMargin Left="15" Bottom="15" Right="15" Top="15"></SymbolMargin>
    </SymbolPalettePalettes>
</SfSymbolPalette>

@code{
     // Defines palette's basic shape collection
    public ObservableCollection<DiagramNode> BasicShapes { get; set; }

    // Defines the default values for Nodes
    public DiagramNode PaletteNodeDefaults;

    protected override void OnInitialized()
    {
        BasicShapes = new ObservableCollection<DiagramNode>()
    {
            new DiagramNode()
            {
                Id = "Rectangle",
                Shape = new DiagramShape() { Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Rectangle }
            },
            new DiagramNode()
            {
                Id = "Ellipse",
                Shape = new DiagramShape() { Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Ellipse }
            },
            new DiagramNode()
            {
                Id = "Hexagon",
                Shape = new DiagramShape() { Type = Shapes.Basic, BasicShape = Syncfusion.Blazor.Diagrams.BasicShapes.Hexagon }
            }
        };
        // Sets the default values for Nodes
        PaletteNodeDefaults = new DiagramNode()
        {
            Width = 100,
            Height = 100,
            Style = new NodeShapeStyle() { StrokeColor = "#3A3A3A" }
        };
    }
}
```

## Palette interaction

Palette interaction notifies the element enter, leave, and dragging of the symbols into the diagram.

## Escape Key function

The diagram provides support to cancel the node from symbol palette when the ESC key is pressed.

## See Also

* [How to add the symbol to the diagram](./nodes)