---
layout: default
---

# HTTP Sessions

HTTP is a stateless protocol. To store user information we need a way of managing state when using HTTP, that's what HTTP Sessions are for.

HTTP sessions use a combination of client side and server side storage. It uses [cookies](https://www.nczonline.net/blog/2009/05/05/http-cookies-explained/) to store small pieces of information on the client side and it stores the session data in files on disk or in a database on the server side.

Cookies contain tokens/values that can be associated with the HTTP request data stored on the server. Cookies have an expiry time. This allows for HTTP Sessions to expire: after a predetermined time a user will need to log in again.

## Set up a session

To add HTTP Sessions to your ExpressJS Server you need to install the [express-session package](https://www.npmjs.com/package/express-session). This adds a `session` method to the `req` object like this: `req.session`.

Create simple ExpressJS app and add configuration like this:

```javascript
var session = require('express-session');

//set up http session middleware
app.use(session({
    secret: 'put your secret phrase here please',
    cookie: { maxAge: 60000 }
}));

//init the session in one route
app.get("/login", function(req, res){
    const currentUsername = req.query.username;
    // req.session will be defined now
    if (currentUsername && !req.session.username){
        //set a session value from a form variable
        req.session.username = currentUsername;
    }
    res.redirect('/');
});

app.get('/', function(req, res){
    let greeting = "Hello";
    if (req.session.username) {
        greeting += (", " + req.session.username);
    }
    res.send(greeting);
});
```

### Test the app using a http session

First go to the `/` route - you should just see `Hello`.

Now 'login' using the `/login` route like this `/login?username=Lindani`. This should redirect to the `/` route which will now display `Hello Lindani`.

If you refresh the '/' route you will still see `Hello Lindani` - as the value for `user` stored in the session is `Lindani`.

You can change the value for user in the session by running - `/login?username=<Any other name here>`

You can also create a logout route that deletes the user from the session like this.

```javascript
app.get('/logout', function(req, res){
    delete req.session.user;
    res.redirect('/');
});
```

Try this and see what happens.






