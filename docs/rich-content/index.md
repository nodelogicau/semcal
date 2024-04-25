# Semantic Calendaring - Rich Content

Calendar User Agent (CUA) support for semantic calendaring is the ultimate goal, as this is how we achieve 
interoperability at the presentation layer (user interface).

The following sections provide guidance on how a CUA might choose to implement support for the semantic
calendaring principles/features.

## Rich Content

Some CUAs already provide support for rich text in descriptions, however the approach may differ from client
to client, leading to incompatible data.

### STYLED-DESCRIPTION

The `STYLED-DESCRIPTION` property was recently added to the iCalendar specification as a standard way of
supporting rich text. Whilst it has been available for nearly two years, support for this property is still
limited.

The following shows an example of what an implementation SHOULD look like:

```
BEGIN:VCALENDAR
PRODID:-//Mozilla.org/NONSGML Mozilla Calendar V1.1 + STYLED-DESCRIPTION//EN
VERSION:2.0
BEGIN:VEVENT
CREATED:20240425T025347Z
LAST-MODIFIED:20240425T025908Z
DTSTAMP:20240425T025908Z
UID:4d19e231-6559-43fc-9f76-c8d3c5ab763d
SUMMARY:ANZAC Day
RRULE:FREQ=YEARLY
CATEGORIES:Public Holiday
DTSTART;VALUE=DATE:20240425
DTEND;VALUE=DATE:20240426
TRANSP:TRANSPARENT
DESCRIPTION:ANZAC Day\nA day
  commemorated by Australia and New Zealand annually.\n\n
STYLED-DESCRIPTION:%3Ch1%3E%3Cb%3EANZAC%20Day%3C%2Fb%3E%3C%
 2Fh1%3E%3Ch1%3E%3C%2Fh1%3E%3Cb%3E%3C%2Fb%3EA%20day%20commemorated%20by%20Au
 stralia%20and%20New%20Zealand%20annually.%3Cbr%3E%3Cbr%3E
X-MOZ-GENERATION:1
END:VEVENT
END:VCALENDAR
```

### Thunderbird (ALTREP Parameter)

Mozilla Thunderbird uses the `ALTREP` parameter on `DESCRIPTION` property to provide HTML markup of text:

```
BEGIN:VCALENDAR
PRODID:-//Mozilla.org/NONSGML Mozilla Calendar V1.1//EN
VERSION:2.0
BEGIN:VEVENT
CREATED:20240425T025347Z
LAST-MODIFIED:20240425T025908Z
DTSTAMP:20240425T025908Z
UID:4d19e231-6559-43fc-9f76-c8d3c5ab763d
SUMMARY:ANZAC Day
RRULE:FREQ=YEARLY
CATEGORIES:Public Holiday
DTSTART;VALUE=DATE:20240425
DTEND;VALUE=DATE:20240426
TRANSP:TRANSPARENT
DESCRIPTION;ALTREP="data:text/html,%3Ch1%3E%3Cb%3EANZAC%20Day%3C%2Fb%3E%3C%
 2Fh1%3E%3Ch1%3E%3C%2Fh1%3E%3Cb%3E%3C%2Fb%3EA%20day%20commemorated%20by%20Au
 stralia%20and%20New%20Zealand%20annually.%3Cbr%3E%3Cbr%3E":ANZAC Day\nA day
  commemorated by Australia and New Zealand annually.\n\n
X-MOZ-GENERATION:1
END:VEVENT
END:VCALENDAR
```

## Google (Rich text in DESCRIPTION)

Google Calendar writes HTML markup directly in the `DESCRIPTION` property:

```
BEGIN:VCALENDAR
PRODID:-//Google Inc//Google Calendar 70.9054//EN
VERSION:2.0
CALSCALE:GREGORIAN
METHOD:REQUEST
BEGIN:VEVENT
DTSTART;VALUE=DATE:20240425
DTEND;VALUE=DATE:20240426
RRULE:FREQ=YEARLY
DTSTAMP:20240425T031133Z
UID:1rc1b7jt5417nnv58p2s22kvvq@google.com
X-MICROSOFT-CDO-OWNERAPPTID:1686630808
CREATED:20240425T030556Z
DESCRIPTION:<b>ANZAC Day</b><br><b> </b><br>A day commemorated by Australia
  and New Zealand annually.<br><b> </b>
LAST-MODIFIED:20240425T031132Z
LOCATION:
SEQUENCE:0
STATUS:CONFIRMED
SUMMARY:ANZAC Day
TRANSP:TRANSPARENT
END:VEVENT
END:VCALENDAR
```

## Outlook.com

Microsoft's consumer-grade calendar in Outlook.com supports entering rich text, but doesn't persist it to 
the iCalendar format:

