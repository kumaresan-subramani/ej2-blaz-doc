---
title: "Context menu"
component: "Scheduler"
description: "This section explains how to integrate the context menu manually to a Scheduler and use it with required options."
---

# Context Menu

You can display context menu on work cells and appointments of Scheduler by making use of the `ContextMenu` control manually from the application end. In the following code example, context menu control is being added from sample end and set its target as `Scheduler` and the target element is get by using `GetTargetElement` public method in Blazor.

On Scheduler cells, you can display the menu items such as `New Event`, `New Recurring Event` and `Today` option. For appointments, you can display its related options such as `Edit Event` and `Delete Event`. The default event window can be opened for appointment creation and editing using the `OpenEditor` method of Scheduler.

The deletion of appointments can be done by using the `DeleteEvent` public method. Also, the `SelectedDate` property can be used to navigate between different dates.

> You can also display custom menu options on Scheduler cells and appointments. Context menu will open on tap-hold in responsive mode.

```csharp

@using Syncfusion.Blazor.Schedule
@using Syncfusion.Blazor.Navigations

<SfSchedule TValue="AppointmentData" @ref="ScheduleRef" Height="650px" @bind-SelectedDate="@SelectedDate">
    <ScheduleEventSettings DataSource="@DataSource"></ScheduleEventSettings>
</SfSchedule>

<SfContextMenu @ref="ContextMenuObj" CssClass="schedule-context-menu" Target=".e-schedule" Items="@MenuItems">
    <ContextMenuEvents OnOpen="OnOpen" ItemSelected="OnItemSelected"></ContextMenuEvents>
</SfContextMenu>

@code{
    private DateTime SelectedDate = new DateTime(2020, 1, 8);
    SfSchedule<AppointmentData> ScheduleRef;
    SfContextMenu ContextMenuObj;
    public AppointmentData EventData { get; set; }
    public CellClickEventArgs TargetCell { get; set; }
    public List<MenuItem> MenuItems = new List<MenuItem>
    {
        new MenuItem { Text = "New Event", IconCss="e-icons new", Id="Add" },
        new MenuItem { Text = "New Recurring Event", IconCss="e-icons recurrence", Id="AddRecurrence" },
        new MenuItem { Text = "Today", IconCss="e-icons today", Id="Today" },
        new MenuItem { Text = "Edit Event", IconCss="e-icons edit", Id="Save" },
        new MenuItem { Text = "Edit Event", IconCss="e-icons edit", Id="EditRecurrenceEvent", Items= EditRecurrenceEvent  },
        new MenuItem { Text = "Delete Event", IconCss="e-icons delete", Id="Delete" },
        new MenuItem { Text = "Delete Event", IconCss="e-icons delete", Id="DeleteRecurrenceEvent" , Items=DeleteRecurrenceEvent }
    };
    public static List<MenuItem> EditRecurrenceEvent = new List<MenuItem>
    {
        new MenuItem { Text = "Edit Occurrence", Id = "EditOccurrence"},
        new MenuItem { Text = "Edit Series", Id = "EditSeries" }
    };
    public static List<MenuItem> DeleteRecurrenceEvent = new List<MenuItem>
    {
        new MenuItem { Text = "Delete Occurrence", Id = "DeleteOccurrence" },
        new MenuItem { Text = "Delete Series", Id = "DeleteSeries"}
    };
    public async Task OnOpen(BeforeOpenCloseMenuEventArgs args)
    {
        string Selector = ".e-appointment,.e-work-cells," +
        ".e-vertical-view .e-date-header-wrap .e-all-day-cells,.e-vertical-view .e-date-header-wrap .e-header-cells";
        var Element = await ScheduleRef.GetTargetElement(Selector , args.Left, args.Top);
        if (Element != null)
        {
            TargetCell = await ScheduleRef.GetCellDetails(Element);
            if (TargetCell == null)
            {
                EventData = await ScheduleRef.GetEventDetails(Element);
                if (EventData.RecurrenceRule != null)
                {
                    await ContextMenuObj.ShowItems(new string[] { "EditRecurrenceEvent", "DeleteRecurrenceEvent" }, true);
                    await ContextMenuObj.HideItems(new string[] { "Add", "AddRecurrence", "Today", "Save", "Delete" }, true);
                }
                else
                {
                    await ContextMenuObj.ShowItems(new string[] { "Save", "Delete" }, true);
                    await ContextMenuObj.HideItems(new string[] { "Add", "AddRecurrence", "Today", "EditRecurrenceEvent", "DeleteRecurrenceEvent" }, true);
                }
            }
            else
            {
                await ContextMenuObj.ShowItems(new string[] { "Add", "AddRecurrence", "Today" }, true);
                await ContextMenuObj.HideItems(new string[] { "Save", "Delete", "EditRecurrenceEvent", "DeleteRecurrenceEvent" }, true);
            }
        }
        else if (args.ParentItem == null)
        {
            args.Cancel = true;
        }
    }
    public async Task OnItemSelected(MenuEventArgs args)
    {
        var SelectedMenuItem = args.Item.Id;
        var ActiveCellsData = TargetCell;
        var SelectedCells = await ScheduleRef.GetSelectedElements();
        if (SelectedCells.Count > 0)
        {
            ActiveCellsData = await ScheduleRef.GetCellDetails(SelectedCells);
        }
        switch (SelectedMenuItem)
        {
            case "Today":
                SelectedDate = DateTime.Now;
                break;

            case "Add":
                await ScheduleRef.OpenEditor(ActiveCellsData, CurrentAction.Add);
                break;

            case "AddRecurrence":
                await ScheduleRef.OpenEditor(ActiveCellsData, CurrentAction.Add, null, 1);
                break;

            case "Save":
                await ScheduleRef.OpenEditor(EventData, CurrentAction.Save);
                break;

            case "EditOccurrence":
                await ScheduleRef.OpenEditor(EventData, CurrentAction.EditOccurrence);
                break;

            case "EditSeries":
                List<AppointmentData> Events = await ScheduleRef.GetEvents();
                EventData = (AppointmentData)Events.Where(data => data.Id == EventData.RecurrenceID).FirstOrDefault();
                await ScheduleRef.OpenEditor(EventData, CurrentAction.EditSeries);
                break;

            case "Delete":
                await ScheduleRef.DeleteEvent(EventData);
                break;

            case "DeleteOccurrence":
                await ScheduleRef.DeleteEvent(EventData, CurrentAction.DeleteOccurrence);
                break;

            case "DeleteSeries":
                await ScheduleRef.DeleteEvent(EventData, CurrentAction.DeleteSeries);
                break;
        }
    }
    public List<AppointmentData> DataSource = new List<AppointmentData>
    {
        new AppointmentData { Id = 1, Subject = "Meeting", StartTime = new DateTime(2020, 1, 8, 11, 30, 0) , EndTime = new DateTime(2020, 1, 8, 12, 30, 0) },
        new AppointmentData { Id = 2, Subject = "Conference", StartTime = new DateTime(2020, 1, 10, 11, 30, 0) , EndTime = new DateTime(2020, 1, 10, 12, 30, 0) },
        new AppointmentData { Id = 3, Subject = "Seminar", StartTime = new DateTime(2020, 1, 6, 9, 30, 0) , EndTime = new DateTime(2020, 1, 6, 11, 0, 0),
        RecurrenceRule = "FREQ=DAILY;INTERVAL=1;COUNT=5" }
    };
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
