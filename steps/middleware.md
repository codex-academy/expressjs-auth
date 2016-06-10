---
layout: default
---

# Middleware

Express JS give us access to a concept called middleware where by we can extend the way that it handles HTTP requests from end users.

We want the middleware to do the following:

* Check if the user is Authenticated
* If the user is not Authenticated, redirect the user to the login route

The login routes should:

* Capture the user's credentials;
* check the user's credentials;
* store the appropriate information in the HTTP Session.

To support login for the `/users` route above you would need to put a user Object in the session. For logout you will need to remove the user Object from the session using the `delete` statement.