```
BEGIN:VCALENDAR
METHOD:REQUEST
PRODID:Microsoft Exchange Server 2010
VERSION:2.0
BEGIN:VTIMEZONE
TZID:AUS Eastern Standard Time
BEGIN:STANDARD
DTSTART:16010101T030000
TZOFFSETFROM:+1100
TZOFFSETTO:+1000
RRULE:FREQ=YEARLY;INTERVAL=1;BYDAY=1SU;BYMONTH=4
END:STANDARD
BEGIN:DAYLIGHT
DTSTART:16010101T020000
TZOFFSETFROM:+1000
TZOFFSETTO:+1100
RRULE:FREQ=YEARLY;INTERVAL=1;BYDAY=1SU;BYMONTH=10
END:DAYLIGHT
END:VTIMEZONE
BEGIN:VEVENT
DESCRIPTION;LANGUAGE=en-AU:ANZAC Day\n\nA day commemorated by Australia and
  New Zealand annually.\n\n
RRULE:FREQ=YEARLY;INTERVAL=1;BYMONTHDAY=25;BYMONTH=4
UID:040000008200E00074C5B7101A82E0080000000064AA10D7BF96DA01000000000000000
 010000000B51DA4866163C44B860696E5898759A3
SUMMARY;LANGUAGE=en-AU:ANZAC Day
DTSTART;VALUE=DATE:20240425
DTEND;VALUE=DATE:20240426
CLASS:PUBLIC
PRIORITY:5
DTSTAMP:20240425T032245Z
TRANSP:TRANSPARENT
STATUS:CONFIRMED
SEQUENCE:0
LOCATION;LANGUAGE=en-AU:
X-MICROSOFT-CDO-APPT-SEQUENCE:0
X-MICROSOFT-CDO-OWNERAPPTID:2122633060
X-MICROSOFT-CDO-BUSYSTATUS:FREE
X-MICROSOFT-CDO-INTENDEDSTATUS:FREE
X-MICROSOFT-CDO-ALLDAYEVENT:TRUE
X-MICROSOFT-CDO-IMPORTANCE:1
X-MICROSOFT-CDO-INSTTYPE:1
X-MICROSOFT-DONOTFORWARDMEETING:FALSE
X-MICROSOFT-DISALLOW-COUNTER:FALSE
X-MICROSOFT-REQUESTEDATTENDANCEMODE:DEFAULT
X-MICROSOFT-ISRESPONSEREQUESTED:TRUE
X-MICROSOFT-LOCATIONS:[]
END:VEVENT
END:VCALENDAR
```

## Outlook (X-ALT-DESC)

Microsoft's business application Outlook uses the addition of a non-standard `X-ALT-DESC` property to persist a
quite convoluted version of HTML markup:

```
BEGIN:VCALENDAR
PRODID:-//Microsoft Corporation//Outlook 16.0 MIMEDIR//EN
VERSION:2.0
METHOD:PUBLISH
X-MS-OLK-FORCEINSPECTOROPEN:TRUE
BEGIN:VEVENT
CLASS:PUBLIC
CREATED:20240425T033157Z
DESCRIPTION:\nANZAC Day\n\n \nA day commemorated by Australia and New Zeala
	nd annually.\n \n
DTEND;VALUE=DATE:20240426
DTSTAMP:20240425T033157Z
DTSTART;VALUE=DATE:20240425
LAST-MODIFIED:20240425T033157Z
PRIORITY:5
RRULE:FREQ=YEARLY;BYMONTHDAY=25;BYMONTH=4
SEQUENCE:0
SUMMARY;LANGUAGE=en-au:ANZAC Day
TRANSP:TRANSPARENT
UID:040000008200E00074C5B7101A82E0080000000010A1FEB41397DA01000000000000000
	0100000002DBB4EBD00123A499618C95F359229E7
X-ALT-DESC;FMTTYPE=text/html:<html xmlns:v="urn:schemas-microsoft-com:vml" 
	xmlns:o="urn:schemas-microsoft-com:office:office" xmlns:w="urn:schemas-mic
	rosoft-com:office:word" xmlns:m="http://schemas.microsoft.com/office/2004/
	12/omml" xmlns="http://www.w3.org/TR/REC-html40"><head><meta name=ProgId c
	ontent=Word.Document><meta name=Generator content="Microsoft Word 15"><met
	a name=Originator content="Microsoft Word 15"><link rel=File-List href="ci
	d:filelist.xml@01DA9713.ECFDA6B0"><!--[if gte mso 9]><xml>\n<o:OfficeDocum
	entSettings>\n<o:AllowPNG/>\n</o:OfficeDocumentSettings>\n</xml><![endif]-
    [...SNIP...]
	36.0pt\;word-wrap:break-word'><div class=WordSection1><h1><span style='mso
	-fareast-font-family:Calibri'>ANZAC Day<o:p></o:p></span></h1><p class=Mso
	Normal><o:p>&nbsp\;</o:p></p><p class=MsoNormal>A day commemorated by Aust
	ralia and New Zealand annually.<o:p></o:p></p><p class=MsoNormal><o:p>&nbs
	p\;</o:p></p></div></body></html>
X-MICROSOFT-CDO-BUSYSTATUS:FREE
X-MICROSOFT-CDO-IMPORTANCE:1
X-MICROSOFT-DISALLOW-COUNTER:FALSE
X-MS-OLK-CONFTYPE:0
END:VEVENT
END:VCALENDAR

```

## Typing and Metadata

TBD.

## Linking

TBD.

## Publishing

TBD.

