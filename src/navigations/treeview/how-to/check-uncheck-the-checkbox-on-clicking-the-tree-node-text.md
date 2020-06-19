# Check/uncheck the checkbox on clicking the tree node text

You can check and uncheck the checkboxes of tree view by clicking the tree node using the `NodeClicked` event of TreeView.

```csharp
@using Syncfusion.Blazor.Navigations
<SfTreeView TValue="MusicAlbum" @ref="tree" ShowCheckBox="true" AutoCheck="true">
    <TreeViewEvents TValue="MusicAlbum" OnKeyPress="TreeNodeClick" NodeClicked="NodeClick" NodeChecking="BeforeCheck" NodeExpanding="ExpandCollapse" NodeCollapsing="ExpandCollapse"></TreeViewEvents>
    <TreeViewFieldsSettings TValue="MusicAlbum" Id="Id" DataSource="@Albums" Text="Name" ParentID="ParentId" HasChildren="HasChild" Expanded="Expanded" IsChecked="IsChecked"></TreeViewFieldsSettings>
</SfTreeView>

@code{

    SfTreeView<MusicAlbum> tree;
    public bool ExpandIconClick { get; set; } = false;
    public bool CheckBoxClick { get; set; } = false;
    List<MusicAlbum> NodeDetails;
    public class MusicAlbum
    {
        public int Id { get; set; }
        public int? ParentId { get; set; }
        public string Name { get; set; }
        public bool Expanded { get; set; }
        public bool? IsChecked { get; set; }
        public bool HasChild { get; set; }

    }
    List<MusicAlbum> Albums = new List<MusicAlbum>();
    public MusicAlbum ModelType = new MusicAlbum();

    async void TreeNodeClick(NodeKeyPressEventArgs args)
    {
        string Key = args.Event.Key;
        if (Key == "Enter" && !ExpandIconClick)
        {
            NodeDetails = await this.tree.GetTreeData(args.Node);
            var Element = new[] { args.Node };
            bool check = NodeDetails[0].IsChecked ?? false;
            if (check)
            {
                this.tree.UncheckAll(Element);
            }
            else
            {
                this.tree.CheckAll(Element);
            }
        }
        ExpandIconClick = false;
    }
    async void NodeClick(NodeClickEventArgs args)
    {
        if (!ExpandIconClick && !CheckBoxClick)
        {
            List<MusicAlbum> NodeDetails = await this.tree.GetTreeData(args.Node);
            var Element = new[] { args.Node };
            if (NodeDetails[0].IsChecked == true)
            {
                this.tree.UncheckAll(Element);
            }
            else
            {
                this.tree.CheckAll(Element);
            }

        }
        ExpandIconClick = false;
        CheckBoxClick = false;
    }

    void ExpandCollapse(NodeExpandEventArgs args)
    {
        ExpandIconClick = true;
    }

    void BeforeCheck(NodeCheckEventArgs args)
    {
        if (args.IsInteracted)
        {
            CheckBoxClick = true;
        }
    }
    protected override void OnInitialized()
    {
        base.OnInitialized();
        Albums.Add(new MusicAlbum
        {
            Id = 1,
            Name = "Discover Music",
            HasChild = true,
        });
        Albums.Add(new MusicAlbum
        {
            Id = 2,
            ParentId = 1,
            Name = "Hot Singles"
        });
        Albums.Add(new MusicAlbum
        {
            Id = 3,
            ParentId = 1,
            Name = "Rising Artists"
        });
        Albums.Add(new MusicAlbum
        {
            Id = 4,
            ParentId = 1,
            Name = "Live Music"
        });
        Albums.Add(new MusicAlbum
        {
            Id = 14,
            HasChild = true,
            Name = "MP3 Albums",
            Expanded = true,
            IsChecked = true
        });
        Albums.Add(new MusicAlbum
        {
            Id = 15,
            ParentId = 14,
            Name = "Rock"
        });
        Albums.Add(new MusicAlbum
        {
            Id = 16,
            Name = "Gospel",
            ParentId = 14,
        });
        Albums.Add(new MusicAlbum
        {
            Id = 17,
            ParentId = 14,
            Name = "Latin Music"
        });
        Albums.Add(new MusicAlbum
        {
            Id = 18,
            ParentId = 14,
            Name = "Jazz"
        });
    }
}
```

Output be like the below.

![TreeView Sample](../images/checkbox.png)