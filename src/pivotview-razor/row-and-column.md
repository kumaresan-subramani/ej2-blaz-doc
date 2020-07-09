---
title: "Row and Column"
component: "Pivot Table"
description: "Miscellaneous aspects of customizing the pivot table."
---

<!-- markdownlint-disable MD012 -->

# Row and Column

## Width and Height

Allows end user to set the pivot table's height and width by using [`Height`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~Height.html) and [`Width`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~Width.html) properties in [`SfPivotView`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.SfPivotView%601.html) class respectively. The supported formats to set [`Height`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~Height.html) and [`Width`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~Width.html) properties are,

* Pixel: For example - 100, 200, "100px", "200px".
* Percentage: For example - "100%", "200%".
* Auto: It is applicable for [`Height`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~Height.html) property alone in-order to render the pivot table beyond its parent container height without vertical scrollbar. The parent container here would show its vertical scrollbar as soon as the component reaches beyond its dimension.

> The pivot table will not be displayed less than **400px**, since it's the minimum width of the component.

```csharp
    @using Syncfusion.Blazor.PivotView

   <SfPivotView TValue="ProductDetails" Width="550" Height="315px">
        <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
             <PivotViewFormatSettings>
                <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
            </PivotViewFormatSettings>
        </PivotViewDataSourceSettings>
    </SfPivotView>

    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }

```

![output](images/height-width.png)

## Row Height

Allows end user to set the height of each pivot table rows commonly using the [`RowHeight`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~RowHeight.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings_properties.html) class.

> By default, the [`RowHeight`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~RowHeight.html) property is set as **30** pixels for desktop layout and **36** pixels for mobile layout.
> The height of the column headers alone may vary when grouping bar feature is enabled.

In the below code sample, the [`RowHeight`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~RowHeight.html) property is set as **60** pixels.

```csharp
    @using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="ProductDetails">
        <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
            <PivotViewFormatSettings>
                <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
            </PivotViewFormatSettings>
        </PivotViewDataSourceSettings>
        <PivotViewGridSettings RowHeight=60></PivotViewGridSettings>
    </SfPivotView>

    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }

```

![output](images/row-height.png)

## Column Width

Allows end user to set the width of each pivot table columns commonly using the [`ColumnWidth`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~ColumnWidth.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings_properties.html) class.

> By default, the [`ColumnWidth`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~ColumnWidth.html) property is set as **110** pixels to each columns except the first column. For first column, **250** pixels and **200** pixels are set respectively with and without grouping bar.

In the below example, the [`ColumnWidth`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~ColumnWidth.html) property is set as **200** pixels.

```csharp
    @using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="ProductDetails">
        <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
             <PivotViewFormatSettings>
                <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
            </PivotViewFormatSettings>
        </PivotViewDataSourceSettings>
        <PivotViewGridSettings ColumnWidth=200></PivotViewGridSettings>
    </SfPivotView>

    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }

```

![output](images/column-width.png)

## Reorder

Allows end user to reorder a particular column header from one index to another index within the pivot table through drag-and-drop option. It can be enabled by setting the [`AllowReordering`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~AllowReordering.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings.html) class to **true**.

```csharp
    @using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="ProductDetails">
        <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
     <PivotViewFormatSettings>
                <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
            </PivotViewFormatSettings>
        </PivotViewDataSourceSettings>
            <PivotViewGridSettings AllowReordering="true"></PivotViewGridSettings>
    </SfPivotView>

    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }

```

![output](images/reorder.png)

## Column Resizing

Allows end user to resize the columns by clicking and dragging the right edge of the column header. While dragging, the width of the respective column will be resized immediately. To enable column resizing option, set the [`AllowResizing`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~AllowResizing.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings.html) class to **true**.

> By default, the column resizing option is enabled.
> In RTL mode, user can click and drag the left edge of the header cell to resize the column.

```csharp
    @using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="ProductDetails">
        <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
        </PivotViewDataSourceSettings>
            <PivotViewGridSettings AllowResizing="true"></PivotViewGridSettings>
    </SfPivotView>

    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }

```

![output](images/resize.png)

## Text Wrap

Allows end user to wrap the cell content to the next line when it exceeds the boundary of the cell width. To enable text wrap, set the [`AllowTextWrap`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~AllowTextWrap.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings.html) class to **true**.

```csharp
    @using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="ProductDetails">
        <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
             <PivotViewFormatSettings>
                <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
            </PivotViewFormatSettings>
        </PivotViewDataSourceSettings>
            <PivotViewGridSettings AllowTextWrap="true"></PivotViewGridSettings>
    </SfPivotView>

    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }

```

