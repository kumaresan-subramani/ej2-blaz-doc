---
title: "Getting Started"
component: "Grid"
description: "Learn how to create an Essential JS 2 DataGrid control and enable features like paging, filtering, sorting, and grouping in ASP.NET MVC."
---

# Getting Started with ASP.NET MVC

> Starting with v16.2.0.x, if you reference Syncfusion assemblies from trial setup or from the NuGet feed, you also have to include a license key in your projects. Please refer to this [link](https://help.syncfusion.com/common/essential-studio/licensing/license-key) to know about registering Syncfusion license key in your ASP.NET Core application to use our components.

## Prerequisites

To get start with ASP.NET MVC application, need to ensure the following software to be installed on the machine.

1. .Net Framework 4.5 and above.
2. ASP.NET MVC 4 or ASP.NET MVC 5
3. Visual Studio

## Create ASP.NET MVC application

Create ASP.NET MVC Application with default template project in Visual Studio 2017.

![Default Template](./images/default-template-mvc.png)

## Adding Syncfusion package

Once your project created, we need to add Syncfusion EJ2 MVC package into your application by using **NuGet Package Manager**.

Open the **NuGet** package manager.

![Solution Explorer](./images/solution-explorer-mvc.png)

Install the **Syncfusion.EJ2.MVC4** package to the application.

![Nuget Demo](./images/nuget-demo-mvc.png)

After Installation completed the Syncfusion DLL's will be included in the project.

> You need to install **NewtonSoft.JSON** as dependency since **Syncfusion.EJ2.MVC** dependent to NewtonSoft.JSON package.

Add **Syncfusion.EJ2** namespace reference in **Web.config** under **Views** folder.

```cs
<namespaces>
    <add namespace="Syncfusion.EJ2"/>
</namespaces>

```

## Adding Scripts and CSS reference

You can add client side resource through **Nuget** package manager or [`CDN`](http://ej2.syncfusion.com/15.4.23/documentation/base/deployment.html?lang=typescript#cdn) in the layout page **Views/Shared/_Layout.cshtml.**

Nuget Package Manager:

Install the **Syncfusion.EJ2.Javascript** package to the application.

![Nuget Demo](./images/script-nuget.jpg)

After Installation completed the script and CSS will be included in the project under the **Scripts** and **Content** folder.

```html
<head>
@* Syncfusion Essential JS 2 Styles *@
<link href="~/Content/ej2/material.css" rel="stylesheet" />

@* Syncfusion Essential JS 2 Scripts *@
<script src="~/Scripts/ej2/ej2.min.js"></script>
</head>
```

> **Syncfusion.EJ2.Javascript** includes typescript declaration files. If your application is not configured to compile typescript then exception may occur. To resolve this please refer [`here`](./how-to/avoid-typescript-compilation/).

CDN Link:

```html
<head>
@* Syncfusion Essential JS 2 Styles *@
<link rel="stylesheet" href="https://cdn.syncfusion.com/ej2/material.css" />

@* Syncfusion Essential JS 2 Scripts *@
<script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js"></script>
</head>
```

## Adding ScriptManager in layout page

Add **ScriptManager** to the bottom of the **_Layout.cshtml** page. The ScriptManager used to place our control initialization script in the page.

```cs
@Html.EJS().ScriptManager()
```

## Add Grid Component

To initialize the Grid component add the below code to your **Index.cshtml** view page which is present under **Views/Home** folder.

{% aspTab template="grid/getting-start-mvc/initialize" %}

{% endaspTab %}

## Defining Row Data

To bind data for the Grid component, you can assign a IEnumerable object to the [`DataSource`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~DataSource.html) property. The list data source can also be provided as an instance of the **DataManager**.

{% aspTab template="grid/getting-start-mvc/databinding", sourceFiles="grid.cs,orderDetails.cs" %}

{% endaspTab %}

## Defining Columns

The columns are automatically generated when columns declaration is empty or undefined while initializing the grid.

The Grid has an option to define columns using [`Columns`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn.html) property.

Let’s check the properties used here:

* The [`Field`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Field.html) property is to map with a property name an array of JavaScript objects.
* The [`HeaderText`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~HeaderText.html) property is to change the title of columns.
* The [`TextAlign`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~TextAlign.html) property is to change the alignment of columns.
By default, columns will be left aligned. To change columns to right align, you need to define **textAlign** as **Right**.
* Using [Format](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Format.html) property
you can format number and date values to standard or custom formats.
Here, you have defined it for the conversion of numeric values to currency.

{% aspTab template="grid/getting-start-mvc/columns", sourceFiles="columns.cs,orderDetails.cs" %}

{% endaspTab %}

## Enable Paging

The paging feature enables users to view the grid record in a paged view. It can be enabled by setting the  [`AllowPaging`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowPaging.html) property to true. Pager can be customized using the [`PageSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridPageSettings.html) property.

{% aspTab template="grid/getting-start-mvc/page", sourceFiles="page.cs,orderDetails.cs" %}

{% endaspTab %}

## Enable Sorting

The sorting feature enables you to order the records. It can be enabled by setting the  [`AllowSorting`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowSorting.html) property as true. Sorting feature can be customized using the [`SortSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSortSettings.html) property.

{% aspTab template="grid/getting-start-mvc/sorting", sourceFiles="sorting.cs,orderDetails.cs" %}

{% endaspTab %}

## Enable Filtering

The filtering feature enables you to view reduced amount of records based on filter criteria. It can be enabled by setting the [`AllowFiltering`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowFiltering.html) property as true. Filtering feature can be customized using the [`FilterSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridFilterSettings.html) property.

{% aspTab template="grid/getting-start-mvc/filtering", sourceFiles="filtering.cs,orderDetails.cs" %}

{% endaspTab %}

## Enable Grouping

The grouping feature enables users to view the grid record in a grouped view. It can be enabled by setting the
 [`AllowGrouping`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowGrouping.html) property to true.
 Grouping feature can be customized using the [`GroupSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridGroupSettings.html) property.

{% aspTab template="grid/getting-start-mvc/grouping", sourceFiles="grouping.cs,orderDetails.cs" %}

{% endaspTab %}

Output be like the below.

![Alt text](./images/grid-sample.png)