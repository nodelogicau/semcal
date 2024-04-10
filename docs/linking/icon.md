# Semantic Calendaring - Icon

A link to a static or dynamic icon representing the referencing component.

## Visual Cues

Icons are important for conveying information regarding contextual type or state
when represented in a user interface (UI). This could potentially provide enourmous
benefits in calendaring, especially when rendering events in a calendar layout.

### Static Icons

A static icon is one where it represents a specific feature of a component, such as
concept or type. Such an icon would not change in response to contextual changes.

### Dynamic Icons

A dynamic icon could be used to impart additional information such as status or
progress of the referenced component. Dynamic icons should be carefully considered
as it would be sourcing information from an external location that is not necessarily
synced with the local representation.

## LINK vs ATTACH vs IMAGE

The following table outlines differences between an _icon_ LINK and
[ATTACH](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.8.1.1) or 
[IMAGE](https://www.rfc-editor.org/rfc/rfc7986.html#section-5.10) properties. 

| Feature         | LINK | ATTACH | IMAGE                   |
|-----------------|------|--------|-------------------------|
| Per component   | Yes  | Yes    | Yes                     |
| Label support   | Yes  | No     | No                      |
| Rendering hints | No   | No     | Yes (via DISPLAY param) |
