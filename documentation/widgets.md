# Widgets
## Subscriptions
### Create a subscription token
POST to `/tokens` using the `x-user-token` header with the `.apiToken` of the user you want to create the token for.  Post the following JSON:
`
{
  type: 'subscribe',
  userId: your-user-id
}
`

The API will return a token object that can be used to subscribe this user (and only subscribe, nothing else) to a line.  It can also be used to get the subscription widget.

### Get the widget
GET `/widgets/subscribe?token=12345&organizationId=your-org-id` where `your-org-id` is the organization you want to show lines for.  The widget will allow users to subscribe to any of the lines for that organization.

## Show Organization
### Create a show-organization token
POST to `/tokens` using the `x-user-token` header with the `.apiToken` of the user you want to create the token for.  Post the following JSON:
`
{
  userId: 'some user ID',
  objectId: 'some organization ID',
  action: 'organization-widget'
}
`
The API will return a token object that can be used to show and organization widget and do things such as reserve or subscribe... depending on the widget.

### Get the widget
GET `/widgets/subscribe?token=12345&organizationId=your-org-id` where `your-org-id` is the organization you want to show lines for.  The widget will allow users to subscribe to any of the lines for that organization.

### Widget Functionality
#### "Reserve"
The widget will redirect the "reserve" link to either Next In Line's reservation handler, or your custom one; essentially, as if the user had clicked on an e-mailed link to reserve a spot.

However, one difference between this link and the link in an e-mail is that the token passed does not have the spot ID in it.  The spotID will be a query parameter, e.g.:
https://www.nextinline.io/reserve?token=12345&spotId=abc-def-ghijk
