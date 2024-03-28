# iCal4j Template - Groupware: Meeting

Perhaps the most common use of iCalendar is to define and share meeting invites. A Meeting is a closed invitation to
select recipients in order for collaborative discussion or other activities. This template may be used to create
or modify `VEVENT` objects to conform with conventional approaches to defining meeting invites.

### Examples

Assuming we use vCard to represent meeting participants, we can construct a new meeting:

```java
VCard organizer = ...
VCard chair = ...

VEvent meeting = new Meeting().organizer(organizer)
            .chair(new Contact(chair))
            .start(LocalDate.of(2023, 11, 13).atStartOfDay())
            .duration(Duration.ofMinutes(30)).apply();
```

The result is something like this:

    BEGIN:VEVENT
    DTSTAMP:20231113T000000Z
    ORGANIZER;CN=Big Boss:mailto:boss@example.com
    DTSTART:20231113T000000
    DURATION:PT30M
    CONCEPT:https://ical4j.org/event-types/MEETING
    ATTENDEE;CUTYPE=INDIVIDUAL;ROLE=CHAIR:mailto:lead-by@example.com
    BEGIN:PARTICIPANT
    PARTICIPANT-TYPE:CONTACT
    UID:1234
    CALENDAR-ADDRESS:mailto:lead-by@example.com
    STRUCTURED-DATA;VALUE=BINARY;ENCODING=BASE64;FMTTYPE=text/vcard:QkVHSU46VkNBUkQNClVJRDoxMjM0DQpGTjpUZWFtIExlYWQNCkNBTEFEUlVSSTptYWlsdG86bGVhZC1ieUBleGFtcGxlLmNvbQ0KRU5EOlZDQVJEDQo=
    END:PARTICIPANT
    END:VEVENT    
