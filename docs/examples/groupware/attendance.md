# iCal4j Template - Groupware: Attendance

A useful metric to track for meetings and other events is actual attendance. Whilst opaque events provide an
intention to attend, Attendance can provide a record of actual participation after the event.

### Examples

For each participant in a meeting attendance may be recorded as follows:

```java
VEvent meeting = ...
VCard attendee = ...
VJournal attendance = new Attendance().participant(new Contact(attendee))
            .start(LocalDateTime.of(2023, 11, 15, 9, 0))
            .end(LocalDateTime.of(2023, 11, 15, 9, 30))
            .context(meeting)
            .apply();
```

The attendance record looks something like this:

    BEGIN:VJOURNAL
    DTSTAMP:20231115T000000Z
    DTSTART:20231115T090000
    DTEND:20231115T093000
    RELATED-TO:9000
    BEGIN:PARTICIPANT
    PARTICIPANT-TYPE:CONTACT
    UID:1234
    CALENDAR-ADDRESS:mailto:attendee@example.com
    STRUCTURED-DATA;VALUE=BINARY;ENCODING=BASE64;FMTTYPE=text/vcard:QkVHSU46VkNBUkQNClVJRDoxMjM0DQpGTjpBdHRlbmRlZQ0KQ0FMQURSVVJJOm1haWx0bzphdHRlbmRlZUBleGFtcGxlLmNvbQ0KRU5EOlZDQVJEDQo=
    END:PARTICIPANT
    END:VJOURNAL
