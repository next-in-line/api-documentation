# API Documentation for Next In Line
Auto-generated documentation is available at http://api.nextinline.io/docs

## Authentication
Use vendor auth when creating organizations.  Use org auth if you want to act as an org (and not a user).

Headers:
- **x-id:** vendor-xyz or org-xyz
- **x-token:** the associated token with the vendor or org

Use user auth ... most of the time.  :)

Headers:
- **x-user-token:** the *apiToken* attribute of the user.  It is generated on login.
