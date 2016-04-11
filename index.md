# User role support

## Authentication & Authorization

Web applications needs a way of knowing which users are logged into the system and what these users can do. Authentication is the process of getting to know a user. This normally involves a username and a password. Authorization is the process of checking what a user can do once they are Authenticated in the system.

Functionality in a system is normally assigned to roles, with roles being assigned to users.

A user is identified as they log into the system. Once a identified, the system knows which roles are assigned to the user. The system use these roles to determine what a user can do.


## Resources

Once you understand the Authentication basics you can look into some third party Authentication modules in npm. For example, [Passport JS](http://passportjs.org/docs) supports a wide array of Authentication methods including Google, Facebook, Github, etc.
