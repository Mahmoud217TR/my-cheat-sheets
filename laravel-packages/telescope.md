# Laravel Telescope


**Table of Content:**
* [Installation](#insatallation)
* [Dashboard Authorization](#dashboard-authorization)

## Insatallation

To download Laravel Telesccope use one of the following:

```
// For Production and Development
composer require laravel/telescope

// For Development Only
composer require laravel/telescope --dev
```

Then Run the Install command and migrate the new tables:

```
php artisan telescope:install
php artisan migrate
```

## Dashboard Authorization

To make only some types of user allowed to access Laravel Telescope go to `app/Providers/TelescopeServiceProvider.php` there is an authorization gate at the end of the file:

```php
protected function gate()
{
    Gate::define('viewTelescope', function ($user) {
        return in_array($user->email, [
            'admin@users.test',
        ]);
    });
}

```