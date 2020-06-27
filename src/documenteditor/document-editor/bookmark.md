---
title: "Bookmarks"
component: "DocumentEditor"
description: "Learn how to add, delete, or navigate bookmarks in JavaScript document editor."
---

# Bookmarks

Bookmark is a powerful tool that helps you to mark a place in the document to find again easily. You can enter many bookmarks in the document and give each one a unique name to identify easily.

Document editor provides built-in dialog to add, delete, and navigate bookmarks within the document. To add a bookmark, select a portion of text in the document. After that, jump to the location or add links to it within the document using built-in hyperlink dialog. You can also delete bookmarks from a document.

>Bookmark names need to begin with a letter. They can include both numbers and letters, but not spaces. To separate the words, use an underscore.
>Bookmark names starting with an underscore are called hidden bookmarks. For example, bookmarks generated for table of contents.

The following example shows how to open bookmark dialog in document editor.

{% tab template="document-editor/dialog",es5Template="bookmark-dialog" , sourceFiles="index.ts,index.html" %}

```typescript

import { DocumentEditor, Editor, Selection,SfdtExport, EditorHistory, BookmarkDialog } from '@syncfusion/ej2-documenteditor';
DocumentEditor.Inject(Editor, Selection, SfdtExport, EditorHistory, BookmarkDialog);
let documenteditor: DocumentEditor = new DocumentEditor({
isReadOnly: false,
enableEditor: true,
enableSelection: true,
enableEditorHistory: true,
enableBookmarkDialog: true
});
documenteditor.appendTo('#DocumentEditor');

document.getElementById('dialog').addEventListener('click', () => {
documenteditor.showDialog('Bookmark');
});

```

{% endtab %}

## See Also

* [Feature modules](../document-editor/feature-module/)
* [Bookmark dialog](../document-editor/dialog#bookmark-dialog/)
