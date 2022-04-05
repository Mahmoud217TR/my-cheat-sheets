# Laravel Tips & Tricks

**Table of Contents:**
* [Accessors & Mutators](#accessors--mutators)
* [Flashing data into Session](#flashing-data-into-session)
* [Get Back Route as URL](#get-back-route-as-url)
* [Make a state in factory](#make-a-state-in-factory)
* [Force HTTPS Scheme](#force-https-scheme)
* [Dynamic Page Titles](#dynamic-page-titles)
* [Sending Requests using GuzzleHttp](#sending-requests-using-guzzlehttp)
* [Getting Values from environment file](#getting-values-from-environment-file)
* [Adding a fav icon](#adding-a-fav-icon)
* [Activating Verification](#activating-verification)


## Accessors & Mutators

Assume we have 4 states for `User` Model (Active, Inactive, Suspended, Banned):

```php
// In User Migration

$table->unsignedBigInteger('state'); // assuming the states are (0, 1, 2, 3)


// In User Model

// To ease getting states 
public static function states(){
    return [
        0 => 'Active',
        1 => 'Inactive',
        2 => 'Suspended',
        3 => 'Banned'
    ];
}

// The Accessor & Mutator
public function state(): Attribute{
    return Attribute::make(
        get: fn ($value) => $this->states()[$value],
        set: fn ($value) => array_search($value,$this->states()),
    );
}

// Any where in app
User::states();             // returns all User states as text (Active, Inactive, Suspended, Banned)
$user->state = 'Inactive';  // Uesr's state becomes 1 in database (Inactive)
$user->state;               // returns the current user state as text ('Inactive')
```


## Flashing data into Session

To flash some data in session:

```php
session()->flash('key','value');

// Dealing with it in the app
session()->has('key')
session()->get('key')
```

## Makin your own helper functions

1. Create `helpers.php` file inside app folder.

2. Write this code inside `helpers.php` file:

    ```php
    <?php
    if (!function_exists('function_name')) {
		function function_name($params){ 
			// your code
		} 
	} 
    ?>
    ```

3. In `composer.json` file put this in autoload block:

    ```json
    "autoload" : {
			"files" : [
				"app/helpers.php"
			]
		}
    ```

4. Run `composer dump-autoload`.


## Get Back Route as URL

If you want to get the back route as url use:
```php
back()->getTargetUrl()
```


## Make a state in factory

To make a state in `Profile` Model factory for example write this:

```php
// In Profile factory
public function withoutUser(){
    return $this->state(function (array $attributes) {
        return [
            'user_id' => null,
        ];
    });
}

// To use it
Profile::factory()->withoutUser()->make();
```


## Force HTTPS Scheme

To force https scheme on **production** put the following code in the `boot` method at `app\Providers\AppServiceProvider`:
```php
	if(config('app.env') === 'production') { // if app in production only
        \URL::forceScheme('https');
    }
```


## Dynamic Page Titles

To make the page title dynamic use this in `app.blade.view`:

```blade
<title>@yield('title',config('app.name', 'Laravel'))</title>
```

In the pages use:

```blade
@extends('app')
@section('title','Page Title')
```


## Sending Requests using GuzzleHttp

To send requests to an external API `https://api.example.com/action` for example use [Guzzle](https://docs.guzzlephp.org/en/latest/overview.html):

```php
use GuzzleHttp\Client;
use GuzzleHttp\Psr7\Request as GuzzleRequest;

public function sendRequest(){

    $client = new Client(['verify' => false]); // ['verify' => false] For HTTP

    $method = 'GET';
    $uri = 'https://api.example.com/action';
    $headers = ['Content-Type' => 'application/json','Accept' => 'application/json'];
    $body = json_encode(['key' => 'value']);

    $request = new GuzzleRequest($method,$uri,$headers,$body);
    $response = $client->send($request);

    // Checking response
    echo $response->getStatusCode(); // if everything works should return 200
    echo $response->getBody();
}
```

For a **Cleaner** code and **Better** Practice:

```php
use GuzzleHttp\Client;
use GuzzleHttp\Psr7\Request as GuzzleRequest;

private function sendRequest($method,$uri,$headers,$body){
    $client = new Client(['verify' => false]); // ['verify' => false] For HTTP
    $request = new GuzzleRequest($method,$uri,$headers,$body);
    return $client->send($request);
}

public function testing(){

    $method = 'GET';
    $uri = 'https://api.example.com/action';
    $headers = ['Content-Type' => 'application/json','Accept' => 'application/json'];
    $body = json_encode(['key' => 'value']);
    
    $response = $this->sendRequest($method,$uri,$headers,$body);

    // Checking response
    echo $response->getStatusCode(); // if everything works should return 200
    echo $response->getBody();
}
```

## Getting Values from environment file

Let's say the `.env` file looks like this:

```
SOME_CUSTOM_KEY = 10
```

To get a value of `SOME_CUSTOM_KEY`:

```php
echo env('SOME_CUSTOM_KEY') // prints 10
```

## Adding a fav icon

If you want to add a fav icon to your website:

- make the logo in `ico` format for example make the file name is `logo.ico`.
- put the `.ico` in `public/images` folder.
- put this in the header:

    ```blade
    <link rel="shortcut icon" href="{{ asset('images/logo.ico') }}" type="image/x-icon">
    ```


## Activating Verification

To activate `User` Model Verification:

1. The `User` Model should implement the `MustVerifyEmail` interface:

    ```php
    class User extends Authenticatable implements MustVerifyEmail
    ```

2. In the `web.php` file:

    ```php
    Auth::routes(['verify' => true]);
    ```

3. Setup the mail services.

4. Add the Middleware `verified`.