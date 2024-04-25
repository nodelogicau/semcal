# Semantic Calendaring - Linking: Author

Identifies a component author, which can be important when a single component can be modified by multiple
collaborators.

## Change Management

The iCalendar specification includes properties specific to [change management](https://www.rfc-editor.org/rfc/rfc5545.html#section-3.8.7),
which includes `CREATED`, `DTSTAMP` and `LAST-MODIFIED` properties. These all provide temporal information regarding changes, but not
individuals that made the changes.

Additional properties such as `ORGANIZER` and `CONTACT` provide some means to identify authors, but have their limitations regarding multiple
collaborators.

## LINK vs ORGANIZER vs CONTACT

The following table highlights the benefits of using a LINK of type author, vs other property types:

| Feature                    | LINK | ORGANIZER          | CONTACT |
|----------------------------|------|--------------------|---------|
| Multiple instances allowed | Yes  | No                 | No      |
| Label support              | Yes  | Yes (CN parameter) | No      |
| Multi-lingual support      | Yes  | Yes                | Yes     |


## Examples

    LINK;LINKREL="author";VALUE=URI:mailto:franky@example.com
