---
title: "Globalization and Localization in Blazor Scheduler"
component: "Scheduler"
description: "This section explains how the Scheduler adapts to various languages and culture by parsing and formatting the date or number appropriately."
---

# Globalization and Localization

The Scheduler integrates different date-time formats and cultures, which allows it to function globally, thus meeting the diverse needs of different regions.

You can adapt the Scheduler to various languages by parsing and formatting the date or number `Internationalization`, adding culture specific customization and translation to the text `Localization`.

## Blazor Server Side

The static local texts in the Scheduler component can be changed to other culture by referring the Resource file. You can refer more details about localization [here](../../common/localization/). By default, Scheduler is set to follow the English culture ('en-US'). The following steps explains how to render the Scheduler in German culture ('de-DE').

* Open the **Startup.cs** file and add the below configuration in the **ConfigureServices** function as follows.

```csharp
using Syncfusion.Blazor;
using System.Globalization;
using Microsoft.AspNetCore.Localization;

namespace BlazorApplication
{
    public class Startup
    {
        ....
        ....
        public void ConfigureServices(IServiceCollection services)
        {
            ....
            ....
            services.AddSyncfusionBlazor();
            services.AddLocalization(options => options.ResourcesPath = "Resources");
            services.Configure<RequestLocalizationOptions>(options =>
            {
                // define the list of cultures your app will support
                var supportedCultures = new List<CultureInfo>()
                {
                    new CultureInfo("de_DE")
                };
                // set the default culture
                options.DefaultRequestCulture = new RequestCulture("de-DE");
                options.SupportedCultures = supportedCultures;
                options.SupportedUICultures = supportedCultures;
                options.RequestCultureProviders = new List<IRequestCultureProvider>() {
                 new QueryStringRequestCultureProvider() // Here, You can also use other localization provider
                };
            });
            services.AddSingleton(typeof(ISyncfusionStringLocalizer), typeof(SampleLocalizer));
        }
    }
}
```

