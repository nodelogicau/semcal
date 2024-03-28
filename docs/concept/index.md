# iCal4j Extensions - Concept

The iCalendar property `CONCEPT` was recently ratified as a standard way to classify iCalendar objects. These extensions
provide some suggested classifications that represent common use-cases for different types of iCalendar objects.

## Overview

The following iCal4j concepts are derived from the different structural patterns used to support different
use-cases for iCalendar objects.

These concepts include:

* [Event](event.md) - an opaque `VEVENT` object that may support recurrences.
* [Observance](observance.md) - a transparent `VEVENT` object that may support recurrences.
* [Action](action.md) - a `VTODO` object that is assignable to individuals for resolution. Supports recurrences.
* [Issue](issue.md) - a `VTODO` object capturing a one-off impediment to other activities or actors. Does not support recurrences.
* [Request](request.md) - a `VTODO` object representing a service request, often fulfilled via an [Action](action.md). May support recurrences.
* [Note](note.md) - a `VJOURNAL` object capturing a note or annotation related to other activities or entities. Does not support recurrences.
* [Metric](metric.md) - a `VJOURNAL` object used to measure past activities or entities. Supports recurrences.
* [Availability](availability.md) - a `VAVAILABILITY` object that defines availability of an intangible or tangible resource. Supports recurrences.
* [Asset](asset.md) - a `VRESOURCE` object representing a related asset. May be used when linking to external resources is insufficient.
* [Contributor](contributor.md) - a `PARTICIPANT` that defines additional roles/contributions beyond those supported by the participant type.
