---
title: "Working with Lists"
component: "DocumentEditor"
description: "Learn the types of lists supported in JavaScript document editor and how to apply or clear it for selected contents."
---

# Working with Lists

Document editor supports both the single-level and multilevel lists. Lists are used to organize data as step-by-step instructions in documents for easy understanding of key points. You can apply list to the paragraph either using supported APIs.

## Create bullet list

Bullets are usually used for unordered lists. To apply bulleted list for selected paragraphs, use the following method of ‘Editor’ instance.

> applyBullet(bullet, fontFamily);

|Parameter|Type|Description|
|---------|----|-----------|
|Bullet|string|Bullet character.|
|fontFamily|string|Bullet font family.|

Refer to the following sample code.

```typescript
documenteditor.editor.applyBullet('\uf0b7', 'Symbol');
```

## Create numbered list

Numbered lists are usually used for ordered lists. To apply numbered list for selected paragraphs, use the following method of ‘Editor’ instance.

> applyNumbering(numberFormat,listLevelPattern)

|Parameter|Type|Description|
|---------|----|-----------|
|numberFormat|string|“%n” representations in ‘numberFormat’ parameter will be replaced by respective list level’s value.“%1)” will be displayed as “1)”|
|listLevelPattern(optional)|string|Default value is 'Arabic'.|

Refer to the following example.

```typescript
documenteditor.editor.applyNumbering('%1)', 'UpRoman');
```

## Clear list

You can also clear the list formatting applied for selected paragraphs. Refer to the following sample code.

```typescript
documenteditor.editor.clearList();
```

## Working with lists

The following sample demonstrates how to create bullet and numbering lists in document editor.

{% tab template="document-editor/list",es5Template="list" , sourceFiles="index.ts" %}

```typescript
import {
  DocumentEditor,
  Editor,
  Selection,
  EditorHistory
} from '@syncfusion/ej2-documenteditor';
import { Toolbar } from '@syncfusion/ej2-navigations';
//Inject the require module
DocumentEditor.Inject(Editor, Selection, EditorHistory);

let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditorHistory: true,
  enableEditor: true,
});
function toolbarAction (args){
  switch (args.item.id) {
    case 'Bullets':
      //To create bullet list
      documenteditor.editor.applyBullet('\uf0b7', 'Symbol');
      break;
    case 'Numbering':
      //To create numbering list
      documenteditor.editor.applyNumbering('%1)', 'UpRoman');
      break;
    case 'clearlist':
      //To clear list
      documenteditor.editor.clearList();
      break;
  }
};

let toolbar: Toolbar = new Toolbar({
  clicked: toolbarAction,
  items: [
    {
      prefixIcon: 'e-de-icon-Bullets',
      tooltipText: 'Bullets',
      id: 'Bullets',
    },
    {
      prefixIcon: 'e-de-icon-Numbering',
      tooltipText: 'Numbering',
      id: 'Numbering',
    },
    {
      text: 'Clear',
      id: 'clearlist',
      tooltipText: 'Clear List',
    },
  ],
});
toolbar.appendTo('#toolbar');

function updateContainerSize() {
  document.getElementById('container').style.height =
    window.innerHeight - document.getElementById('toolbar').offsetHeight + 'px';
}

updateContainerSize();

documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## Editing numbered list

Document editor restarts the numbering or continue numbering for a numbered list. These options are found in the built-in context menu, if the list value is selected. Refer to the following screenshot.

![Image](images/list.png)

## See Also

* [List dialog](../document-editor/dialog#list-dialog/)
