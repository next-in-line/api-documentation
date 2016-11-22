# API Documentation for Next In Line
Auto-generated documentation is available at http://api.nextinline.io/docs

# API Authentication
## Description
Use vendor auth when creating organizations.  Use org auth if you want to act as an org (and not a user).

Headers:
- **x-id:** vendor-xyz or org-xyz
- **x-token:** the associated token with the vendor or org

Use user auth ... most of the time.  :)

Headers:
- **x-user-token:** the *apiToken* attribute of the user.  It is generated on login.

## Examples
Getting a list of organizations for a particular vendor:

# Users
## Creating
When creating a user, an initial password is required, even though the field is not actually required.  In the POST to `/users`, make sure to include `password: "somepassword"`

# Organizations Model
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

# Profiles Model
## profile.information
This is where the bulk of information stored in a profile will be kept.  Some probable information would be:

* information.age
* information.name
* information.birthdate
* information.gender

etc.

Because the Next In Line API is not specific to any business type, this data may change significantly.
