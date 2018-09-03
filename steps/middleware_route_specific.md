---
layout: default
---

# Route specific middleware

Route specific middleware allows you to add middleware components onto routes.

```javascript
var checkUser = function(req, res, next){
  if (req.session.user){
      // calling the next function - just proceeds to the route.
      return next();
  }
  // the user is not logged in redirect them to the login page
  res.redirect('/login');
};

app.get('/users', checkUser, function(req, res){
  // use the username in the session the find the user detail
  var userData = userService.getUserData(req.session.user);
  res.render('user', userData)
});
```
