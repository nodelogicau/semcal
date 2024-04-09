# Semantic Calendaring - Alternate

An Alternate link property provides the location of an alternate representation of the enclosing component. This
could be interpreted as a duplication of the `URL` property, however `LINK` property allows more freedom to
specify multiple representations of a component.

## LINK vs URL

The following table compares the use of an alternate [LINK](https://www.rfc-editor.org/rfc/rfc9253.html#name-link) property against the
[URL](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.8.4.6) property.

| Feature                     | LINK | URL |
|-----------------------------|------|-----|
| Supported in all components | Yes  | Yes |
| Multiple instances allowed  | Yes  | No  |
| Label support               | Yes  | No  |
| Multi-lingual support       | Yes  | No  |
| Media type support          | Yes  | No  |


## Examples

    LINK;LINKREL="alternate";VALUE=URI:https://example.com/tasks/01234567-abcd1234.html
