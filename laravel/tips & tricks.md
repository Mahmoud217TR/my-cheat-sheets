# Laravel Tips & Tricks

**Table of Contents:**
* [Accessors & Mutators](#accessors--mutators)
* [Model Scopes](#model-scopes)
* [Auto Create Profile when Creating a User](#auto-create-profile-when-creating-a-user)
* [Flashing data into Session](#flashing-data-into-session)
* [Making your own helper functions](#making-your-own-helper-functions)
* [Get Back Route as URL](#get-back-route-as-url)
* [Factory States and Sequneces](#factory-states-and-sequneces)
* [Force HTTPS Scheme](#force-https-scheme)
* [Dynamic Page Titles](#dynamic-page-titles)
* [Sending Requests using GuzzleHttp](#sending-requests-using-guzzlehttp)
* [Getting Values from environment file](#getting-values-from-environment-file)
* [Adding a fav icon](#adding-a-fav-icon)
* [Activating Verification](#activating-verification)
* [Logging Functions](#logging-functions)
* [Ordering by Relationships](#ordering-by-relationships)
* [Grouping by Days](#grouping-by-day)
* [Replicating Models](#replicating-models-in-database)


## Accessors & Mutators

Assume we have 4 states for `User` Model (Active, Inactive, Suspended, Banned):

```php
// In User Migration

$table->unsignedBigInteger('state'); // assuming the states are (0, 1, 2, 3)


// In User Model

// To ease getting states (((((ALWAYS START FROM 1)))))
public static function states(){
    return [
        1 => 'Active',
        2 => 'Inactive',
        3 => 'Suspended',
        4 => 'Banned'
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


## Model Scopes

If you have a `Post` model for example and it has 2 states (Draft => 1, Published => 2) you can declare scopes:

```php
// In the Post Model
public function scopeDraft($query){
    return $query->where('state','1');
}

public function scopePublished($query){
    return $query->where('state','2');
}

// In the App
Post::Published()->get(); // get published posts
Post::Draft()->get(); // get draft posts
```


## Auto Create Profile when Creating a User

Assume we have a `Profile` model that is created when ever a `User` is registered, use the `booted` method:

```php
protected static function booted()
{
    static::created(function ($user) {
        $user->profile()->save(new Profile);
    });
}
```


## Flashing data into Session

To flash some data in session:

```php
session()->flash('key','value');

// Dealing with it in the app
session()->has('key')
session()->get('key')
```

## Making your own helper functions

1. Create `helpers.php` file inside app folder.

2. Write this code inside `helpers.php` file:

    ```php
    <?php
    if (!function_exists('function_name')) {
		function function_name($params){ 
			// your code
		} 
	} 
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


## Factory States and Sequneces

To make a state in `Post` Model factory for example write this:

```php
// In Post factory
public function withoutUser(){
    return $this->state(function (array $attributes) {
        return [
            'user_id' => null,
        ];
    });
}

// To use it
Post::factory()->withoutUser()->make();
```

To make a Sequneces as `Post` model belongs to an existing `User` model:

```php
// In Post factory
public function forExistingUser(){
    return $this->state(new Sequence(fn ($sequence) =>['user_id' => User::all()->random()]));
}

// To use it
Post::factory()->forExistingUser()->make()
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


## Logging Functions

To log for example in database seeder:

```php
$this->command->info('Info');
$this->command->warn('Warning');
$this->command->error('Error');
```


## Ordering by Relationships

To Order a `Post` models by their comments count for example:

```php
$posts = Post::withCount('comments')->orderBy('comments_count', 'desc')->get();
```


## Grouping by Day

To get `Log` model grouped by **Day** using `created_date` attribute for example:

```php
Log::all()->groupBy(function($log){
    return $log->created_at->format('d-m-y');;
})
```

If you want it to be sorted by latest also:

```php
Log::orderBy('created_at','DESC')->get()->groupBy(function($log){
    return $log->created_at->format('d-m-y');;
})

// Better Code
Log::latest()->get()->groupBy(function($log){
    return $log->created_at->format('d-m-y');;
})
```


## Replicating Models in Database

If you want to replicate a model in the database with **new id & timestamps**, for example we want to replicate a `Post` model which has the id of 1:

```php
Post::find(1)->replicate()->save()
```
