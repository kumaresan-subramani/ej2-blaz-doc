---
title: "Add or Remove Tab Items"
component: "Tabs"
description: "This example demonstrates how to add or remove a tab item in the Blazor Tab component."
---

# Add/Remove Tab Items

Tabs can be added dynamically by passing list of items and index value to the `AddTab` method. You can remove the tab items by passing the specified item through `RemoveTab` method. Tab items can also be removed by clicking the close icon which appears on the tab header on setting true to `ShowCloseButton` property.

In the following demo, you can add a tab item as first tab and remove the last tab item by clicking the **Add Tab** and **Remove Last Tab** buttons respectively.

```csharp
@using Syncfusion.Blazor.Navigations
@using Syncfusion.Blazor.Buttons

<SfButton OnClick="AddItemClick" Content="Add Tab"></SfButton>
<SfButton OnClick="RemoveItemClick" Content="Remove Last Tab"></SfButton>
<br/>
<SfTab @ref="Tab" ShowCloseButton="true">
    <TabItems>
        <TabItem Content="New York City comprises 5 boroughs sitting where the Hudson River meets the Atlantic Ocean. At its core is Manhattan, a densely populated borough that’s among the world’s major commercial, financial and cultural centers. Its iconic sites include skyscrapers such as the Empire State Building and sprawling Central Park. Broadway theater is staged in neon-lit Times Square.">
            <ChildContent>
                <TabHeader Text="New York"></TabHeader>
            </ChildContent>
        </TabItem>
        <TabItem Content="Los Angeles is a sprawling Southern California city and the center of the nation’s film and television industry. Near its iconic Hollywood sign, studios such as Paramount Pictures, Universal and Warner Brothers offer behind-the-scenes tours. On Hollywood Boulevard, TCL Chinese Theatre displays celebrities’ hand- and footprints, the Walk of Fame honors thousands of luminaries and vendors sell maps to stars’ homes.">
            <ChildContent>
                <TabHeader Text="Los Angeles"></TabHeader>
            </ChildContent>
        </TabItem>
        <TabItem Content="Chicago, on Lake Michigan in Illinois, is among the largest cities in the U.S. Famed for its bold architecture, it has a skyline punctuated by skyscrapers such as the iconic John Hancock Center, 1,451-ft. Willis Tower (formerly the Sears Tower) and the neo-Gothic Tribune Tower. The city is also renowned for its museums, including the Art Institute of Chicago with its noted Impressionist and Post-Impressionist works.">
            <ChildContent>
                <TabHeader Text="Chicago"></TabHeader>
            </ChildContent>
        </TabItem>
    </TabItems>
</SfTab>

@code{
    SfTab Tab;
    List<TabItem> TabData;
    public void AddItemClick()
    {
        TabData = new List<TabItem>()
        {
            new TabItem() { Header = new TabHeader() { Text = "Sydney" }, Content = "Sydney, capital of New South Wales and one of Australia largest cities, is best known for its harbourfront Sydney Opera House, with a distinctive sail-like design. Massive Darling Harbour and the smaller Circular Quay port are hubs of waterside life, with the arched Harbour Bridge and esteemed Royal Botanic Garden nearby. Sydney Tower’s outdoor platform, the Skywalk, offers 360-degree views of the city and suburbs." }
        };
        Tab.AddTab(TabData, 0);
    }
    public void RemoveItemClick()
    {
        Tab.RemoveTab(Tab.Items.Count - 1);
    }
}

<style>
    .e-content .e-item {
        font-size: 12px;
        margin: 10px;
        text-align: justify;
    }
</style>
```

Output be like the below.

![Add and remove tabs](../images/addRemoveTab.png)