# Semantic Calendaring - Edit

A link to a form or application that supports editing of the enclosing component.

## Editor Support

An existing challenge with iCalendar is maintaining a single source of truth for components,
as they may be modified using different editors connected to the same calendar store (e.g.
a CalDAV implementation).

The multiple editor problem is compounded when potentially derived properties are introduced
(e.g. `STYLED-DESCRIPTION`), leading to inconsistent and potentially outdated properties.

The inclusion of an edit LINK could provide a recommended way to update a component, that is
consistent with the initial authoring. Such a link may also be used to extend the functionality
of calendar user agents (CUAs) by integrating external editors into the user interface (UI).

## Examples

    LINK;LINKREL="edit";VALUE=URI:https://example.com/tasks/01234567-abcd1234?action=edit
