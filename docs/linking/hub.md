# Semantic Calendaring - Linking: Hub

A link to a WebSub hub used for topic registration and subscription.

## Push Notifications

[WebSub](../publishing/websub.md) is a W3C standard for publishing updates to subscribers on the Web. Typically,
this is used to publish Atom and RSS feed updates, however it also support other content
types.

A _hub_ LINK can be used to share subscription details for update topics to agents that
support them. To subscribe to a topic the subscriber must have both a hub location and
a topic name. For the name of the topic it is proposed a separate _self_ LINK would be used.

## Examples

    LINK;LINKREL="hub";VALUE=URI:https://websub.example.com/topic/subscribe
