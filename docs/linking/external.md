# Semantic Calendaring - Linking: External

A link to a reference that is not part of the same context as the enclosing component.

## References

An external LINK provides the ability to link multiple external references that may be used
in the context of the referencing component. Other iCalendar properties are intended for linking
to other iCalendar components, but none are suited to referencing non-iCalendar data.

## LINK vs RELATED-TO

The following table highlights the differences between an external LINK and 
[RELATED-TO](https://www.rfc-editor.org/rfc/rfc9253.html#name-related-to) properties.

| Feature                           | LINK    | RELATED-TO |
|-----------------------------------|---------|------------|
| Multiple instances allowed        | Yes     | Yes        |
| Supports non-iCalendar references | Yes     | No         |
| Relation type support             | Yes (*) | Yes        |
| Label support                     | Yes     | No         |

* NOTE: LINK relation types do not support the same relation types as RELATED-TO.
