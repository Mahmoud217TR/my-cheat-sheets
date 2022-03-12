# Redirecting - Requests & Responses

**Table of Contents:**
* [Redirecting](#redirecting)
* [Requests](#requsets)
* [Responses](#responses)


## Redirecting

To Redirect to a URL:

```php
return Redirect::to('url');
return Redirect::to('url')->with('key', 'value'); // Passing Data
```

To Redirect to a Route:

```php 
return Redirect::route('route.name'));
return Redirect::route('route.name',compact('data'))); // Passing Data
```

To Redirect to the previous location:

```php
return Redirect::back();
```

To Redirect to a Controller called `Controller` action called `action` for example:

```php
return Redirect::action('Controller::action');
return Redirect::action('Controller::action', compact('data')); // Passing Data
```


## Requsets

To get a Request URL/Path/URI for example the url is `http://app.example/a/b`:

```php
Request::url(); // returns "http://app.example/a/b"
Request::path(); // returns "/a/b"
Request::getRequestUri(); // returns "/a/b/?c=d"
```

To get Request parameters:

```php
request()->all();
```


## Responses

To make a Response:

```php
return Response::make($data);   // returns response with data
return Response::make($data, 200); // returns response with data & status of 200
return Response::json($data); // returns response with json data
```

To make a Response with Download link to a file:

```php
return Response::download($filepath);
return Response::download($filepath, $filename);
```
