---
title: "Paste Cleanup"
component: "Rich Text Editor"
description: "This section explains on how to formate word content as HTML format by using the pasteCleanup settings in the RichTextEditor."
---

# Paste from MS Word

The Rich Text Editor allows you to reduce the effort while converting the Microsoft Word content to HTML format with format and styles.

## MS Word to HTML

By default, Rich Text Editor consider the following processes on paste content from Microsoft Word.

**List conversion:** The list elements copied from the Microsoft Word document contains paragraph tags with styles and classes. The list elements are converted to standard HTML list elements by referring the styles and class names in the paragraph tags.

**Converting style:** The styles of the elements copied from the Microsoft Word document are converted to standard CSS styles and added as inline styles for each respective element.

**Tags and comments:** The Microsoft Word specific XML tags and comments are removed when cleanup on paste.

## Paste cleanup

You can control the formatting and styles on pasting the content to the editor using the pasteCleanup settings property. The following settings are available to clean up the content:

| API | Description | Default Value | Type |
|:----------------:|:---------:|:-----------------------------:|:---------:|
| [prompt](#prompt) | To invoke prompt dialog with paste options on pasting the content in editor. | false | boolean |
| [plainText](#plain-text) | To paste the content as plain text. | false | boolean |
| [keepFormat](#keep-format) | To keep the same format with copied content. | true | boolean |
| [deniedTags](#denied-tags) | To ignore the tags when pasting HTML content. | null | string[] |
| [deniedAttrs](#denied-attributes) |  To paste the content by filtering out these attributes from the content. | null | string[] |
| [allowedStyleProps](#allowed-style-properties) |  To paste the content by accepting these style attributes and removing other style attributes. | ['background', 'background-color', 'border', 'border-bottom', 'border-left', 'border-radius', 'border-right', 'border-style', 'border-top', 'border-width', 'clear', 'color', 'cursor', 'direction', 'display', 'float', 'font', 'font-family', 'font-size', 'font-weight', 'font-style', 'height', 'left', 'line-height', 'margin', 'margin-top', 'margin-left', 'margin-right', 'margin-bottom', 'max-height', 'max-width', 'min-height', 'min-width', 'overflow', 'overflow-x', 'overflow-y', 'padding', 'padding-bottom', 'padding-left', 'padding-right', 'padding-top', 'position', 'right', 'table-layout', 'text-align', 'text-decoration', 'text-indent', 'top', 'vertical-align', 'visibility', 'white-space', 'width'] | string[] |

> Rich Text Editor features are segregated into individual feature-wise modules. To use paste cleanup, inject paste cleanup module using the `RichTextEditor.Inject(PasteCleanup)`.

## Prompt dialog

When `prompt` is set to true, pasting the content in the editor will open a dialog box that contains three options `Keep`, `Clean`, and `Plain Text` as radio buttons:
1. `Keep`: Radio button to keep the same format with copied content.
2. `Clean`: Radio button to clear all the style formats with copied content.
3. `Plain Text`: Radio button to paste the copied content as plain text without any formatting or style (including the removal of all tags).

> When `prompt` value is set true, the API properties [plainText](#plain-text) and [keepFormat](#keep-format) will not be considered for processing when pasting the content.

## Paste as plain text

When `plainText` is set to true, the copied content will be converted as plain text by removing all the HTML tags and styles applied to it and only the plain text is pasted in the editor.

> When `plainText` value is set true, the API property [prompt](#prompt) should be set to false, and [keepFormat](#keep-format) will not be considered for processing when pasting the content.

## Keep format

When `keepFormat` is set to true, the copied content will maintain all the style formatting allowed in the `allowedStyleProps` on pasting the content in the editor.

When `keepFormat` is set to false, the style in the copied content will be removed without considering the allowed styles in the `allowedStyleProps` when pasting the content in the editor.

> When `keepFormat` value is set true, the API property [prompt](#prompt) and [plainText](#plain-text) should be set to false.

## Denied tags

When `deniedTags` values are set, the tags that matches the 'denied tags' list will be removed on pasting the copied content in the editor. For Example,

1. `'a'`: Paste the content by filtering out anchor tags.
2. `'a[!href]'`: Paste the content by filtering out anchor tags that do not have the ‘href’ attribute.
3. `'a[href, target]'`: Paste the content by filtering out anchor tags that have the ‘href’ and ‘target’ attributes.

## Denied attributes

When the `deniedAttrs` values are set, the attributes that matches the 'denied attributes' list will be removed on pasting the copied content in the editor. For Example,

`'id', 'title'`: This will remove the attributes ‘id’ and ‘title’ from all tags.

## Allowed style properties

By default, the following basic styles are allowed on pasting the content to the editor.

['background', 'background-color', 'border', 'border-bottom', 'border-left', 'border-radius', 'border-right', 'border-style', 'border-top', 'border-width', 'clear', 'color', 'cursor', 'direction', 'display', 'float', 'font', 'font-family', 'font-size', 'font-weight', 'font-style', 'height', 'left', 'line-height', 'margin', 'margin-top', 'margin-left', 'margin-right', 'margin-bottom', 'max-height', 'max-width', 'min-height', 'min-width', 'overflow', 'overflow-x', 'overflow-y', 'padding', 'padding-bottom', 'padding-left', 'padding-right', 'padding-top', 'position', 'right', 'table-layout', 'text-align', 'text-decoration', 'text-indent', 'top', 'vertical-align', 'visibility', 'white-space', 'width']

When you configure allowedStyleProps, the styles, which matches the ‘allowed style properties’ list are allowed, all other style properties will be removed on pasting the content in the editor.

For Example,

`allowedStyleProps: ['color', 'margin']'`: This will allow only the style properties ‘color’ and ‘margin’ in each pasted element.

In the following example, the paste cleanup related settings are explained with its module configuration

{% tab template="rich-text-editor/toolbar/multirow", sourceFiles="app/**/*.ts,index.html,index.css" %}

```typescript
import { Component } from '@angular/core';
import { ToolbarService, HtmlEditorService, PasteCleanupService } from '@syncfusion/ej2-angular-richtexteditor';
@Component({
    selector: 'app-root',
    template: `<ejs-richtexteditor id='defaultRTE' [toolbarSettings]='tools' [pasteCleanupSettings]="pasteCleanupSettings">
    <ng-template #valueTemplate>
      <p>RichTextEditor is a WYSIWYG editing control which will reduce the effort for users while trying to express their formatting word content as HTML or Markdown format.</p>
      <p><b>Paste Cleanup properties:</b></p>
      <ul>
          <li>
              <p>prompt - specifies whether to enable the prompt when pasting in RichTextEditor.</p>
          </li>
          <li>
              <p>plainText - specifies whether to paste as plain text or not in RichTextEditor.</p>
          </li>
          <li>
              <p>keepFormat- specifies whether to keep or remove the format when pasting in RichTextEditor.</p>
          </li>
          <li>
              <p>deniedTags - specifies the tags to restrict when pasting in RichTextEditor.</p>
          </li>
          <li>
              <p>deniedAttributes - specifies the attributes to restrict when pasting in RichTextEditor.</p>
          </li>
          <li>
              <p>allowedStyleProperties - specifies the allowed style properties when pasting in RichTextEditor.</p>
          </li>
      </ul>
    </ng-template>
    </ejs-richtexteditor>`,
    providers: [ToolbarService, HtmlEditorService, PasteCleanupService]
})
export class AppComponent  {
    public tools: object = {
        type: 'MultiRow',
        items: ['Bold', 'Italic', 'Underline', 'StrikeThrough',
    'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
    'LowerCase', 'UpperCase', '|',
    'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
    'Outdent', 'Indent', '|',
    'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
    'SourceCode', 'FullScreen', '|', 'Undo', 'Redo']
    };
    public pasteCleanupSettings: object = {
    prompt: true,
    plainText: false,
    keepFormat: false,
    deniedTags: ['a'],
    deniedAttrs: ['class', 'title', 'id'],
    allowedStyleProps: ['color', 'margin', 'font-size']
};
}

```

{% endtab %}