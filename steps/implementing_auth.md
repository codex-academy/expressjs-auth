---
layout: default
---

# Implementing your own Authentication

Once your server supports HTTP Sessions and you understand the basics of Express middleware you can start thinking of how to implement some user Authentication & Authorization.

So let's start simple. Create a simple Authentication system that:

* allows a user to login;
* redirects a user to the login screen with a message if their login attempt failed;
* allows a user to login using the username `UserOne` with a password of `thereWeG0`;
* allows the user to logout.

Let's extend that to a system that:

* allows a user to login;
* redirects a user back to the login screen with a message if their login attempt failed;
* allows a user to register. Use an in memory store: if the server is restarted the credentials will be gone.

Now for a more advanced implementation. Let's extend the system again to one that:

* allows user to login;
* redirects a user back to the login screen with a message if their login attempt failed;
* allows a user to register:
    * stores user details in a database;
    * encrypts the user's password. Tip: look at [the bcrypt module](https://www.npmjs.com/package/bcrypt-nodejs) in npm.
* locks the users account if they supply the wrong password 3 times in a row;
* allows a user to logout.

Once you have mastered the above you should have a good understanding of how the Authentication process works. How do you think you should handle the Authorization process?