![output](images/textwrap.png)

## Grid Lines

Allows end user to display cell border for each cells using [`GridLines`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~GridLines.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings_properties.html) class.

Available mode of grid lines are:

| Modes | Actions |
|-------|---------|
| Both | Displays both the horizontal and vertical grid lines.|
| None | No grid lines are displayed.|
| Horizontal | Displays the horizontal grid lines only.|
| Vertical | Displays the vertical grid lines only.|
| Default | Displays grid lines based on the theme.|

> By default, pivot table renders grid lines in [**PivotGridLine.Both**](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~GridLines.html) mode.

```csharp
    @using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="ProductDetails">
    <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
             <PivotViewFormatSettings>
                <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
            </PivotViewFormatSettings>
        </PivotViewDataSourceSettings>
            <PivotViewGridSettings GridLines=PivotGridLine.Vertical></PivotViewGridSettings>
    </SfPivotView>

    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }

```

![output](images/gridlines.png)

## Selection

Selection provides an option to highlight a row or a column or a cell. It can be done through simple mouse down or arrow keys. To enable selection in the pivot table, set the [`AllowSelection`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~AllowSelection.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings.html) class to **true**.

The pivot table supports two types of selection that can be set using [`Type`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewSelectionSettings~Type.html) property in [`PivotViewSelectionSettings`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewSelectionSettings.html) class. The selection types are:

* [**PivotSelectionType.Single**](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotSelectionType.html): It is set by default, and it only allows selection of a single row or a column or a cell.
* [**PivotSelectionType.Multiple**](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotSelectionType.html): Allows you to select multiple rows or columns or cells.
To perform multi-selection, press and hold "CTRL" key and click the desired rows or cells. To select range of rows or cells, press and hold the "SHIFT" key and click the rows or columns or cells.

```csharp
    @using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="ProductDetails">
    <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
             <PivotViewFormatSettings>
                <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
            </PivotViewFormatSettings>
        </PivotViewDataSourceSettings>
            <PivotViewGridSettings AllowSelection="true">
                <PivotViewSelectionSettings Type=PivotSelectionType.Multiple></PivotViewSelectionSettings>
            </PivotViewGridSettings>
    </SfPivotView>

    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }

```

![output](images/selection.png)

### Selection Mode

The pivot table supports four types of selection mode that can be set using [`Mode`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewSelectionSettings~Mode.html) in [`PivotViewSelectionSettings`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewSelectionSettings.html) class. The selection modes are:

* [**SelectionMode.Row**](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.SelectionMode.html): It is set by default, and allows user to select only rows.
* [**SelectionMode.Column**](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.SelectionMode.html): Allows user to select only columns.
* [**SelectionMode.Cell**](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.SelectionMode.html): Allows user to select only cells.
* [**SelectionMode.Both**](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.SelectionMode.html): Allows user to select rows and columns at the same time.

```csharp
    @using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="ProductDetails">
    <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
             <PivotViewFormatSettings>
                <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
            </PivotViewFormatSettings>
        </PivotViewDataSourceSettings>
            <PivotViewGridSettings AllowSelection="true">
                <PivotViewSelectionSettings Mode=SelectionMode.Both Type=PivotSelectionType.Multiple></PivotViewSelectionSettings>
            </PivotViewGridSettings>
    </SfPivotView>

    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }

```

![output](images/selection2.png)

### Cell Selection Mode

The pivot table supports two types of cell selection mode that can be set using [`PivotCellSelectionMode`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewSelectionSettings~CellSelectionMode.html) in [`PivotViewSelectionSettings`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewSelectionSettings.html) class. The cell selection modes are:

* [**PivotCellSelectionMode.Flow**](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotCellSelectionMode.html): It is set by default. The range of cells are selected between the start index and end index that includes in-between cells of rows.
* [**PivotCellSelectionMode.Box**](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotCellSelectionMode.html): Range of cells are selected from the start and end column indexes that includes in-between cells of rows within the range.

```csharp
    @using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="ProductDetails">
    <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
            <PivotViewFormatSettings>
                <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
            </PivotViewFormatSettings>
        </PivotViewDataSourceSettings>
            <PivotViewGridSettings AllowSelection="true">
                <PivotViewSelectionSettings CellSelectionMode=PivotCellSelectionMode.Box Type=PivotSelectionType.Multiple Mode=SelectionMode.Cell></PivotViewSelectionSettings>
            </PivotViewGridSettings>
    </SfPivotView>

    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }

```

