---
layout: default
---

# HTTP Sessions

HTTP is a stateless protocol, to store user session information one needs a way of managing state when using it. HTTP Sessions are used for that.

HTTP sessions use a combination of client side and server side storage. It use [Cookies](https://www.nczonline.net/blog/2009/05/05/http-cookies-explained/) to store small pieces of information on a user's PC. Server side the session data are stored in files on disk or in a database.

Cookies contains an token/values that are used associate the HTTP request data stored on the server. Cookies have an expiry time, this allows for HTTP Sessions to expire. The HTTP Session will expire after a predetermined time and a user will need to login again.

## Setup a session:

To add HTTP Sessions to your ExpressJS Server you need to install the [express-session package](https://www.npmjs.com/package/express-session).

Add configuration like this:

```javascript

var session = require('express-session');

//setup HttpSession middleware
app.use(session({
    secret: 'put your secret phrase here please',
    cookie: { maxAge: 60000 }
}));

//in a route Now
app.get("/my-route", function(req, res){
    // req.session - will be defined now...
    if (!req.session.user){
        //set a session value from a form variable
        req.session.user = req.body.username;
    }
});
```
