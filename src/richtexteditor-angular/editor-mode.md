---
title: "Rich Text Editor Editor modes"
component: "Rich Text Editor"
description: "This section for Syncfusion Angular Rich Text Editor component to explain the markdown editing and HTML editing of the content through out the page."
---

# Editor modes

The Rich Text Editor component used to create, edit and return the content in valid HTML markup or markdown (MD) of the content. It supports following two editing formation.

* HTML Editor
* Markdown Editor

## HTML Editor

Rich Text Editor is a WYSIWYG editing control for formatting the word content as HTML.

The HTML editing mode is the default mode of Rich Text Editor. Which is used for format the content through the available toolbar items and returns the valid HTML markup. Set the [`editorMode`](../api/rich-text-editor/#editormode) property as `HTML`. To use HTML editing feature, inject `HtmlEditorService` in the provider section of `AppModule`.

```typescript

/**
* RTE HTML Editor functionality Sample
*/
import { Component } from '@angular/core';
import { ToolbarService, LinkService, ImageService, HtmlEditorService } from '@syncfusion/ej2-angular-richtexteditor';
@Component({
    selector: 'app-root',
    template: `<ejs-richtexteditor #defaultRTE id='defaultRTE'>
                <ng-template #valueTemplate>
                    <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor
                    that provides the best user experience to create and update the content.
                    Users can format their content using standard toolbar commands.</p>

                    <p><b>Key features:</b></p>

                    <ul><li><p>Provides &lt;IFRAME&gt; and &lt;DIV&gt; modes</p></li>
                    <li><p>Capable of handling markdown editing.</p></li>
                    <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
                    <li><p>Provides a fully customizable toolbar.</p></li>
                    <li><p>Provides HTML view to edit the source directly for developers.</p></li>
                    <li><p>Supports third-party library integration.</p></li>
                    <li><p>Allows preview of modified content before saving it.</p></li>
                    <li><p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p></li>
                    <li><p>Contains undo/redo manager.</p></li>
                    <li><p>Creates bulleted and numbered lists.</p></li>
                    </ul>
                </ng-template>
                </ejs-richtexteditor>`,
    providers: [ToolbarService, LinkService, ImageService, HtmlEditorService]
})
export class AppComponent  {

}

```

## Markdown Editor

Set the [`editorMode`](../api/rich-text-editor/#editormode) property value as `Markdown` to create or edit the content and apply formatting to view markdown formatted content.

The third-party library such as `Marked` or any other library is used to convert markdown into HTML content.

* The Supported Tags are  `h6`,`h5`,`h4`,`h3`,`h2`,`h1`,`blockquote`,`pre`,`p`,`ol`,`ul`.
* The Supported Selection Tags are `Bold`, `Italic`, `StrikeThrough`, `InlineCode`, `SubScript`, `SuperScript`, `UpperCase`, `LowerCase`.
* The supported insert commands are `Image`, `Link` and `Table`.

For further details on Markdown editing, refer to the [`Markdown`](../markdown.html)

```typescript

    /**
    * RTE MarkDown Editor Sample
    */
    import { Component } from '@angular/core';
    import { ToolbarService, LinkService, ImageService, MarkdownEditorService } from '@syncfusion/ej2-angular-richtexteditor';
    @Component({
    selector: 'app-root',
    template: `<ejs-richtexteditor #rteMarkDown id='markDown' [editorMode]='mode'>
                <ng-template #valueTemplate>
                  ***Overview***
                  The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor used to create, edit and return the content in valid HTML markup or markdown (MD) of the content.
                  The editor provides a standard toolbar to format content using its commands. Modular library features to load the necessary functionality on demand.
                  The toolbar contains commands to align the text, insert link, insert image, insert list, undo/redo operation, HTML view, and more.
                  ***Key features***
                  - *Mode*: Provides IFRAME and DIV mode.
                  - *Module*: Modular library to load the necessary functionality on demand.
                  - *Toolbar*: Provide a fully customizable toolbar.
                  - *Editing*: HTML view to edit the source directly for developers.
                  - *Third-party Integration*: Supports to integrate third-party library.
                  - *Preview*: Preview the modified content before saving it.
                  - *Tools*: Handling images, hyperlinks, video, uploads and more.
                  - *Undo and Redo*: Undo/redo manager.
                  - *Lists*:Creates bulleted and numbered list.
                </ng-template>
               </ejs-richtexteditor>`,
               providers: [ToolbarService, LinkService, ImageService, MarkdownEditorService]
})
export class AppComponent  {
  public mode: string = 'Markdown';
}

```
