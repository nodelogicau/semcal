# Semantic Calendaring

Semantic Calendaring explores the intersection of the Semantic Web with calendaring standards.

## Overview

Calendaring standards such as iCalendar have increasing support for Semantic Web concepts via updated and extensions to
the original specifications.

This enables calendaring software to participate in interoperability initiatives designed
for the Web. Some of these initiatives include:

* Web Linking
* Linked Data (e.g. JSON-LD, RDFa, etc.)
* Microformats
* WebSub
* WebMention
* Linked Data Notifications

In applying these standards natively to a calendaring context, the Semantic Web provides support for a powerful graph
of calendaring information.

## Principles

The principles of semantic calendaring can be divided into three areas: rich content, semantic data, and publishing.

### Rich Content

Calendar interoperability is both strengthened and limited by it's approach to backwards compatibility. Whilst catering to the
lowest common denominator has ensured maximum compatibility across calendaring clients, it has meant that simple features
such as rich content have struggled to gain traction.

Whilst the introduction of the `STYLED-DESCRIPTION` property was intended to solve the issue of rich content support, it's
implementation has been slow due to unclear guidelines on how it should be used.

Semcal proposes the following principles around using rich content in semantic calendar objects:

1. Every semantic calendar object SHOULD include a `STYLED-DESCRIPTION` property of content type `text/html`. This property SHOULD also
   be derived content (indicated via the `DERIVED=TRUE` parameter) to promote consistency of HTML styling and formatting.
2. A semantic calendar object SHOULD only be maintained via a single calendar user agent (CUA). This is to ensure that the rich content
   in each `STYLED-DESCRIPTION` property is consistent with the rest of the object (e.g. we explicitly want to avoid updating the
   `DESCRIPTION` property without updating the corresponding `STYLED-DESCRIPTION`. CUAs that don't support semantic calendaring SHOULD
   remove any `STYLED-DESCRIPTION` properties if they update the `DESCRIPTION` to avoid propogating inconsistent data.
3. A semantic calendar object SHOULD include a `LINK` property referring to a URL for editing/maintaining the object. This is specified
   via the `LINKREL=edit` parameter, which should be incorporated into an update function in supporting CUAs. This is to support simultaneous
   access to a calendar object (e.g. via CalDAV) using multiple clients.

### Semantic Data

Until recently iCalendar did not include a standard mechanism for typing or metadata. It now provides two, with the inclusion of `CONCEPT`
and `STRUCTURED-DATA` properties.

The following principles for semantic data are proposed by semcal:

1. Each semantic calendar object MUST include a `CONCEPT` property. This is used to specify the type of event, to-do, journal, etc.
   represented by the calendar object. An example of a type could be a Meeting event, a Service Request to-do, or a Metric journal.
   By specifying type information a richer interaction is facilitated between calendar user agents. NOTE: "vanilla" typing MUST also
   be supported by providing types that represent event, to-do, journal, etc. without further specificity.
2. A semantic calendar object SHOULD include linked data via the `STRUCTURED-DATA` property. Linked data is typically defined via
   JSON-LD or RDFa formats (JSON and XML respectively), and allows for interactions with non-calendaring systems. For example, a
   Web search engine may be able to parse the `STRUCTURED-DATA` property of semantic calendar objects in order to index the object
   for improved search results.


### Publishing

TBD.
