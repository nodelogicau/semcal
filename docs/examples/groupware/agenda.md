# iCal4j Template - Groupware: Agenda

An Agenda represents one or more objectives for a meeting, or series of meetings. Sometimes a meeting may not
address all the items on an agenda due to lack of time, etc., so it is useful to maintain the Agenda separately
such that it may be shared across multiple meetings if required.

### Examples

Multiple Agenda may be linked in sequence to track items individually. This can be useful where time constraints
require additional meetings to address outstanding Agenda items:

```java
VToDo item4 = new Agenda().summary("Further business and close").uid(...).apply();
VToDo item3 = new Agenda().summary("Standing items").uid(...).nextItem(item4).apply();
VToDo item2 = new Agenda().summary("Business arising").uid(...).nextItem(item3).apply();
VToDo item1 = new Agenda().summary("ACME Monthly Board Meeting").uid(...).nextItem(item2).apply();

ComponentList agenda = new ComponentList(Arrays.asList(item1, item2, item3, item4);
```

The resulting component list looks like this:

    BEGIN:VTODO
    DTSTAMP:20231113T000000Z
    CONCEPT:https://ical4j.org/action-types/ACTION
    SUMMARY:ACME Monthly Board Meeting
    UID:1
    LINK;VALUE=UID;LINKREL=next:2
    END:VTODO
    BEGIN:VTODO
    DTSTAMP:20231113T000000Z
    CONCEPT:https://ical4j.org/action-types/ACTION
    SUMMARY:Business arising
    UID:2
    LINK;VALUE=UID;LINKREL=next:3
    END:VTODO
    BEGIN:VTODO
    DTSTAMP:20231113T000000Z
    CONCEPT:https://ical4j.org/action-types/ACTION
    SUMMARY:Standing items
    UID:3
    LINK;VALUE=UID;LINKREL=next:4
    END:VTODO
    BEGIN:VTODO
    DTSTAMP:20231113T000000Z
    CONCEPT:https://ical4j.org/action-types/ACTION
    SUMMARY:Further business and close
    UID:4
    END:VTODO
