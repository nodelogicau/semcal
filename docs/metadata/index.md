# Semantic Calendaring - Templating

Historically, Calendar User Agents (CUAs) have provided minimal support for templating supported iCalendar objects (notably `VEVENT`),
such that sensible defaults are applied. For example, Microsoft Outlook supports the creation of both Appointments (for individual events)
and Meetings (for group events), providing slight changes in the user interface (UI) to support creation of different `VEVENT` objects.

Similarly, you may find when you create an "All Day Event" the Time Transparency property will often default to `TRANSPARENT`, whereas an event
with a time component defaults to `OPAQUE`.

These are all behaviours implemented independently by different CUAs, but a more consistent approach to templating can be achieved
with the help of additional properties.

## Concept

The `CONCEPT` property was recently introduced to assist with more fine-grained classification of iCalendar object types. For
example, a `VEVENT` object is used to represent meetings, observances, appointments, etc., but without additional properties
it can be difficult to identify the purpose of a `VEVENT` object.

Semantic Calendaring proposes some initial `CONCEPT` definitions, including assumptions that can be made regarding each of the defined
concepts. For example, an Observance SHOULD always have time transparency of `TRANSPARENT` as it does not consume any time in a
calendar.

## Structured Data

The `STRUCTURED-DATA` property was added to support embedding additional structured information to support enhanced interoperability
between CUAs. With agreement on what structured data formats SHOULD be supported, a greater usefulness may emerge.

### JSON-LD

JSON Linked Data is commonly used to define page metatadata on the World Wide Web, such that search engines can more accurately index
and classify pages. Through embedding JSON-LD in iCalendar objects that same benefits relating to search indexing may be realised.

### RDFa

TBD.
