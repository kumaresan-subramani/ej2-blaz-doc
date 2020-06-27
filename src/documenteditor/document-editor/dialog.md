---
title: "Dialog"
component: "DocumentEditor"
description: "Learn the built-in dialog support in JavaScript document editor and how to open it."
---

# Dialog

Documenteditor provides dialog support to major operations such as insert or edit hyperlink, formatting text, paragraph, style, list and table properties.

## Font Dialog

Font dialog allows you to modify all text properties for selected contents at once such as bold, italic, underline, font size, font color, strikethrough, subscript and superscript.

Refer to the following example.

{% tab template="document-editor/dialog",es5Template="font" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  FontDialog,
  SfdtExport,
} from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, FontDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableFontDialog: true,
  enableSfdtExport: true,
});
let containerPanel: HTMLElement = document.getElementById('container');
let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {

  // To open Font Dialog
  documenteditor.showDialog('Font');
});
function updateContainerSize() {
  containerPanel.style.height =
    window.innerHeight - document.getElementById('toolbar').offsetHeight + 'px';
}

updateContainerSize();
documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## Paragraph dialog

This dialog allows modifying the paragraph formatting for selection at once such as text alignment, indentation, and spacing.

To open this dialog, refer to the following example.

{% tab template="document-editor/dialog",es5Template="paragraph-dialog" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  ParagraphDialog,
  SfdtExport,
} from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, ParagraphDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableParagraphDialog: true,
  enableSfdtExport: true,
});
let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {
  //To open paragraph dialog
  documenteditor.showDialog('Paragraph');
});
documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## Table dialog

This dialog allows creating and inserting a table at cursor position by specifying the required number of rows and columns.

To open this dialog, refer to the following example.

{% tab template="document-editor/dialog",es5Template="table-dialog" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  TableDialog,
  SfdtExport,
} from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, TableDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableTableDialog: true,
  enableSfdtExport: true,
});
let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {
  //To open table dialog
  documenteditor.showDialog('Table');
});
documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## Bookmark dialog

This dialog allows you to perform the following operations:

* View all bookmarks.
* Navigate to a bookmark.
* Create a bookmark at current selection.
* Delete an existing bookmark.
To open this dialog, refer to the following example.

{% tab template="document-editor/dialog",es5Template="bookmark-dialog" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  BookmarkDialog,
  SfdtExport,
} from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, BookmarkDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableBookmarkDialog: true,
  enableSfdtExport: true,
});
let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {
  //To open bookmark dialog
  documenteditor.showDialog('Bookmark');
});
documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## Hyperlink dialog

This dialog allows editing or inserting a hyperlink at cursor position.

To open this dialog, refer to the following example.

{% tab template="document-editor/dialog",es5Template="link-dialog" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  HyperlinkDialog,
  SfdtExport,
} from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, HyperlinkDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableHyperlinkDialog: true,
  enableSfdtExport: true,
});
let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {
  //To open hyperlink dialog
  documenteditor.showDialog('Hyperlink');
});
documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## Table of contents dialog

This dialog allows creating and inserting table of contents at cursor position. If the table of contents already exists at cursor position, you can customize its properties.

To open this dialog, refer to the following example.

{% tab template="document-editor/dialog",es5Template="toc-dialog" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  TableOfContentsDialog,
  SfdtExport
} from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, TableOfContentsDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableTableOfContentsDialog: true,
  enableSfdtExport: true,
});
let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {
  //To open table of contents dialog
  documenteditor.showDialog('TableOfContents');
});
documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## Styles Dialog

This dialog allows managing the styles in a document. It will display all the styles in the document with options to modify the properties of the existing style or create new style with the help of ‘Style dialog’. Refer to the following example.

{% tab template="document-editor/dialog",es5Template="styles-dialog" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  StyleDialog,
  StylesDialog,
  SfdtExport,
} from '@syncfusion/ej2-documenteditor';

