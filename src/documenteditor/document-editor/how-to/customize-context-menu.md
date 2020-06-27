---
title: "How to customize context menu"
component: "DocumentEditor"
description: "Learn how to customize context menu with document editor in real time scenarios like create simple word processor."
---

# Context menu customization

## How to customize context menu in document editor

Document Editor allows you to add custom option in context menu. It can be achieved by using the [`addCustomMenu()`](../../api/document-editor/contextMenu/#addcustommenu) method and custom action is defined using the [`customContextMenuSelect`](../../api/document-editor/customContentMenuEventArgs/)

### Add Custom Option

The following code shows how to add custom option in context menu.

```typescript
let documentEditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false
});
documentEditor.enableAllModules();
documentEditor.appendTo('#DocumentEditor');
// Creating custom menu items
let menuItems: MenuItemModel[] = [
    {
        text: 'Search In Google',
        id: 'search_in_google',
        iconCss: 'e-icons e-de-ctnr-find'
    }];
// Adding custom options
documentEditor.contextMenu.addCustomMenu(menuItems, false);
// To handle contextmenu select event
documentEditor.customContextMenuSelect = (args: CustomContentMenuEventArgs): void => {
    let item: string = args.id;
    let id: string = documentEditor.element.id;
    switch (item) {
        case id + 'search_in_google':
            let searchContent: string = documentEditor.selection.text;
            if (!documentEditor.selection.isEmpty && /\S/.test(searchContent)) {
                window.open('http://google.com/search?q=' + searchContent);
            }
            break;
    }
};
```

### Customize custom option in context menu

Document Editor allows you to customize the added custom option and also to hide/show default context menu.

#### Hide default context menu items

The following code shows how to hide default context menu and add custom option in context menu.

```typescript
let documentEditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false
});
documentEditor.enableAllModules();
documentEditor.appendTo('#DocumentEditor');
// Creating custom menu items
let menuItems: MenuItemModel[] = [
    {
        text: 'Search In Google',
        id: 'search_in_google',
        iconCss: 'e-icons e-de-ctnr-find'
    }];
// Adding custom options
documentEditor.contextMenu.addCustomMenu(menuItems, true);
```

#### Customize added context menu items

The following code shows how to hide/show added custom option in context menu using the [`customContextMenuBeforeOpen`](../../api/document-editor/beforeOpenCloseCustomContentMenuEventArgs/).

```typescript
let documentEditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false
});
documentEditor.enableAllModules();
documentEditor.appendTo('#DocumentEditor');
// Creating custom menu items
let menuItems: MenuItemModel[] = [
    {
        text: 'Search In Google',
        id: 'search_in_google',
        iconCss: 'e-icons e-de-ctnr-find'
    }];
// Adding custom options
documentEditor.contextMenu.addCustomMenu(menuItems, false);
// To show/hide custom menu item
documentEditor.customContextMenuBeforeOpen = (args: BeforeOpenCloseCustomContentMenuEventArgs): void => {
    let search: HTMLElement = document.getElementById(args.ids[0]);
    search.style.display = 'none';
    let searchContent: string = documentEditor.selection.text;
    if ((!documentEditor.selection.isEmpty) && (/\S/.test(searchContent))) {
        search.style.display = 'block';
    }
};
// To handle contextmenu select event
documentEditor.customContextMenuSelect = (args: CustomContentMenuEventArgs): void => {
    let item: string = args.id;
    let id: string = documentEditor.element.id;
    switch (item) {
        case id + 'search_in_google':
            let searchContent: string = documentEditor.selection.text;
            if (!documentEditor.selection.isEmpty && /\S/.test(searchContent)) {
                window.open('http://google.com/search?q=' + searchContent);
            }
            break;
    }
};
```

The following is the output of custom context menu with customization.

{% tab template="document-editor/customize-context-menu", es5Template="customize-context-menu", sourceFiles="index.ts,index.html" %}

```typescript
import { DocumentEditor, Editor,Selection,OptionsPane, Search, ContextMenu, EditorHistory,ImageResizer, ListDialog,TableDialog, HyperlinkDialog, ParagraphDialog, FontDialog, PageSetupDialog, BookmarkDialog, StyleDialog, TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, TableOfContentsDialog } from '@syncfusion/ej2-documenteditor';
import { CheckBox, ChangeEventArgs } from '@syncfusion/ej2-buttons';

DocumentEditor.Inject(Editor,Selection,OptionsPane, Search, ContextMenu, EditorHistory,ImageResizer, ListDialog,TableDialog, HyperlinkDialog, ParagraphDialog, FontDialog, PageSetupDialog, BookmarkDialog, StyleDialog, TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, TableOfContentsDialog);

let defaultCheckBoxObj: CheckBox = new CheckBox({ label: 'Hide Default Context Menu', change: contextmenuHelper });
defaultCheckBoxObj.appendTo('#default-context-menu');

let positionCheckBoxObj: CheckBox = new CheckBox({ label: 'Add Custom option at bottom', change: contextmenuHelper });
positionCheckBoxObj.appendTo('#position-context-menu');

let documentEditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false
});
documentEditor.enableAllModules();
documentEditor.appendTo('#DocumentEditor');
// Creating custom menu items
let menuItems: MenuItemModel[] = [
    {
        text: 'Search In Google',
        id: 'search_in_google',
        iconCss: 'e-icons e-de-ctnr-find'
    }];
// Adding custom options
documentEditor.contextMenu.addCustomMenu(menuItems, false);
// To show/hide custom menu item
documentEditor.customContextMenuBeforeOpen = (args: BeforeOpenCloseCustomContentMenuEventArgs): void => {
    let search: HTMLElement = document.getElementById(args.ids[0]);
    search.style.display = 'none';
    let searchContent: string = documentEditor.selection.text;
    if ((!documentEditor.selection.isEmpty) && (/\S/.test(searchContent))) {
        search.style.display = 'block';
    }
};
// To handle contextmenu select event
documentEditor.customContextMenuSelect = (args: CustomContentMenuEventArgs): void => {
    let item: string = args.id;
    let id: string = documentEditor.element.id;
    switch (item) {
        case id + 'search_in_google':
            let searchContent: string = documentEditor.selection.text;
            if (!documentEditor.selection.isEmpty && /\S/.test(searchContent)) {
                window.open('http://google.com/search?q=' + searchContent);
            }
            break;
    }
};
// function to handle the CheckBox change event
function contextmenuHelper(args: ChangeEventArgs): void {
    documentEditor.contextMenu.addCustomMenu(menuItems, defaultCheckBoxObj.checked, positionCheckBoxObj.checked);
}

```

{% endtab %}
