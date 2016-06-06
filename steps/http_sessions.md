---
layout: default
---

# HTTP Sessions

HTTP is a stateless protocol. To store user session information we need a way of managing state when using it: we'll use HTTP Sessions for this.

HTTP sessions use a combination of client side and server side storage. It uses [cookies](https://www.nczonline.net/blog/2009/05/05/http-cookies-explained/) to store small pieces of information on the client side. It stores the session data in files on disk or in a database on the server side.

Cookies contain tokens/values that are can be associated with the HTTP request data stored on the server. Cookies have an expiry time. This allows for HTTP Sessions to expire: after a predetermined time a user will need to log in again.

## Set up a session

To add HTTP Sessions to your ExpressJS Server you need to install the [express-session package](https://www.npmjs.com/package/express-session). This adds a `session` method to the `req` object like this: `req.session`.

Add configuration like this:

```javascript
var session = require('express-session');

//set up HttpSession middleware
app.use(session({
    secret: 'put your secret phrase here please',
    cookie: { maxAge: 60000 }
}));

//in a route
app.get("/my-route", function(req, res){
    // req.session will be defined now
    if (!req.session.user){
        //set a session value from a form variable
        req.session.user = req.body.username;
    }
});
```