DocumentEditor.Inject(Editor, Selection, SfdtExport, StyleDialog,StylesDialog);

let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableStyleDialog: true,
  enableSfdtExport: true,
  enableStylesDialog:true
});

let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {

  //To open styles dialog
  documenteditor.showDialog('Styles');
});

documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## Style dialog

You can directly use this dialog for modifying any existing style or add new style by providing the style name.

To open this dialog, refer to the following example.

{% tab template="document-editor/dialog",es5Template="style-dialog" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  StyleDialog,
  SfdtExport
} from '@syncfusion/ej2-documenteditor';

DocumentEditor.Inject(Editor, Selection, SfdtExport, StyleDialog);

let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableStyleDialog: true,
  enableSfdtExport: true
});

let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {

  //To open style dialog
  documenteditor.showDialog('Style');
});

documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## List dialog

This dialog allows creating a new list or modifying existing lists in the document.

To open this dialog, refer to the following example.
{% tab template="document-editor/dialog",es5Template="list-dialog" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  ListDialog,
  SfdtExport,
} from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, ListDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableListDialog: true,
  enableSfdtExport: true,
});
let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {
  //To open list dialog
  documenteditor.showDialog('List');
});
documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## Borders and shading dialog

This dialog allows customizing the border style, border width, and background color of the table or selected cells.

To open this dialog, refer to the following example.

{% tab template="document-editor/dialog",es5Template="borders-shading" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  BordersAndShadingDialog,
  SfdtExport,
} from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, BordersAndShadingDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableBordersAndShadingDialog: true,
  enableSfdtExport: true,
});
let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {
  //To open hyperlink dialog
  documenteditor.showDialog('BordersAndShading');
});
documenteditor.appendTo('#DocumentEditor');
documenteditor.editor.insertTable(2,2);

```

{% endtab %}

## Table options dialog

This dialog allows customizing the default cell margins and spacing between each cells of the selected table.

To open this dialog, refer to the following example.

{% tab template="document-editor/dialog",es5Template="table-options" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  TableOptionsDialog,
  SfdtExport,
} from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, TableOptionsDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableTableOptionsDialog: true,
  enableSfdtExport: true,
});
let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {
  //To open table options dialog
  documenteditor.showDialog('TableOptions');
});
documenteditor.appendTo('#DocumentEditor');
documenteditor.editor.insertTable(2,2);

```

{% endtab %}

## Table properties dialog

This dialog allows customizing the table, row, and cell properties of the selected table.

To open this dialog, refer to the following example.

{% tab template="document-editor/dialog",es5Template="table-properties" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  TableOptionsDialog,
  TablePropertiesDialog,
  BordersAndShadingDialog,
  SfdtExport,
} from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, TablePropertiesDialog,
  BordersAndShadingDialog,TableOptionsDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enableTableOptionsDialog: true,
  enableTablePropertiesDialog:true,
  enableBordersAndShadingDialog:true,
  enableSfdtExport: true,
});
let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {
  //To open table properties dialog
  documenteditor.showDialog('TableProperties');
});
documenteditor.appendTo('#DocumentEditor');
documenteditor.editor.insertTable(2,2);

```

{% endtab %}

## Page setup dialog

This dialog allows customizing margins, size, and layout options for pages of the section.

To open this dialog, refer to the following example.

{% tab template="document-editor/dialog",es5Template="page-setup" , sourceFiles="index.ts,index.html" %}

```typescript

import {
  DocumentEditor,
  Editor,
  Selection,
  PageSetupDialog,
  SfdtExport
} from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, PageSetupDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
  isReadOnly: false,
  enableSelection: true,
  enableEditor: true,
  enablePageSetupDialog: true,
  enableSfdtExport: true,
});
let button: HTMLElement = document.getElementById('dialog');
button.addEventListener('click', function() {
  //To open page setup dialog
  documenteditor.showDialog('PageSetup');
});
documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## See Also

* [Feature module](../document-editor/feature-module/)