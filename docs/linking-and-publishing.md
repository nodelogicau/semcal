# A brief history of calendaring

## Overview

- Linking and publishing are two important functions in calendaring
- Historically iCalendar has supported "linking" events, etc. with organizers, attendees,
and related events, etc.
- Publishing via email and HTTP is well-supported
- Recent specifications provide much richer linking to participants, locations,
resources, and anything addressable via URI
- These additional linking capabilities allow for more publishing alternatives, that
in-turn provide greater efficiency and consistency for linked data

- Two alternatives to enriching calendar data are to embed or link to more metadata
- For open standards, consensus on complex structures is difficult to obtain, making
embedding metadata more difficult 
- Links can be used in a backwards-compatible way, such that they may be ignored where
they are not supported
- Linked data is often represented as a knowledge graph, with the ability to traverse
the graph in any direction (requires reciprocal links*)
- The graphs representing events as implemented today by most vendors is very small
compared to the potential supported by today's standards
- The introduction of more linked data is also likely to increase frequency of updates,
as those links are updated

- For frequent, discrete changes to calendar data, email notifications are perhaps not
the most efficient or desirable publishing mechanism
- WebSub provides a means to deliver frequent and irregular changes without email or
HTTP polling


## iCal4j

* Core library supports parsing, object model, validation, etc.
* vCard provides parsing and object model for vCard
* Extensions builds on object models
* Serializer converts object model to other formats, including jCal and xCal
* Connector explores persistence, including CalDAV
* Integration supports iCalendar transports, including email
* Template provides creation patterns for common data types
* Command implements common patterns for data processing, including validation and serialization

With Open Source, we have the luxury of exploring not just the current state of calendaring, but
also what the future may look like.


## iCalendar LINK

* The LINK property introduces an important concept from the Semantic Web, the ability to connect
data to produce knowledge graphs
* RELATED-TO provides some support for connections, but was limited in scope
* Through links to external content we can enrich data without the burden of bloated metadata
* Links also offer good support for backwards compatibility, in that LINK properties are ignored
where they aren't supported

Linking allows us not only to extend the metadata of an object, but also to introduce ways
to distribute and discover new data.


## WebSub

* WebSub is a publish/subscribe model whereby data consumers can subscribe to a topic and receive
updates in near real time
* WebSub is good for distributing frequent (or infrequent) updates to a large number of subscribers
* Compared to polling, WebSub becomes increasingly more efficient as the number of subscribers grow
and/or the frequency of polling increases
* Calendar polling works today due to low frequency typical of most user agents. But what if we want
updates every 15 minutes, or every 15 seconds?
* iCalendar supports WebSub via the LINK RELTYPE=hub. Consumers can optionally subscribe to a topic
(probably based on the UID), by providing a callback URL for updates.

WebSub is naturally suited to public events, discoverable on the Web, etc. But also for events
distributed via email, such as registration confirmation, whereby METHOD=PUBLISH is typically used
as acceptance of the event is already implied. In such cases it is unlikely to receive further emails
for event updates, but could easily be distributed via WebSub.


## Webmention

* Webmention support registering reciprocal links back to the source of linked data. The source has the
option to inspect the link and incorporate into the original data
* There is no equivalent to Webmention in iCalendar today, but comparison could be made with iTIP method
REPLY (although Webmention is more applicable to creation of new data)
* A supporting user agent would check new objects for links to external content, which is parsed to identify
any LINK with RELTYPE=webmention. This link is then used to notify the source of the new link
* Webmention is almost the opposite of WebSub in terms of direction of data flow, completing the circle
between link data
  
Consider the scenario of a meeting scribe, taking attendance, notes and actions in their tool of choice.
The scribe may not be the meeting organizer, or even belong to the same organization. Using Webmention
to link the notes and actions to the original meeting will ensure all participants receive links to the
new data via the original meeting invitation.


## Knowledge Graphs and AI

* It may seem like an obligatory reference to AI, but AI is very relevant to calendaring as demonstrated
by many of the major players
* For example, Microsoft Copilot is already capable of observing a meeting and summarising the key points
and actions. It won't be long before AI is capable of also scheduling follow-up meetings using calendar
availability, etc.
* AI is currently dominated by proprietary offerings that lock data away, preventing open integration
and interoperability.

We need solutions that offer open access to data and connected knowledge graphs to promote the goals
of interoperability into the future.

The combination of WebSub and Webmention provides a basis for building connected knowledge graphs in
an open, non-proprietary way.
