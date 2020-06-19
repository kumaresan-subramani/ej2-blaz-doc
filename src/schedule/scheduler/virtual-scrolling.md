---
title: "Virtual scrolling in Blazor Scheduler"
component: "Scheduler"
description: "This section demonstrtes how to dynamically load the resources and events as you scroll through the scheduler"
---

# Virtual scrolling

To achieve better performance in the Scheduler when loading a large number of resources and events, we have added virtual scrolling support in the timeline views to load a large set of resources and events instantly as you scroll. You can dynamically load large number of resources and events in timeline view of the Scheduler by setting `true` to the `AllowVirtualScrolling` property within the timeline view-specific settings. The virtual loading of events is possible in Agenda view, by setting `AllowVirtualScrolling` property to `true` within the agenda view specific settings.

> The Schedule has the following limitations while enabling virtual scrolling
>    1. User couldn't configure the templates "resource template, cell template, and month header template"
>    2. The navigation to a specific resource using "scrollToResource".

```csharp
@using Syncfusion.Blazor.Schedule

<SfSchedule TValue="EventData" Width="100%" Height="650px" SelectedDate="@(new DateTime(2020, 4, 1))">
    <ScheduleGroup EnableCompactView="false" Resources="@GroupData"></ScheduleGroup>
    <ScheduleResources>
        <ScheduleResource TValue="ResourceData" DataSource="@ResourceDatasource" Field="ResourceId" Title="Resource" Name="Resources" TextField="Text" IdField="Id" ColorField="Color" AllowMultiple="true"></ScheduleResource>
    </ScheduleResources>
    <ScheduleEventSettings DataSource="@AppointmentData"></ScheduleEventSettings>
    <ScheduleViews>
        <ScheduleView Option="View.TimelineMonth" AllowVirtualScrolling="true"></ScheduleView>
    </ScheduleViews>
</SfSchedule>

@code{
    static EventData data = new EventData();
    public static List<ResourceData> ResourceDatasource = GenerateResourceData();
    public static List<EventData> AppointmentData = GenerateStaticEvents();
    public string[] GroupData { get; set; } = { "Resources" };
    static public List<ResourceData> GenerateResourceData()
    {
        List<ResourceData> resources = new List<ResourceData>(300);
        var colors = new string[] { "#ff8787", "#9775fa", "#748ffc", "#3bc9db", "#69db7c",
            "#fdd835", "#748ffc", "#9775fa", "#df5286", "#7fa900",
            "#fec200", "#5978ee", "#00bdae", "#ea80fc"};
        for (int a = 1; a <= 300; a++)
        {
            int index = a % colors.Length;
            index = index == 0 ? (colors.Length / a) : index;
            resources.Add(new ResourceData
            {
                Id = a,
                Text = "Resource " + a,
                Color = colors[index]
            });
        }
        return resources;
    }
    public static List<EventData> GenerateStaticEvents()
    {
        DateTime date = new DateTime(2020, 4, 1);
        List<EventData> data = new List<EventData>(3600);
        var id = 1;
        for (var i = 0; i < 300; i++)
        {
            Random random = new Random();
            List<int> listNumbers = new List<int>();
            int[] randomCollection = new int[24];
            int number;
            int max = 30;
            for (int a = 0; a < 12; a++)
            {
                do
                {
                    number = random.Next(max);
                } while (listNumbers.Contains(number));
                listNumbers.Add(number);
                var startDate = date.AddDays(number);
                startDate = startDate.AddMilliseconds((((number % 10) * 10) * (1000 * 60)));
                var endDate = startDate.AddMilliseconds(((1440 + 30) * (1000 * 60)));
                data.Add(new EventData
                {
                    Id = id,
                    Subject = "Event #" + id,
                    StartTime = startDate,
                    EndTime = endDate,
                    IsAllDay = (id % 10 == 0) ? false : true,
                    ResourceId = i + 1
                });
                id++;
            }
        }
        return data;
    }
    public class EventData
    {
        public int Id { get; set; }
        public string Subject { get; set; }
        public DateTime StartTime { get; set; }
        public DateTime EndTime { get; set; }
        public bool IsAllDay { get; set; }
        public int ResourceId { get; set; }
    }

    public class ResourceData
    {
        public int Id { get; set; }
        public string Text { get; set; }
        public string Color { get; set; }
    }
}
```

> For now, the virtual loading of resources and events is available only for timeline views. In the future, we plan to port the same virtual loading on all other applicable Scheduler views.
