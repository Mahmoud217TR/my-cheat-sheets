## Authentication

**Table of Contents:**
* [Dealing with Authenticated user](#dealing-with-authenticated-user)
* [Login & Logut](#login--logut)


## Dealing with Authenticated user

To Deal with the authenticated user:

```php
Auth::check();  // Determine if the current user is authenticated
Auth::user();   // Get the currently authenticated user
Auth::id();     // Get the ID of the currently authenticated user
```

## Login & Logut

For Login & Logout:

```php
Auth::attempt(array('email' => $email, 'password' => $password)); // Attempt to authenticate a user using the given credentials

Auth::attempt($credentials, true); // 'Remember me' by passing true to Auth::attempt()

Auth::once($credentials);   // Log in for a single request

Auth::login(User::find(1)); // Log a user into the application
Auth::loginUsingId(1);      // Log the given user ID into the application

Auth::logout();  // Log the user out of the application

Auth::validate($credentials);   // Validate a user's credentials
```