> Add [`UseRequestLocalization()`](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/localization?view=aspnetcore-3.0#localization-middleware) middle-ware in Configure method in **Startup.cs** file to get browser Culture Information.

* Then, write a **class** by inheriting **ISyncfusionStringLocalizer** interface and override the `Manager` property to get the resource file details from the application end.

```csharp
using Syncfusion.Blazor;

namespace SchedulerBlazorLocalization
{
     public class SampleLocalizer : ISyncfusionStringLocalizer
    {
        public string Get(string key)
        {
            return this.Manager.GetString(key);
        }

        public System.Resources.ResourceManager Manager
        {
            get
            {
                return SchedulerBlazorLocalization.Resources.SyncfusionBlazorLocale.ResourceManager;
            }
        }
    }
}
```

* Add **.resx** file to [`Resource`](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/localization?view=aspnetcore-3.0#resource-files) folder and that file contains the key value pair of locale content in the following format.

```csharp
<Component_Name>_<Feature_Name>_<Locale_Key>
```

* Finally, specify the culture for Scheduler using `Locale` property as in the following code example.

```csharp
@using Syncfusion.Blazor.Schedule

<SfSchedule TValue="AppointmentData" Locale="de-DE" Height="650px" SelectedDate="@(new DateTime(2020, 2, 14))">
    <ScheduleEventSettings DataSource="@DataSource"></ScheduleEventSettings>
</SfSchedule>

@code{
    List<AppointmentData> DataSource = new List<AppointmentData>
{
        new AppointmentData { Id = 1, Subject = "Paris", StartTime = new DateTime(2020, 2, 13, 10, 0, 0) , EndTime = new DateTime(2020, 2, 13, 12, 0, 0) },
        new AppointmentData { Id = 2, Subject = "Germany", StartTime = new DateTime(2020, 2, 15, 10, 0, 0) , EndTime = new DateTime(2020, 2, 15, 12, 0, 0) }
    };
    public class AppointmentData
    {
        public int Id { get; set; }
        public string Subject { get; set; }
        public DateTime StartTime { get; set; }
        public DateTime EndTime { get; set; }
    }
}
```

## Blazor Web Assembly

The following steps explain how to render the Scheduler in German culture ('de-DE') in Blazor Web Assembly application.

* You can download the locale definition of Blazor components from this [link](https://github.com/syncfusion/ej2-locale). Once downloaded, copy the required local definition file into `wwwroot\sf-locale` folder. Use `LoadLocaleData` method to load the locale definitions.

* Set the culture by using the `SetCulture` method.

```csharp
@using Syncfusion.Blazor
@using Syncfusion.Blazor.Schedule
@using Microsoft.JSInterop
@inject HttpClient Http;

<SfSchedule TValue="AppointmentData" Height="650px">
</SfSchedule>
@code {
    [Inject]
    IJSRuntime JsRuntime { get; set; }
    protected override async Task OnAfterRenderAsync(bool firstRender)
    {
        if (firstRender)
        {
            var Locale = await Http.GetJsonAsync<object>("sf-locale/locale.json");
            this.JsRuntime.Sf().LoadLocaleData(Locale).SetCulture("de");
        }
    }
    public class AppointmentData
    {
        public int Id { get; set; }
        public string Subject { get; set; }
        public string Location { get; set; }
        public DateTime StartTime { get; set; }
        public DateTime EndTime { get; set; }
        public string Description { get; set; }
        public bool IsAllDay { get; set; }
        public string RecurrenceRule { get; set; }
        public string RecurrenceException { get; set; }
        public Nullable<int> RecurrenceID { get; set; }
    }
}
```

## Setting date format

Scheduler can be used with all valid date formats and by default it follows the universal date format "MM/dd/yyyy". If the `DateFormat` property is not specified particularly, then it will work based on the locale that is assigned to the Scheduler. As the default locale applied on Scheduler is "en-US", this makes it to follow the "MM/dd/yyyy" pattern.

```csharp
@using Syncfusion.Blazor.Schedule

<SfSchedule TValue="AppointmentData" Height="650px" DateFormat="yyyy/MM/dd">
</SfSchedule>

@code{
    public class AppointmentData
    {
        public int Id { get; set; }
        public string Subject { get; set; }
        public string Location { get; set; }
        public DateTime StartTime { get; set; }
        public DateTime EndTime { get; set; }
        public string Description { get; set; }
        public bool IsAllDay { get; set; }
        public string RecurrenceRule { get; set; }
        public string RecurrenceException { get; set; }
        public Nullable<int> RecurrenceID { get; set; }
    }
}
```

## Time mode

The time mode of the Scheduler can be either 12 or 24 hours format which is completely based on the `Locale` set to the Scheduler. Since the default `Locale` value of the Scheduler is en-US, the time mode will be set to 12 hours format automatically.

## Displaying Scheduler in RTL mode

The Scheduler layout and its behavior can be changed as per the common RTL (Right to Left) conventions by setting `EnableRtl` to `true`. By doing so, the Scheduler will display its usual layout from right to left. It's default value is `false`.

```csharp
@using Syncfusion.Blazor
@using Syncfusion.Blazor.Schedule

<SfSchedule TValue="AppointmentData" Height="650px" EnableRtl="true">
</SfSchedule>

@code {
    public class AppointmentData
    {
        public int Id { get; set; }
        public string Subject { get; set; }
        public string Location { get; set; }
        public DateTime StartTime { get; set; }
        public DateTime EndTime { get; set; }
        public string Description { get; set; }
        public bool IsAllDay { get; set; }
        public string RecurrenceRule { get; set; }
        public string RecurrenceException { get; set; }
        public Nullable<int> RecurrenceID { get; set; }
    }
}
```

## See Also

* [How to change first day of the week in the Scheduler](./working-hours/#setting-start-day-of-the-week)