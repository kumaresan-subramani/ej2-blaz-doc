---
title: "Excel Export"
component: "Gantt"
description: "Learn how to export Gantt data to Excel and CSV documents in the Essential JS 2 Gantt component."
---

# Excel Export

Gantt supports client-side exporting, which allows you to export its data to the Excel and CSV formats. Use the [`excelExport`](../api/gantt/#excelexport) and [`csvExport`](../api/gantt/#csvexport) methods for exporting. To enable Excel export in the Gantt, set the [`allowExcelExport`](../api/gantt/#allowexcelexport) to true.

To export data to Excel and CSV, inject the `ExcelExport` module in Gantt.

{% tab template="gantt/excel-export", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { GanttComponent, Inject, Toolbar, ToolbarItem, ExcelExport, Selection } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    private ganttInstance: any;
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
  };
  public toolbarOptions: ToolbarItem[] = ['ExcelExport', 'CsvExport'];
  public toolbarClick(args: ClickEventArgs): void {
       if (args.item.id === 'GanttExport_excelexport') {
           this.ganttInstance.excelExport();
        } else if (args.item.id === 'GanttExport_csvexport') {
            this.ganttInstance.csvExport();
        }
    };
    render() {
        return <GanttComponent id='GanttExport' dataSource={data} taskFields={this.taskFields} toolbar={this.toolbarOptions}
        toolbarClick={this.toolbarClick.bind(this)} allowExcelExport={true} height='400px' ref={gantt => this.ganttInstance = gantt}>
            <Inject services={[Toolbar, ExcelExport, Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Multiple Gantt exporting

In Gantt, the Excel export provides support to export multiple Gantt data in new sheet or same sheet.

### Same sheet

The Excel export provides support to export multiple Gantt data in the same sheet. To export in same sheet, define `multipleExport.type` as `AppendToSheet` in `ExcelExportProperties`. You can also provide blank rows between exported multiple Gantt data. These blank rows count can be defined using `multipleExport.blankRows`.

{% tab template="gantt/excel-export", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { GanttComponent, Inject, Toolbar, ToolbarItem, ExcelExport, ExcelExportProperties, Selection } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    private firstGantt: any;
    private secondGantt: any;
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
  };
  public toolbarOptions: ToolbarItem[] = ['ExcelExport'];
  public toolbarClick(args: ClickEventArgs): void {
       if (args.item.id === 'FirstGantt_excelexport') {
           const appendExcelExportProperties: ExcelExportProperties = {
               multipleExport: {type: 'AppendToSheet',blankRows: 2}
            };
            const firstGanttExport: Promise<any> = this.firstGantt.excelExport(appendExcelExportProperties,true);
            firstGanttExport.then((fData: any) => {
                this.secondGantt.excelExport(appendExcelExportProperties,false,fData);
            });
        }
    };
    render() {
        return (
            <div>
            <p><b>First Gantt:</b></p>
            <GanttComponent id='FirstGantt' dataSource={[data[0]]} taskFields={this.taskFields} toolbar={this.toolbarOptions}
        toolbarClick={this.toolbarClick.bind(this)} allowExcelExport={true} height='280px' ref={gantt => this.firstGantt = gantt} treeColumnIndex={1} projectStartDate='03/31/2019' projectEndDate='04/14/2019'>
            <Inject services={[Toolbar, ExcelExport, Selection]} />
        </GanttComponent>
        <p><b>Second Gantt:</b></p>
            <GanttComponent id='SecondGantt' dataSource={[data[1]]} taskFields={this.taskFields} allowExcelExport={true} height='250px' ref={gantt => this.secondGantt = gantt} treeColumnIndex={1}>
            <Inject services={[ExcelExport, Selection]} />
        </GanttComponent>
            </div>
        );
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

>By default, `multipleExport.blankRows` value is 5.

### New sheet

The Excel exporting provides support to export multiple Gantt in new sheet. To export in new sheet, define `multipleExport.type` as `NewSheet` in `ExcelExportProperties`.

{% tab template="gantt/excel-export", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { GanttComponent, Inject, Toolbar, ToolbarItem, ExcelExport, ExcelExportProperties, Selection } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    private firstGantt: any;
    private secondGantt: any;
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
  };
  public toolbarOptions: ToolbarItem[] = ['ExcelExport'];
  public toolbarClick(args: ClickEventArgs): void {
       if (args.item.id === 'FirstGantt_excelexport') {
           const appendExcelExportProperties: ExcelExportProperties = {
                        multipleExport: {type: 'NewSheet'}
                    };
                    const firstGanttExport: Promise<any> = this.firstGantt.excelExport(appendExcelExportProperties,true);
                    firstGanttExport.then((fData: any) => {
                        this.secondGantt.excelExport(appendExcelExportProperties,false,fData);
                    });
            }
    };
    render() {
        return (
            <div>
            <p><b>First Gantt:</b></p>
            <GanttComponent id='FirstGantt' dataSource={[data[0]]} taskFields={this.taskFields} toolbar={this.toolbarOptions}
        toolbarClick={this.toolbarClick.bind(this)} allowExcelExport={true} height='280px' ref={gantt => this.firstGantt = gantt} treeColumnIndex={1} projectStartDate='03/31/2019' projectEndDate='04/14/2019'>
            <Inject services={[Toolbar, ExcelExport, Selection]} />
        </GanttComponent>
        <p><b>Second Gantt:</b></p>
            <GanttComponent id='SecondGantt' dataSource={[data[1]]} taskFields={this.taskFields} allowExcelExport={true} height='250px' ref={gantt => this.secondGantt = gantt} treeColumnIndex={1}>
            <Inject services={[ExcelExport, Selection]} />
        </GanttComponent>
            </div>
        );
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

## Customize the Excel export

Gantt Excel export allows the users to customize the exported document based on requirement.

### Export hidden columns

In Gantt, the Excel export provides an option to export hidden columns by defining `includeHiddenColumn` as `true`.

{% tab template="gantt/excel-export", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { GanttComponent, Inject, Toolbar, ToolbarItem, ExcelExport, ColumnsDirective,ColumnDirective, Selection } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    private ganttInstance: any;
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
  };
  public toolbarOptions: ToolbarItem[] = ['ExcelExport', 'CsvExport'];
  public toolbarClick(args: ClickEventArgs): void {
       if (args.item.id === 'GanttExport_excelexport') {
           const excelExportProperties: ExcelExportProperties = {
                includeHiddenColumn: true
            };
           this.ganttInstance.excelExport(excelExportProperties);
        } else if (args.item.id === 'GanttExport_csvexport') {
            const excelExportProperties: ExcelExportProperties = {
                includeHiddenColumn: true
            };
            this.ganttInstance.csvExport(excelExportProperties);
        }
    };
    render() {
        return <GanttComponent id='GanttExport' dataSource={data} taskFields={this.taskFields} toolbar={this.toolbarOptions}
        toolbarClick={this.toolbarClick.bind(this)} allowExcelExport={true} height='400px' ref={gantt => this.ganttInstance = gantt} treeColumnIndex={1}>
            <ColumnsDirective>
                <ColumnDirective field='TaskID' headerText='Task ID' textAlign='Left' width='100' ></ColumnDirective>
                <ColumnDirective field='TaskName' headerText='Task Name' width='150'></ColumnDirective>
                <ColumnDirective field='StartDate' headerText='StartDate' width='150' visible={false}></ColumnDirective>
                <ColumnDirective field='Duration' headerText='Duration' width='150' ></ColumnDirective>
                <ColumnDirective field='Progress' headerText='Progress' width='150'></ColumnDirective>
            </ColumnsDirective>
            <Inject services={[Toolbar, ExcelExport, Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Show or hide columns on exported Excel

In Gantt, while exporting, you can show a hidden column or hide a visible column using the [`toolbarClick`](../api/gantt/#toolbarclick) and [`excelExportComplete`](../api/gantt/#excelexportcomplete) events.

In the `toolbarClick` event, using the `args.item.id` property, you can show or hide columns by setting the `column.visible` property to `true` or `false` respectively.

Similarly, in the excelExportComplete event, you can revert the columns visibility back to the previous state.

{% tab template="gantt/excel-export", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { GanttComponent, Inject, Toolbar, ToolbarItem, ExcelExport, ColumnsDirective,ColumnDirective, Selection } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    private ganttInstance: any;
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
  };
  public toolbarOptions: ToolbarItem[] = ['ExcelExport', 'CsvExport'];
  public toolbarClick(args: ClickEventArgs): void {
       if (args.item.id === 'GanttExport_excelexport') {
           this.ganttInstance.treeGrid.grid.columns[0].visible = true;
           this.ganttInstance.treeGrid.grid.columns[3].visible = false;
           this.ganttInstance.excelExport();
        } else if (args.item.id === 'GanttExport_csvexport') {
            this.ganttInstance.treeGrid.grid.columns[0].visible = true;
            this.ganttInstance.treeGrid.grid.columns[3].visible = false;
            this.ganttInstance.csvExport();
        }
    };
    public excelExportComplete(): void {
      this.ganttInstance.treeGrid.grid.columns[0].visible = false;
      this.ganttInstance.treeGrid.grid.columns[3].visible = true;
  }
    render() {
        return <GanttComponent id='GanttExport' dataSource={data} taskFields={this.taskFields} toolbar={this.toolbarOptions}
        toolbarClick={this.toolbarClick.bind(this)} excelExportComplete={this.excelExportComplete.bind(this)} allowExcelExport={true} height='400px' ref={gantt => this.ganttInstance = gantt} treeColumnIndex={1}>
            <ColumnsDirective>
                <ColumnDirective field='TaskID' headerText='Task ID' textAlign='Left' width='100' ></ColumnDirective>
                <ColumnDirective field='TaskName' headerText='Task Name' width='150'></ColumnDirective>
                <ColumnDirective field='StartDate' headerText='StartDate' width='150' visible={false}></ColumnDirective>
                <ColumnDirective field='Duration' headerText='Duration' width='150' ></ColumnDirective>
                <ColumnDirective field='Progress' headerText='Progress' width='150'></ColumnDirective>
            </ColumnsDirective>
            <Inject services={[Toolbar, ExcelExport, Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Cell formatting during export

In Gantt, you can customize the TreeGrid cells in the exported document using the [`excelQueryCellInfo`](../api/gantt/#excelquerycellinfo) event. In this event, you can format the TreeGrid cells of exported Excel and CSV documents based on the required condition.

In the following sample, the background color has been customized for `TaskID` column in the exported Excel using the `args.style` and `backColor` properties.

{% tab template="gantt/excel-export", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { GanttComponent, Inject, Toolbar, ToolbarItem, ExcelExport, Selection, ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-react-gantt';
import { ganttData } from './datasource';
class App extends React.Component<{}, {}>{
    private ganttInstance: any;
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
  };
  public toolbarOptions: ToolbarItem[] = ['ExcelExport'];
  public toolbarClick(args: ClickEventArgs): void {
       if (args.item.id === 'GanttExport_excelexport') {
           this.ganttInstance.excelExport();
        }
    };
    public excelQueryCellInfo(args)  {
        if(args.column.field == 'Progress') {
            if(args.value > 80) {
                args.style = { backColor: '#A569BD' };
            }
            else if(args.value < 20) {
                args.style = { backColor: '#F08080' };
            }
        }
    };
    public queryTaskbarInfo(args)  {
        if (args.data.Progress > 80) {
            args.progressBarBgColor = "#6C3483";
            args.taskbarBgColor = args.taskbarBorderColor = "#A569BD";
        } else if (args.data.Progress < 20) {
            args.progressBarBgColor = "#CD5C5C";
            args.taskbarBgColor = args.taskbarBorderColor = "#F08080";
        }
    };
    public queryCellInfo(args)  {
        if(args.column.field == 'Progress') {
            if(args.data.Progress > 80) {
                args.cell.style.backgroundColor  = '#A569BD';
            }
            else if(args.data.Progress < 20) {
                args.cell.style.backgroundColor  = '#F08080';
            }
        }
    };
    public labelSettings: any = {
        taskLabel: '${Progress}%'
    };
    public splitterSettings: any = {
        columnIndex: 3
    };
    render() {
        return <GanttComponent id='GanttExport' dataSource={ganttData} taskFields={this.taskFields} toolbar={this.toolbarOptions}
        toolbarClick={this.toolbarClick.bind(this)} queryCellInfo={this.queryCellInfo} excelQueryCellInfo={this.excelQueryCellInfo} queryTaskbarInfo={this.queryTaskbarInfo} allowExcelExport={true} height='400px' ref={gantt => this.ganttInstance = gantt} treeColumnIndex={1} labelSettings={this.labelSettings} splitterSettings={this.splitterSettings} >
            <ColumnsDirective>
                <ColumnDirective field='TaskID' headerText= 'Task ID' textAlign= 'Left' width= '100' visible= {false}></ColumnDirective>
                <ColumnDirective field='TaskName' headerText= 'Task Name' width= '150'></ColumnDirective>
                <ColumnDirective field='Progress' headerText= 'Progress' width= '150'></ColumnDirective>
                <ColumnDirective field='StartDate' headerText= 'Start Date' width= '150'></ColumnDirective>
                <ColumnDirective field='Duration' headerText= 'Duration' width= '150'></ColumnDirective>
            </ColumnsDirective>
            <Inject services={[Toolbar, ExcelExport, Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### Theme

The Excel export also provides an option to include custom theme for exported Excel document.

To apply theme in exported Excel, define the `theme` in `ExcelExportProperties`.

{% tab template="gantt/excel-export", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { GanttComponent, Inject, Toolbar, ToolbarItem, ExcelExport, Selection } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    private ganttInstance: any;
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
  };
  public toolbarOptions: ToolbarItem[] = ['ExcelExport'];
  public toolbarClick(args: ClickEventArgs): void {
       if (args.item.id === 'GanttExport_excelexport') {
           const excelExportProperties: ExcelExportProperties = {
                theme:
                        {
                            header: { fontName: 'Segoe UI', fontColor: '#666666' },
                            record: { fontName: 'Segoe UI', fontColor: '#666666' }
                        }
            };
           this.ganttInstance.excelExport(excelExportProperties);
        }
    };
    render() {
        return <GanttComponent id='GanttExport' dataSource={data} taskFields={this.taskFields} toolbar={this.toolbarOptions}
        toolbarClick={this.toolbarClick.bind(this)} allowExcelExport={true} height='400px' ref={gantt => this.ganttInstance = gantt} treeColumnIndex={1}>
            <Inject services={[Toolbar, ExcelExport, Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> By default, material theme is applied to the exported Excel document.

### Add header and footer

The Excel export also allows users to include header and footer contents to the exported Excel document.

{% tab template="gantt/excel-export", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { GanttComponent, Inject, Toolbar, ToolbarItem, ExcelExport, Selection } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    private ganttInstance: any;
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
  };
  public toolbarOptions: ToolbarItem[] = ['ExcelExport'];
  public toolbarClick(args: ClickEventArgs): void {
       if (args.item.id === 'GanttExport_excelexport') {
           const excelExportProperties: ExcelExportProperties = {
                header: {
                            headerRows: 7,
                            rows: [
                                { cells: [{ colSpan: 4, value: "Northwind Traders", style: { fontColor: '#C67878', fontSize: 20, hAlign: 'Center', bold: true, } }] },
                                { cells: [{ colSpan: 4, value: "2501 Aerial Center Parkway", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                                { cells: [{ colSpan: 4, value: "Suite 200 Morrisville, NC 27560 USA", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                                { cells: [{ colSpan: 4, value: "Tel +1 888.936.8638 Fax +1 919.573.0306", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                                { cells: [{ colSpan: 4, hyperlink: { target: 'https://www.northwind.com/', displayText: 'www.northwind.com' }, style: { hAlign: 'Center' } }] },
                                { cells: [{ colSpan: 4, hyperlink: { target: 'mailto:support@northwind.com' }, style: { hAlign: 'Center' } }] },
                            ]
                        },
                        footer: {
                            footerRows: 4,
                            rows: [
                                { cells: [{ colSpan: 4, value: "Thank you for your business!", style: { hAlign: 'Center', bold: true } }] },
                                { cells: [{ colSpan: 4, value: "!Visit Again!", style: { hAlign: 'Center', bold: true } }] }
                            ]
                        },
            };
           this.ganttInstance.excelExport(excelExportProperties);
        }
    };
    render() {
        return <GanttComponent id='GanttExport' dataSource={data} taskFields={this.taskFields} toolbar={this.toolbarOptions}
        toolbarClick={this.toolbarClick.bind(this)} allowExcelExport={true} height='400px' ref={gantt => this.ganttInstance = gantt} treeColumnIndex={1}>
            <Inject services={[Toolbar, ExcelExport, Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

### File name for exported document

You can set the required file name for the exported document by defining the `fileName` property in `ExcelExportProperties`.

{% tab template="gantt/excel-export", compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { GanttComponent, Inject, Toolbar, ToolbarItem, ExcelExport, Selection } from '@syncfusion/ej2-react-gantt';
import { data } from './datasource';
class App extends React.Component<{}, {}>{
    private ganttInstance: any;
    public taskFields: any = {
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        duration: 'Duration',
        progress: 'Progress',
        child: 'subtasks'
  };
  public toolbarOptions: ToolbarItem[] = ['ExcelExport', 'CsvExport'];
  public toolbarClick(args: ClickEventArgs): void {
       if (args.item.id === 'GanttExport_excelexport') {
           const excelExportProperties: ExcelExportProperties = {
                fileName:"Gantt.xlsx"
            };
           this.ganttInstance.excelExport(excelExportProperties);
        } else if (args.item.id === 'GanttExport_csvexport'){
            const excelExportProperties: ExcelExportProperties = {
                fileName:"Gantt.csv"
            };
           this.ganttInstance.csvExport(excelExportProperties);
        }
    };
    render() {
        return <GanttComponent id='GanttExport' dataSource={data} taskFields={this.taskFields} toolbar={this.toolbarOptions}
        toolbarClick={this.toolbarClick.bind(this)} allowExcelExport={true} height='400px' ref={gantt => this.ganttInstance = gantt} treeColumnIndex={1}>
            <Inject services={[Toolbar, ExcelExport, Selection]} />
        </GanttComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}
