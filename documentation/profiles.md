# Profiles
## profile.information
This is where the bulk of information stored in a profile will be kept.  Some probable information would be:

* information.age
* information.name
* information.birthdate
* information.gender

etc.

Because the Next In Line API is not specific to any business type, this data may change significantly.

### Searching
You can search the `.information` attribute using query parameters, e.g.: `/profiles?information.name=John Doe`.

By default, the operator for the comparision will be `=`.  If you want to change this, you can prefix your parameter with `operator:`, e.g.: `/profiles?information.name==~:John` will find all profiles where the name contains John (due to the `=~` operator).
