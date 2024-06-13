# Semantic Calendaring - Publishing: Webmention

Webmention is a [W3C standard](https://www.w3.org/TR/webmention/) to support reciprocal links between published content
and reffering content (i.e. content that includes a link to the original content).

## Example: Meeting

As we propose to enrich event data by linking to external iCalendar objects, it becomes useful to have a mechanism
to discover and maintain relationships between such objects. One example is for scheduled meetings, whereby an
agenda, attendance, actions, etc. may all be maintained outside the context of the original meeting object.

Following the establishment of a meeting date and time, you may decide to publish an agenda. This agenda might be
defined as one or more `VTODO` objects, or even a `VJOURNAL` object, but by using Webmention to link back to the
original meeting `VEVENT` we can automatically ensure the agenda(s) are linked and published to all meeting 
participants.

Similarly, during the meeting a list of action items may be produced, again consisting of `VTODO` or other object
types. Again, using Webmention we can link these actions to the original meetings such that participants will all
have access to the relevant followup activities.

Post meeting, a summary of attendance and outcomes (i.e. meeeting minutes) may be produced and linked to the original
meeting. In all scenarios the use of Webmention provides a clear link to the original meeting and uses the established
communication channels to share these updates with participants.

## Challenges

There are some potential hurdles to using Webmention effectively, as follows:

* The Webmention protocol only allows linking between Web URLs, so all source and target objects must be accessible
via an unathenticated URL. This poses challenges to security of information contained in these objects. There is a
[Private Webmention](https://indieweb.org/Private-Webmention) extension to address access control, but as yet does
not appear to be finalsed.
* The source URL does not support metadata regarding the content of the URL, so there would be no way to indicate
whether a Webmention is an agenda item, an action or meeting minutes. An alternative specification called
[Linked Data Notification](https://www.w3.org/TR/ldn/) proposes to use JSON-LD to send notifications between Web
actors, which whist being more complex, could be used to convey metadata regarding links.
