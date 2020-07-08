---
title: "Merge the duplicate cells in specific column with export"
component: "Grid"
description: "Learn how to merge the duplicate cells in the specific column and it is export."
---

# Merge the duplicate cells for the particular column in Grid view and its exporting

You can merge the duplicate cells (based on the value) for the particular column of Grid by using ['dataBound'](../../api/grid/#databound) event.  At the same time, you can also merge the duplicate cells for particular column while exporting by using the [`excelQueryCellInfo`](../../api/grid/#excelquerycellinfo) event for Excel/CSV  and [`pdfQueryCellInfo`](../../api/grid/#pdfquerycellinfo) event for PDF exporting.

In the below demo,  the duplicate cells are merged for the `OrderID` column  in Grid view and its exporting.

{% tab template="grid/custom-cellmerge-export", sourceFiles="index.ts,datasource.ts", es5Template="custom-cellmerge" %}

```typescript
import { Grid, ExcelQueryCellInfoEventArgs, ExcelCell, PdfQueryCellInfoEventArgs, ExcelExport } from '@syncfusion/ej2-grids';
import {PdfExport, PdfGridCell,Toolbar } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(ExcelExport, PdfExport,Toolbar );
// global variable declaration for excel export
let gridcells: ExcelCell;
let ValOfOrderID:Number =null;
let i=1;
// global variable declaration for pdf Export
let pdfGridcell: PdfGridCell;
let ValOfOrderID_PDF :Number = null;
let pdfCellindex:Number =1;
let grid: Grid = new Grid(
    {
        dataSource: data,
        allowExcelExport:true,
        allowPdfExport:true,
        toolbar:["ExcelExport","PdfExport"],
        toolbarClick: toolbarClick,
        dataBound: onDataBound,
        excelQueryCellInfo:excelQueryCellInfo,
        excelExportComplete: excelExportComplete,
        pdfQueryCellInfo: pdfQueryCellInfo,
        pdfExportComplete: pdfExportComplete,
        allowPaging:true,
        pageSettings: { pageSize:5 },
        columns: [
            { field: 'OrderID', headerText: 'Order ID', width: 120, textAlign: 'Right' },  
            { field: 'CustomerID', headerText: 'Customer ID', width: 130 },
            {field: "City", headerText:"ShipCity",width:120}
        ],
        height: 260,
    });
    grid.appendTo('#Grid');
    function toolbarClick(args){
        if (args.item.text === 'PDF Export') {
            this.pdfExport();
        }
        if (args.item.text === 'Excel Export') {
            this.excelExport();
        }
     }
    function onDataBound(args: any) {
    let previousData: string = null;
    let stRowIndex: number = null;
    let endRowIndex: number = null;
    let grid = this;
    let rows = this.getRows();
    let data = this.getCurrentViewRecords();

    for (let i = 0, len = rows.length; i < len; i++) {
        if (!previousData) {
            previousData = data[i]['OrderID'];
            stRowIndex = parseInt(rows[i].getAttribute("aria-rowindex"));
        }
        else if (previousData === data[i]['OrderID']) {
            rows[i].children[0].classList.add('e-hide');
        }
        else if (previousData && previousData !== data[i]['OrderID']) {
            if (grid.getRows().length > 0 && grid.getRows().length > stRowIndex) {
                endRowIndex = parseInt(rows[i].getAttribute("aria-rowindex"), 10);
                let targetCell: Element[] =
                    [].slice.call(grid.getRows()[stRowIndex].querySelectorAll('.e-rowcell')).filter((cell: Element) =>
                        parseInt(cell.getAttribute('aria-colindex'), 10) === parseInt(rows[i].children[0].getAttribute('aria-colindex')));
                (targetCell[0] as any).setAttribute("rowSpan", endRowIndex - stRowIndex);
                previousData = data[i]['OrderID'];
                stRowIndex = parseInt(rows[i].getAttribute("aria-rowindex"), 10);
            }
        }
        if (rows[i].children[0].classList.contains("e-hide") || i < len) {
            endRowIndex = parseInt(rows[i].getAttribute("aria-rowindex"), 10);
            if (endRowIndex > 0) {
                let targetCell: Element[] = [].slice.call(grid.getRows()[stRowIndex].querySelectorAll('.e-rowcell')).filter((cell: Element) =>
                    parseInt(cell.getAttribute('aria-colindex'), 10) === parseInt(rows[i].children[0].getAttribute('aria-colindex')));
                (targetCell[0] as any).setAttribute("rowSpan", endRowIndex + 1);
            }
        }
    }
}

function excelQueryCellInfo(args: ExcelQueryCellInfoEventArgs) {

    if (!ValOfOrderID && args.column.field == "OrderID") {
        ValOfOrderID = args.data["OrderID"];
        gridcells = (args.cell as ExcelCell);
    }
    else if (ValOfOrderID && args.column.field == "OrderID" && ValOfOrderID == args.data["OrderID"]) {
        i++;
    } else if (ValOfOrderID !== args.data["OrderID"] && args.column.field == "OrderID") {
        (gridcells as ExcelCell).rowSpan = i;
        ValOfOrderID = args.data["OrderID"];
        gridcells = (args.cell as ExcelCell);
        i = 1;
    }
}
// Reset the excel export global variable values
function excelExportComplete(args: ExcelExportCompleteArgs) {
    ValOfOrderID = null;
    gridcells = null;
    i=1;
  }
function pdfQueryCellInfo(args: PdfQueryCellInfoEventArgs) {
    if(!ValOfOrderID_PDF && args.column.field == "OrderID"){
            ValOfOrderID_PDF =  args.data["OrderID"];
            pdfGridcell = (args.cell as PdfGridCell);
        }
        else if(ValOfOrderID_PDF && args.column.field == "OrderID" &&  ValOfOrderID_PDF ==args.data["OrderID"]){
          (pdfCellindex as any)++;
        } else if(ValOfOrderID_PDF !== args.data["OrderID"] && args.column.field == "OrderID") {
          (pdfGridcell as PdfGridCell).rowSpan = pdfCellindex as any;
          ValOfOrderID_PDF = args.data["OrderID"];
          pdfGridcell=(args.cell as PdfGridCell);
          pdfCellindex = 1 ;
        }
      }
       // Reset the pdf export global variable values
       function pdfExportComplete(args: PdfExportCompleteArgs){
        ValOfOrderID_PDF=null;
        pdfGridcell=null;
        pdfCellindex =1;
      }
```

{% endtab %}
