# Tokens
If you get a token (e.g., from a callback) that you need to interact with, here's how.  Note that all these actions will cause the token to be used and no longer work.

## Reservation Token
You probably need to get more information from the user (like what profile to use).  What you can do is simply get the token's information (e.g., the user and spot) by simply doing a GET to `/tokens/{tokenID}`.

## Login Token
PUT to `/tokens/{tokenID}`.  You will get the user object back along with an apiToken to use, and that user will be logged in.  This will cause the token to expire.

## Unsubscribe Token
PUT to `/tokens/{tokenID}`.  This will delete unsubscribe the user from whatever line he got a notification from.  This also causes the token to expire.
