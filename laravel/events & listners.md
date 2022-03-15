# Events & Listeners

**Table of Contents:**
* [Events](#events)
* [Listners](#listners)
* [Attaching Event to Listners](#attaching-event-to-listners)
* [Generating Events & Listeners](#generating-events--listeners)


## Events

To Create an event called `NewEvent` for example use:

```
php artisan make:event NewEvent
```

To fire the previous event:

```php
event(new NewEvent());
```


## Listners

To create a listner called `NewListner` for example use:

```
php artisan make:listner NewListner
```


## Attaching Event to Listners

To attach an event called `NewEvent` to a multiple listners called `NewListener1`, `NewListener2`, `NewListener3` for example, open your `app\Providers\EventServiceProvider` and modify the protected property `listen` to look like this:

```php
protected $listen = [
    NewEvent::class => [
        NewListener1::class,
        NewListener2::class,
        NewListener3::class,
    ],
];
```


## Generating Events & Listeners

If you modify the file `app\Providers\EventServiceProvider` and attached some event to listners that one of them or both of them are not made up yet you can generate them by using:

```
php artisan event:generate
```