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
