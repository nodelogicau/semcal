# Semantic Calendaring - Publishing

Using existing W3C standards such as WebSub, calendar user agents (CUAs) can provide more dynamic updates to
calendaring information.

## Overview

When we think of publishing content on the Internet, it is usually associated with making content available
via a URL, which may have either public or restricted access. This includes websites (e.g. blogs, publications, etc.),
social media (i.e. posts and comments) and generally any content accessible via the World Wide Web.

However, other methods of content delivery may also be considered "publishing", including email, instant messaging,
and other push-based technologies. Whilst the iCalendar and vCard specifications are certainly compatible with
web-based publishing, they are also uniquely suited to content publishing via push technologies.

## Beyond Email

Sharing iCalendar events with third parties has long depended on the use of email or web-based publishing. Email
is commonly used to send event invitations using the iTIP specification for iCalendar object negotiation. Another
common use of email is to send basic event information that may be imported to a calendar without explicit
acceptance.

Web-based publishing of events is another popular way of importing events, and is also the basis for subscription
implementations that use polling to check for updates and automatically import any changes.
