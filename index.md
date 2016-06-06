---
layout: default
---

# Middleware

Express provides [middleware](http://expressjs.com/en/guide/using-middleware.html) to configure how it handles HTTP requests.

You can use middleware for adding Authentication and Authorization to your application.

## Authentication

You can use middleware to do the following:

* Check if the user is Authenticated;
* if the user is not Authenticated, redirect the user to the `login` route;
* check what roles are assigned to a user;
* block access to routes a user's role don't have access to.

The `login` route should:

* Capture the user's credentials;
* check if the user's credentials are valid;
* store the right information in the HTTP Session.

## Authorization

Web applications needs a way of knowing which users are logged into the system and what these users can do. Authentication is the process of getting to know a user. This normally involves a username and a password. Authorization is the process of checking what a user can do once they are Authenticated in the system.

Functionality in a system is normally assigned to roles, with roles being assigned to users.

A user is identified as they log into the system. Once a identified, the system knows which roles are assigned to the user. The system use these roles to decide what a user can do.
