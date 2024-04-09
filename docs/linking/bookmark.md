# Semantic Calendaring - Bookmark

A permalink (bookmark) to the enclosing component.

## External Referencing

A bookmark link may be useful for providing a portable link to the original source
of a component. Such a link SHOULD be accessible from anywhere and return the same
result (i.e. the original component).

A bookmark link may also be used in conjunction with a hub link in order to subscribe
to a WebSub topic providing updates to the specified component.

## LINK vs SOURCE

The following table outlines differences between a bookmark LINK and 
[SOURCE](https://www.rfc-editor.org/rfc/rfc7986.html#section-5.8) property.

| Feature       | LINK | SOURCE |
|---------------|------|--------|
| Per component | Yes  | No     |
| Label support | Yes  | No     |

## Examples

    LINK;LINKREL="bookmark";VALUE=URI:https://example.com/tasks/01234567-abcd1234.ics
