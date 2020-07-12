
# Accessibility

Maps provides built-in compliance with the [WAI-ARIA](http://www.w3.org/WAI/PF/aria-practices/) specifications.
WAI-ARIA accessibility supports are achieved through the attributes like `aria-label`. It helps users to provide information about elements in a document for assistive technology.

**Aria-label:** Attribute provides text label with some default description for the following elements in maps.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Element</b></td>
<td><b>Default description</b></td>
</tr>
<tr>
<td>Maps container</td>
<td>-</td>
</tr>
<tr>
<td>Maps title</td>
<td>Reads maps title</td>
</tr>
<tr>
<td>Maps subtitle</td>
<td>Reads maps subtitle</td>
</tr>
<tr>
<td>Legend title</td>
<td>Reads legend title</td>
</tr>
</table>

 You can change this default description using the description property in `Legend`, `TitleSettings`,
 `SubtitleSettings` and `Maps` objects. It helps the screen reader to read for assistive purpose.