---
title: "Getting Started"
component: "Gantt"
description: "Learn how to create an Essential JS 2 Gantt control and enable features like filtering, sorting, and Editing in ASP.NET Core."
---

# Getting Started with ASP.NET Core

> Starting with v16.2.0.x, if you reference Syncfusion assemblies from trial setup or from the NuGet feed, you also have to include a license key in your projects. Refer to this [link](https://help.syncfusion.com/common/essential-studio/licensing/license-key) to know about registering Syncfusion license key in your ASP.NET Core application to use our components.

## Prerequisites

To get started with the ASP.NET Core application, ensure that the following software are installed on the machine:

* Visual Studio 2017
* DotNet Core 2.0

## Setup ASP.NET Core application with Essential JS 2 for ASP.NET Core

The following steps to create ASP.NET Core Application.

**Step 1:** Create ASP.NET Core Web Application with default template project in Visual Studio 2017.

![Alt text](./images/default-template.png)

**Step 2:** Once your project created. We need to add Syncfusion EJ2 package into your application by using Nugget Package Manager.

Open the `nuGet` package manager.

![Alt text](./images/solution-explorer-core.png)

Install the **Syncfusion.EJ2** package to the application

![Alt text](./images/nuget-demo.png)

After Installation complete this will included in the project. You can refer it from the Project Assembly Reference.

> We need to install **NewtonSoft.JSON** as dependency since it **Syncfusion.EJ2** dependent to NewtonSoft.JSON package.

**Step 3:** Open the **Views/_ViewImports.cshtml** to import Syncfusion.EJ2 package.

```cs
@addTagHelper *, Syncfusion.EJ2
```

**Step 4:** Add client-side resource through [`CDN`](http://ej2.syncfusion.com/15.4.23/documentation/base/deployment.html?lang=typescript#cdn) or local [`package`](https://www.npmjs.com/package/@syncfusion/ej2) in the layout page **Views/Shared/_Layout.cshtml.**

```html
<head>
@* Syncfusion Essential JS 2 Styles *@
<link rel="stylesheet" href="https://cdn.syncfusion.com/ej2/material.css" />

@* Syncfusion Essential JS 2 Scripts *@
<script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js"></script>
</head>
```

**Step 5:** Adding Script Manager in layout page **Views/Shared/_Layout.cshtml.**

```cs

<ejs-scripts></ejs-scripts>

```

**Step 6:** Add the below code to your Index.cshtml view page which is present under Views/Home folder, to initialize the gantt.

{% aspTab template="gantt/getting-started/gantt", sourceFiles="gantt.cs" %}

{% endaspTab %}

## Binding Gantt with data

Bind data with the Gantt control by using the [`DataSource`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~DataSource.html) property. It accepts an array of JavaScript object or the DataManager instance.

{% aspTab template="gantt/getting-started/bindingData", sourceFiles="bindingData.cs" %}

{% endaspTab %}

## Mapping task fields

The data source fields that are required to render the tasks are mapped to the Gantt control using the [`TaskFields`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~TaskFields.html) property.

{% aspTab template="gantt/getting-started/mappingFields", sourceFiles="mappingFields.cs" %}

{% endaspTab %}

## Defining columns

Gantt has an option to define columns as an array. You can customize the Gantt columns using the following properties:

* `Field`: Maps the data source fields to the columns.
* `HeaderText`: Changes the title of columns.
* `TextAlign`: Changes the alignment of columns. By default, columns will be left aligned. To change the columns to right align, set `TextAlign` to right.
* `Format`: Formats the number and date values to standard or custom formats. Here, it is defined for the conversion of numeric values to currency.

{% aspTab template="gantt/getting-started/definingColumns", sourceFiles="definingColumns.cs" %}

{% endaspTab %}

## Enable editing

The editing feature enables you to edit the tasks in the Gantt control. It can be enabled by using the [`EditSettings.AllowEditing`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.GanttEditSettings~AllowEditing.html) and [`EditSettings.AllowTaskbarEditing`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.GanttEditSettings~AllowTaskbarEditing.html) properties.

The following editing options are available to update the tasks in Gantt:

* Cell
* Dialog
* Taskbar
* Connector line

### Cell editing

Modify the task details through cell editing by setting the edit mode to `Auto`.

{% aspTab template="gantt/getting-started/cellEditing", sourceFiles="cellEditing.cs" %}

{% endaspTab %}

`Note:` When the edit mode is set to `Auto`, you can change the cells to editable mode by double-clicking anywhere at the TreeGrid and edit the task details in the edit dialog by double-clicking anywhere at the chart.

### Dialog editing

Modify the task details through dialog by setting the edit mode to `Dialog`.

{% aspTab template="gantt/getting-started/dialogEditing", es5Template="dialogEditing" %}

{% endaspTab %}

`Note:` In dialog editing mode, the edit dialog will appear while performing double-click action in both TreeGrid and chart sides.

### Taskbar editing

Modify the task details through user interaction such as resizing and dragging the taskbar by enabling the [`AllowTaskbarEditing`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.GanttEditSettings~AllowTaskbarEditing.html) property.

{% aspTab template="gantt/getting-started/taskbarEditing", sourceFiles="taskbarEditing.cs" %}

{% endaspTab %}

### Dependency Editing

Modify the task dependencies using mouse interactions by enabling the [`AllowTaskbarEditing`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.GanttEditSettings~AllowTaskbarEditing.html) property along with mapping the task dependency data source field to the [`Dependency`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.GanttTaskFields~Dependency.html) property.

{% aspTab template="gantt/getting-started/dependencyEditing", sourceFiles="dependencyEditing.cs" %}

{% endaspTab %}

## Enable filtering

The filtering feature enables you to view the reduced amount of records based on filter criteria. Gantt provides the menu filtering support for each column. It can be enabled by setting the [`AllowFiltering`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~AllowFiltering.html) property to `true`. Filtering feature can also be customized using the [`FilterSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~FilterSettings.html) property.

{% aspTab template="gantt/getting-started/filtering", sourceFiles="filtering.cs" %}

{% endaspTab %}

## Enable sorting

The sorting feature enables you to order the records. It can be enabled by setting the [`AllowSorting`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~AllowSorting.html) property to `true`.The sorting feature can be customized using the [`SortSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~SortSettings.html) property.

{% aspTab template="gantt/getting-started/sorting", sourceFiles="sorting.cs" %}

{% endaspTab %}

## Enabling predecessors or task relationships

Predecessor or task dependency in the Gantt control is used to depict the relationship between the tasks.

* Start to Start (SS): You cannot start a task until the dependent task starts.
* Start to Finish (SF): You cannot finish a task until the dependent task finishes.
* Finish to Start (FS): You cannot start a task until the dependent task completes.
* Finish to Finish (FF): You cannot finish a task until the dependent task completes.
You can show the relationship in tasks by using the [`Dependency`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.GanttTaskFields~Dependency.html) property as shown in the following code example.

{% aspTab template="gantt/predecessor/enableDependency", sourceFiles="enableDependency.cs" %}

{% endaspTab %}

## Assigning resources

You can display and assign the resource for each task in the Gantt control.
Create a collection of list object, which contains ID and name of the resource and assign it to the [`Resources`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~Resources.html) property. Map the resource ID and name with [`ResourceIDMapping`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~ResourceIDMapping.html) and [`ResourceNameMapping`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~ResourceNameMapping.html) properties, respectively.

{% aspTab template="gantt/resources/assignResource", sourceFiles="assignResource.cs" %}

{% endaspTab %}

Output be like the below.

![Alt text](./images/gantt-output.png)