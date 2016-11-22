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
### List a particular vendor's organizations
`
GET /organizations HTTP/1.1
Content-Type: application/json
x-token: pri-ec8a83df297021dca0c43fc854f98a061370325def180a125189c087abc6448735ba21679d4b26d17eca4ba31f5170f5653b19cf363e16e413417c6b7469cdce
x-id: vendor-7c5c73b3-81e8-418f-891b-db1b4bb7d064
`

(response is an array of organizations)

### List all lines for a given organization without being logged in
```
GET /lines HTTP/1.1
Content-Type: application/json
x-token: pri-3f0e8eb2e26a1a9966f4f0d3ab8a92bb7b103467dbd1371ca26e5ba5a92644b553bf366054d9006022cacb4be414008859a69a80b352e3546b3af0bdb506888a
x-id: org-f1594bd7-7999-4dd9-8007-394dcb7c4af3
```

(response is an array of lines for that organization)
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
