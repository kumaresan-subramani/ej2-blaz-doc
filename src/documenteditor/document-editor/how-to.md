---
title: "How to"
component: "DocumentEditor"
description: "Learn how to work with document editor in real time scenarios like create simple word processor, override keyboard shortcut behaviors, and more."
---

# How to override the keyboard shortcuts in document editor

Document editor triggers the [`keyDown`](../api/document-editor/documentEditorKeyDownEventArgs/) event every time when any key is entered and provides an instance of `DocumentEditorKeyDownEventArgs`. You can use the `isHandled` property to override the keyboard shortcut behaviour.

## Preventing default keyboard shortcut

The following code shows how to prevent the `CTRL + C` keyboard shortcut for copying selected content in document editor.

{% tab template="document-editor/prevent-keyboard", es5Template="prevent-keyboard", sourceFiles="index.ts,index.html" %}

```typescript
import { DocumentEditor, Selection, Editor, DocumentEditorKeyDownEventArgs } from '@syncfusion/ej2-documenteditor';

DocumentEditor.Inject(Selection, Editor)

let documentEditor: DocumentEditor = new DocumentEditor({ enableEditor: true, isReadOnly: false });

documentEditor.appendTo('#DocumentEditor');

documentEditor.keyDown = function (args: DocumentEditorKeyDownEventArgs) {
    let keyCode: number = args.event.which || args.event.keyCode;
    let isCtrlKey: boolean = (args.event.ctrlKey || args.event.metaKey) ? true : ((keyCode === 17) ? true : false);
    //67 is the character code for 'C'
    if (isCtrlKey && keyCode === 67) {
        //To prevent copy operation set isHandled to true
        args.isHandled = true;
    }
}
```

{% endtab %}

## Override or define the keyboard shortcut

Override or define a new keyboard shortcut behaviour instead of preventing the keyboard shortcut.

For example, `Ctrl + S` keyboard shortcut saves the document in SFDT format by default, and there is no behaviour for `Ctrl + Alt + S`. The following code demonstrates how to override the `Ctrl + S` shortcut to save a document in DOCX format and define `Ctrl + Alt + S` to save the document in SFDT format.

{% tab template="document-editor/override-keyboard", es5Template="override-keyboard", sourceFiles="index.ts,index.html" %}

```typescript
import { DocumentEditor, Selection, Editor, DocumentEditorKeyDownEventArgs, SfdtExport, WordExport } from '@syncfusion/ej2-documenteditor';

DocumentEditor.Inject(Selection, Editor, SfdtExport, WordExport);

let documentEditor: DocumentEditor = new DocumentEditor({ enableEditor: true, enableSfdtExport : true, enableWordExport: true, isReadOnly:false });

documentEditor.appendTo('#DocumentEditor');

documentEditor.keyDown = function (args: DocumentEditorKeyDownEventArgs) {
    let keyCode: number = args.event.which || args.event.keyCode;

    let isCtrlKey: boolean = (args.event.ctrlKey || args.event.metaKey) ? true : ((keyCode === 17) ? true : false);

    let isAltKey: boolean = args.event.altKey ? args.event.altKey : ((keyCode === 18) ? true : false);

   // 83 is the character code for 'S'
    if (isCtrlKey && !isAltKey && keyCode === 83) {
        //To prevent default save operation, set the isHandled property to true
        args.isHandled = true;
       documentEditor.save('sample', 'Docx');
       args.event.preventDefault();
    } else if (isCtrlKey && isAltKey && keyCode === 83) {
       documentEditor.save('sample', 'Sfdt');
    }
}
```

{% endtab %}