# Organizations
## Business Hours
When an organization is created, 7 associated business hour records will be created, one for each day of the week.  They will look basically like this:

```
{
  "id": "d68f1fcf-25a3-4967-be3e-686b9ef213cc",
  "day": 3,
  "open": true,
  "opens": "08:00:00",
  "closes": "17:00:00",
  "organizationId": "bb236800-ef7d-49fc-b04d-c3c689223994"
},
```

*day* refers to the 0 indexed day of the week.  *opens* and *closes* are HH:MM:SS (or HH:MM, either one is fine) formatted 24-hour times.

*Future support note:* support for blocking out certain days (e.g., holidays) will eventually be added, if needed.

## organization.customInformation

This is a plain object; however, there's some custom information that can be used here.

### Custom Links
*customInformation.reservationLink*: If set, this is the base URL that will be used for "click here to reserve" type links in notifications.
*customInformation.unsubscribeLink*: same as above, only for unsubscribing.

Each link will have `?token=TOKEN appended` (or `&token=TOKEN` if there are already query parameters in the link).  The token can be interacted with via `/tokens` endpoints to do the appropriate thing.
