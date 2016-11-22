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

## Searching
All models allow for direct attributes to be searched in a `value == lookup` sort of way; e.g., `/users?email=johndoe@example.com`