> Cell selection requires [`Mode`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewSelectionSettings~Mode.html) property in [`PivotViewSelectionSettings`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewSelectionSettings.html) class to be [**SelectionMode.Cell**](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.SelectionMode.html) or [**SelectionMode.Both**](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.SelectionMode.html), and [`Type`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewSelectionSettings~Type.html) property should be [**PivotSelectionType.Multiple**](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotSelectionType.html).

![output](images/cell-selection.png)

### Changing background color of the selected cell

The background-color of the selected cell can be changed using built-in CSS names. To do so, please refer to the code sample below, which shows that the selected cells are changed to a **green yellow** color.

```csharp
    @using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="ProductDetails">
    <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
        </PivotViewDataSourceSettings>
            <PivotViewGridSettings AllowSelection="true">
                <PivotViewSelectionSettings CellSelectionMode=PivotCellSelectionMode.Box Type=PivotSelectionType.Multiple Mode=SelectionMode.Cell></PivotViewSelectionSettings>
            </PivotViewGridSettings>
    </SfPivotView>
<style>

   .e-pivotview .e-cellselectionbackground,
   .e-pivotview .e-selectionbackground,
   .e-pivotview .e-grid .e-rowsheader.e-selectionbackground,
   .e-pivotview .e-grid .e-columnsheader.e-selectionbackground {
    background-color: greenYellow !important;
   }

</style>
    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }

```

![output](images/cell-selection-color.png)

### Event

The event `CellSelected` is triggered when cell selection gets completed. It provides selected cells information with its corresponding column and row headers. It has following parameters - [`SelectedCellsInfo`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotCellSelectedventArgs~SelectedCellsInfo.html), [`CurrentCell`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotCellSelectedEventArgs~CurrentCell.html) and [`Target`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotCellSelectedEventArgs~Target.html). This event allows user to view selected cells information and user can pass those selected cells information to any external component for data binding.

```csharp

@using Syncfusion.Blazor.PivotView

    <div>
        <div class="column-8">
            <SfPivotView Width="800" Height="340">
            <PivotViewDataSourceSettings @bind-DataSource="@data" ExpandAll="false" EnableSorting=true>
                <PivotViewColumns>
                    <PivotViewColumn Name="Year"></PivotViewColumn>
                    <PivotViewColumn Name="Quarter"></PivotViewColumn>
                </PivotViewColumns>
                <PivotViewRows>
                    <PivotViewRow Name="Country"></PivotViewRow>
                    <PivotViewRow Name="Products"></PivotViewRow>
                </PivotViewRows>
                <PivotViewValues>
                    <PivotViewValue Name="Sold" Caption="Units Sold"></PivotViewValue>
                    <PivotViewValue Name="Amount"></PivotViewValue>
                </PivotViewValues>
            </PivotViewDataSourceSettings>
            <PivotViewEvents TValue="ProductDetails" CellSelected="cellSelected"></PivotViewEvents>
            <PivotViewGridSettings AllowSelection="true">
                <PivotViewSelectionSettings Mode="SelectionMode.Cell" Type="PivotSelectionType.Multiple" CellSelectionMode="PivotCellSelectionMode.Box"></PivotViewSelectionSettings>
            </PivotViewGridSettings>
            </SfPivotView>
        </div>
        <div class="column-4">
        <h5>Event Trace:</h5> <br>
        <div style="height:300px; overflow:auto;">
            @if (SelectedCells != null)
            {
                @if (SelectedCells.SelectedCellsInfo != null)
                {
                    @foreach (var cell in SelectedCells.SelectedCellsInfo)
                    {
                        <p>
                            <b>ColumnHeader:</b> @cell.ColumnHeaders<br>
                            <b>RowHeader:</b> @cell.RowHeaders<br>
                            <b>Value:</b> @cell.Value<br>
                            <b>Measure:</b> @cell.Measure
                        </p>
                        <br>
                    }
                }
            }
        </div>
    </div>

</div>

    @code{
        public List<ProductDetails> data { get; set; }
        public PivotCellSelectedEventArgs SelectedCells;
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData();
        }
        public void cellSelected(PivotCellSelectedEventArgs args)
        {
            SelectedCells = args;
            //args.SelectedCellsInfo -> get selected cells information
        }
    }

```

![output](images/cellselected_event.png)

## Clip Mode

The clip mode provides options to display its overflow cell content in the pivot table. It can be configured using the [`ClipMode`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~ClipMode.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings.html) class. The pivot table supports three types of clip modes which are:

