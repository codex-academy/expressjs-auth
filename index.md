---
layout: default
---

# Middleware

ExpressJS provides [middleware](http://expressjs.com/en/guide/using-middleware.html) to configure how it handles HTTP requests. You can use middleware to run code, to make changes to the request and the response objects, and more. We'll use it to add Authentication and Authorization to your application.

Web applications need a way of knowing which users are logged into the system and what these users can do. **Authentication** is the process of getting to know a user; this normally involves a username and a password. **Authorization** is the process of checking what a user can do once they are Authenticated in the system.

## Authentication

You can use middleware to do the following:

* Check if the user is Authenticated;
* if the user is not Authenticated, redirect the user to the `login` route;
* check what roles are assigned to a user;
* block access to routes a user's role don't have access to.

The `login` route should:

* Capture the user's credentials;
* check if the user's credentials are valid;
* store the appropriate information in the HTTP Session.

## Authorization

Functionality in a system is normally assigned to roles; roles are assigned to users.

A user is identified as they log into the system. Once they are identified, the system knows which roles are assigned to the user. The system uses these roles to determine what a user can do.
