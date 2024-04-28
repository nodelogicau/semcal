# Semantic Calendaring

Semantic Calendaring explores the intersection of the Semantic Web with calendaring standards.

## Introduction

The Internet was designed to connect multiple disparate nodes spread across many different networks. And whilst
it was intended to promote decentralisation of data, we increasingly see data siloed in proprietary systems
for financial gain.

### Open Standards

To protect user rights to data ownership and control, we must strive to implement and evolve open standards, such
as those defined by the Internet Engineering Task Force (IETF) and the World Wide Web Consortium (W3C). In this
way we ensure maximum interoperability and data portability.

### The Semantic Web

The W3C and IETF have defined a number of standard to promote data sharing via common formats, such as the
Resource Definition Framework (RDF), JSON Linked Data (JSON-LD) and the ATOM Syndication Format. Such standards
define a shared model for both WHAT data can be shared and HOW it can be shared.

Whilst such shared purpose models are useful for maximising data sharing, often we find more specific data formats
and protocols can be more suited for specific types of data. One such example is the use of iCalendar for events
and other time-based information.

### iCalendar

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

The principles of semantic calendaring can be divided into four areas: rich content, semantic data, linking
and publishing.

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

### Templates

Templating is often used to apply sensible defaults and semantic metadata when creating new events and other objects. iCalendar has
recently introduced two properties supporting semantic metadata: `CONCEPT` and `STRUCTURED-DATA`. Using `CONCEPT` we are able to
provide more granular type information that allows CUAs to recognise and process objects differently.

`STRUCTURED-DATA` allows us to capture or generate additional data formats beyond the scope of the iCalendar specification. We can
embed agreed formats (such as JSON-LD) to enhance CUAs' interoperability. 

The following principles for semantic data are proposed by semcal:

1. Each semantic calendar object MUST include a `CONCEPT` property. This is used to specify the type of event, to-do, journal, etc.
   represented by the calendar object. An example of a type could be a Meeting event, a Service Request to-do, or a Metric journal.
   By specifying type information a richer interaction is facilitated between calendar user agents. NOTE: "vanilla" typing MUST also
   be supported by providing types that represent event, to-do, journal, etc. without further specificity.
2. A semantic calendar object SHOULD include linked data via the `STRUCTURED-DATA` property. Linked data is typically defined via
   JSON-LD or RDFa formats (JSON and XML respectively), and allows for interactions with non-calendaring systems. For example, a
   Web search engine may be able to parse the `STRUCTURED-DATA` property of semantic calendar objects in order to index the object
   for improved search results.


### Linking

The `LINK` property allows for additional linking between semantic calendar objects to support construction of a 
larger semantic graph.

The following semcal principles demonstrate additional linking relationships:

1. For recurring events, individual occurrences may be customized with additional information specifically for that instance.
   With semcal, when customising such an instance the CUA SHOULD include a `LINK` property referring to the previous instance
   via the `LINKREL=prev` parameter.
2. Semantic calendaring objects SHOULD include authoring information via one or more `LINK` properties with a `LINKREL=author`
   parameter.


### Publishing

Whilst many calendaring clients support subscribing to remote calendars, the reality is that most published events are statically
imported to internal calendars either via Web links or email attachments.

The following principles propose how to support subscriptions for updating individual events:

1. A CUA supporting semantic calendar SHOULD create a topic named from the event `UID` value for each published event via a WebSub
   hub. This hub is to be linked in the event via a `LINK` with `LINKREL=hub`. A recipient CUA SHOULD check for such `LINK`
   properties and automatically subscribe to the topic corresponding to the event `UID`. The subscription duration should be at
   least until the event has passed, but typically with an additional grace period to allow for updates including media related
   to the event.
2. Optionally, a CUA may choose to support reciprocal links for specific events via the Webmention standard. To support reciprocal
   links a semantic calendar object MUST include a `LINK` property referring to a callback URL for posting a new link. This
   property is identified via the `LINKREL=webmention` parameter. When creating new calendar objects that refer to another, CUAs
   may check for a Webmention link in the related object and POST a link to the new event. The receiving CUA may optionally
   require approval prior to updating the original event with the new link, but once approved would add a new `LINK` property
   for the URL using the `LINKREL=replies` parameter.

