# restful_user_registration v2
A fork of droath/restful_user_registration, updated for RESTful v2.

This module creates a user registration resource & endpoint for the Drupal RESTful module.

It uses the guts of the Services module's user registration function, but modified to work within the context of RESTful resources.

It accepts user name, password, & e-mail address, JSON encoded in the body of a POST request to the <restful_api_path>/user-registration endpoint. For example: https://example.org/api/user-registration. Like so:

```json
{
  "name":"<some_name>",
  "pass":"<some_password>",
  "mail":"<some_email>"
}
```

Error messages from Drupal will be captured & returned by RESTful as field errors, like this:

```json
"errors": {
    "name": [
      "The name Orgiastic Clambake is already taken."
    ],
    "mail": [
      "The e-mail address don't.throw.your.shuriken@me.ninja is already registered. Have you forgotten your password?"
    ]
  }
  ```
  
  On success it returns the UID.
  
  Whatever Drupal does when registering through Services should also be done automatically when registering through this resource, such as sending welcome e-mails, etc.
