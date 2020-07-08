---
title: "Getting Started"
component: "Grid"
description: "Learn how to create an Essential JS 2 DataGrid control and enable features like paging, filtering, sorting, and grouping in ASP.NET Core."
---

# Getting Started with ASP.NET Core

> Starting with v16.2.0.x, if you reference Syncfusion assemblies from trial setup or from the NuGet feed, you also have to include a license key in your projects. Please refer to this [link](https://help.syncfusion.com/common/essential-studio/licensing/license-key) to know about registering Syncfusion license key in your ASP.NET Core application to use our components.

## Prerequisites

To get started with ASP.NET Core application, need to ensure the following software to be installed on the machine.
* Visual Studio 2017
* DotNet Core 2.0

## Create ASP.NET Core application

Create ASP.NET Core Web Application with default template project in Visual Studio 2017.

![Alt text](./images/default-template.png)

## Adding Syncfusion package

Using Nuget Package Manager we need to add **Syncfusion.EJ2.AspNet.Core** package into your application.

Open the `NuGet` package manager.

![Alt text](./images/solution-explorer-core.png)

Install the **Syncfusion.EJ2.AspNet.Core** package to the application

![Alt text](./images/nuget-package-demo.png)

After Installation completed the Syncfusion DLL's will be included in the project.

> We need to install **NewtonSoft.JSON** as dependency since **Syncfusion.EJ2.AspNet.Core** dependent to NewtonSoft.JSON package.

Open the **Views/_ViewImports.cshtml** to import Syncfusion.EJ2.AspNet.Core package.

```cs
@addTagHelper *, Syncfusion.EJ2
```

## Adding Scripts and CSS reference

We can add client side resource through [`CDN`](http://ej2.syncfusion.com/15.4.23/documentation/base/deployment.html?lang=typescript#cdn) or NPM [`package`](https://www.npmjs.com/package/@syncfusion/ej2) in the layout page **Views/Shared/_Layout.cshtml.**

CDN Link:

```html
<head>
@* Syncfusion Essential JS 2 Styles *@
<link rel="stylesheet" href="https://cdn.syncfusion.com/ej2/material.css" />

@* Syncfusion Essential JS 2 Scripts *@
<script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js"></script>
</head>
```

NPM Package:

Install `@syncfusion/ej2` package using below command.

> npm install @syncfusion/ej2

Now the required scripts and CSS files are available in the **../node_modules/@syncfusion/ej2/dist** and CSS **../node_modules/@syncfusion/ej2/styles** package folders respectively. Copy those script and themes files from the `node_modules` into the `wwwroot` folder of the application.

```html
<head>
@* Syncfusion Essential JS 2 Styles *@
<link href="~/styles/material.css" rel="stylesheet" />

@* Syncfusion Essential JS 2 Scripts *@
<script src="~/scripts/ej2.min.js"></script>
</head>
```

## Adding ScriptManager in layout page

Add `ScriptManager` to the bottom of the `_Layout.cshtml` page. The ScriptManager used to place our control initialization script in the page.

```cs
<body>
    @RenderBody()
    @RenderSection("Scripts", required: false)
<ejs-scripts></ejs-scripts>
</body>
```

## Add Grid Component

To initialize the Grid component add the below code to your `Index.cshtml` view page which is present under `Views/Home` folder.

{% aspTab template="grid/getting-start-core/grid" %}

{% endaspTab %}

## Defining Row Data

To bind data for the Grid component, you can assign a IEnumerable object to the [`dataSource`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~DataSource.html) property. The list data source can also be provided as an instance of the `DataManager`.

{% aspTab template="grid/getting-start-core/databinding", sourceFiles="grid.cs,orderDetails.cs" %}

{% endaspTab %}

## Defining Columns

The columns are automatically generated when `columns` declaration is empty or undefined while initializing the grid.

The Grid has an option to define columns using [`e-grid-columns`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Columns.html) tag helper. In `e-grid-column` tag helper we have properties to customize columns.

Let’s check the properties used here:

* We have added [`field`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Field.html) to map with a property name an array of JavaScript objects.
* We have added [`headerText`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~HeaderText.html) to change the title of columns.
* We have used [`textAlign`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~TextAlign.html) to change the alignment of columns.
By default, columns will be left aligned. To change columns to right align, we need to define `textAlign` as `Right`.
* Also, we have used another useful property, [format](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Format.html).
Using this, we can format number and date values to standard or custom formats.
Here, we have defined it for the conversion of numeric values to currency.

{% aspTab template="grid/getting-start-core/gridcolumns", sourceFiles="grid.cs,orderDetails.cs" %}

{% endaspTab %}

## Enable Paging

The paging feature enables users to view the grid record in a paged view. It can be enabled by setting the  [`allowPaging`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowPaging.html) property to true. Pager can be customized using [`e-grid-pagesettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~PageSettings.html) tag helper.

{% aspTab template="grid/getting-start-core/page", sourceFiles="page.cs,orderDetails.cs" %}

{% endaspTab %}

## Enable Sorting

The sorting feature enables you to order the records. It can be enabled by setting the  [`allowSorting`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowSorting.html) property as true. Sorting feature can be customized using [`e-grid-sortsettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~SortSettings.html) tag helper.

{% aspTab template="grid/getting-start-core/sorting", sourceFiles="sorting.cs,orderDetails.cs" %}

{% endaspTab %}

## Enable Filtering

The filtering feature enables you to view reduced amount of records based on filter criteria. It can be enabled by setting the [`allowFiltering`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowFiltering.html) property as true. Filtering feature can be customized using [`e-grid-filtersettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~FilterSettings.html) tag helper.

{% aspTab template="grid/getting-start-core/filtering", sourceFiles="filtering.cs,orderDetails.cs" %}

{% endaspTab %}

## Enable Grouping

The grouping feature enables users to view the grid record in a grouped view. It can be enabled by setting the
 [`allowGrouping`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowGrouping.html) property to true.
 Grouping feature can be customized using the [`e-grid-groupsettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~GroupSettings.html) tag helper.

{% aspTab template="grid/getting-start-core/grouping", sourceFiles="grouping.cs,orderDetails.cs" %}

{% endaspTab %}

Output be like the below.

![Alt text](./images/grid-sample.png)