* [**PivotClipMode.Clip**](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotClipMode.html): Truncates the cell content when it overflows its area.
* [**PivotClipMode.Ellipsis**](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotClipMode.html): Displays ellipsis when the cell content overflows its area.
* [**PivotClipMode.EllipsisWithTooltip**](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotClipMode.html): Displays ellipsis when the cell content overflows its area, also it will display the tooltip while hover on ellipsis is applied.

>By default, [`ClipMode`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotViewGridSettings~ClipMode.html) value is set to [**PivotClipMode.Ellipsis**](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.PivotView.PivotClipMode.html).

```csharp
    @using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="ProductDetails">
        <PivotViewDataSourceSettings DataSource="@data">
            <PivotViewColumns>
                <PivotViewColumn Name="Year"></PivotViewColumn>
                <PivotViewColumn Name="Quarter"></PivotViewColumn>
            </PivotViewColumns>
            <PivotViewRows>
                <PivotViewRow Name="Country"></PivotViewRow>
                <PivotViewRow Name="Products"></PivotViewRow>
            </PivotViewRows>
            <PivotViewValues>
                <PivotViewValue Name="Amount" Caption="Sold Amount"></PivotViewValue>
            </PivotViewValues>
             <PivotViewFormatSettings>
                <PivotViewFormatSetting Name="Amount" Format="C"></PivotViewFormatSetting>
            </PivotViewFormatSettings>
        </PivotViewDataSourceSettings>
        <PivotViewGridSettings ClipMode=PivotClipMode.Clip></PivotViewGridSettings>
    </SfPivotView>

    @code{
        public List<ProductDetails> data { get; set; }
        protected override void OnInitialized()
        {
            this.data = ProductDetails.GetProductData().ToList();
           //Bind the data source collection here. Refer "Assigning sample data to the pivot table" section in getting started for more details.
        }
    }
```

![output](images/clipmode.png)


## Cell Template

You can customize the pivot table cell element by using the `CellTemplate` property in `PivotViewTemplates` class. The `CellTemplate` property accepts either an HTML string or the element's ID, which can be used to append additional HTML elements to showcase each cell with custom format.

In this demo, the revenue cost for each year is represented with trend icons.

>We need to specify the model type for datasource from which the context will be generated and accessed in the CellTemplate. Using the context we can define the conditions based on that templates will be appended to the cell element


```csharp
@using Syncfusion.Blazor.PivotView

    <SfPivotView TValue="TemplateData" ModelType="@Model" Height="300" Width="800">
            <PivotViewTemplates>
                <CellTemplate>
                    @{
                        var data = (context as ValueDetails);
                        if (data.Value > 175)
                        {
                            <span class="tempwrap sb-icon-profit pv-icons"></span>
                        }
                        else if (data.Value > 100)
                        {
                            <span class="tempwrap sb-icon-neutral pv-icons"></span>
                        }
                        else if (data.Value > 0)
                        {
                            <span class="tempwrap sb-icon-loss pv-icons"></span>
                        }

                    }
                </CellTemplate>
            </PivotViewTemplates>
            <PivotViewDataSourceSettings DataSource="@dataSource" ExpandAll=true EnableSorting=true>
                <PivotViewColumns>
                    <PivotViewColumn Name="EnerType" Caption="Energy Type"></PivotViewColumn>
                    <PivotViewColumn Name="EneSource" Caption="Energy Source"></PivotViewColumn>
                </PivotViewColumns>
                <PivotViewRows>
                    <PivotViewRow Name="Year" Caption="Year"></PivotViewRow>
                    <PivotViewRow Name="HalfYear" Caption="Half Year"></PivotViewRow>
                </PivotViewRows>
                <PivotViewValues>
                    <PivotViewValue Name="ProCost" Caption="Revenue Growth"></PivotViewValue>
                </PivotViewValues>
                <PivotViewFormatSettings>
                    <PivotViewFormatSetting Name="ProCost" Format="C0" UseGrouping=true></PivotViewFormatSetting>
                </PivotViewFormatSettings>
            </PivotViewDataSourceSettings>
            <PivotViewGridSettings ColumnWidth="140"></PivotViewGridSettings>
        </SfPivotView>

    @code{
        public class ValueDetails
        {
            public string FieldName { get; set; }
            public double Value { get; set; }
            public string Axis { get; set; }
            public string FormattedText { get; set; }
        }
        public ValueDetails Model = new ValueDetails();

        public List<TemplateData> dataSource { get; set; }

        protected override void OnInitialized()
        {
            this.dataSource = TemplateData.GetTemplateData();
        }
    }

```

![output](images/cell_template.png)