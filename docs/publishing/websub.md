# Semantic Calendaring - Publishing: WebSub

## Overview

We are used to thinking that APIs are the best (only?) way of sharing data across systems in an open way. But
API calls are not well-suited to all use-cases, in particular those involving asynchronous communication.

Instead of wasteful and inefficient API calls based on polling, we can implement callbacks in the form of
Webhooks or WebSub.

## What is WebSub?

WebSub is standard that defines both a model for topic subscription and topic updates (i.e. callbacks). It can
be used to share any type of data, but is currently more commonly associated with sharing syndication formats
such as RSS or Atom.

## WebSub for iCalendar

WebSub is well-suited for iCalendar (and vCard) updates, as they can range from frequent to infrequent depending
on the entity or event. Currently, the most common way to share updates for iCalendar is either via email or
Web-based polling. Both of these methods can be unsuited to either public events, or events that require
immediate change notifications.

WebSub can be considered as a "push" model whereby updates are sent directly to subscribers in near real-time.
