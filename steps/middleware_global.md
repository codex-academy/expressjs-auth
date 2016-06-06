---
layout: default
---

# Global middleware

A global middleware component will execute for each request to your ExpressJS server.

To create a new middleware component add this configuration:

```javascript
app.use(function(req, res, next){
  console.log('in my middleware!');
  //proceed to the next middleware component
  next();
});
```

This middleware component doesn't do much: it only logs a message to the console.

## Using middleware

If you extend the middleware to check your HttpSession you can use it can use it for system Authentication.

```javascript
app.use(function(req, res, next){
  console.log('in my middleware!');

  // the user is not going to the login screen
  if (req.path != "/login"){
      //is the user not logged in?
      if (!req.session.username ){
          // redirects to the login screen
          return res.redirect("/login");
      }
  }

  //proceed to the next middleware component
  next();
});
```

## Logout

To logout we need to remove the username from the HttpSession.

In a `/logout` route, you can remove the username from the HttpSession using code like this:

```javascript
delete req.session.username
```
