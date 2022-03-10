# Artisan Commands

**Table of Contents:**
* [Generate Application Key](#generate-application-key)
* [Dealing with Routes in Artisan](#dealing-with-routes-in-artisan)
* [Artisan serve command](#artisan-serve-command)
* [Artisan tinker command](#artisan-tinker-command)
* [Maintenance Mode](#maintenance-mode)
* [Creating Objects](#creating-objects)
* [Dealing with Migrations](#dealing-with-migrations)


## Generate Application Key

To set the application key use `php artisan key:generate`.

## Dealing with Routes in Artisan

To deal with routes with `artisan` command:

```
// List all registered routes
php artisan route:list

// Create a route cache file for faster route registration
php artisan route:cache

// Remove the route cache file
php artisan route:clear
```


## Artisan serve command

- To Change the default port to `8080` for example use `php artisan serve --port 8080`.
- To get it to work outside localhost for example on `0.0.0.0` host use `php artisan serve --host 0.0.0.0`.


## Artisan tinker command

To Interact with your application use `php artisan tinker`.


## Maintenance Mode

- To put the application into maintenance mode use `php artisan down`.
- To bring the application out of maintenance mode use `php artisan up`.


## Creating Objects

- To create an Eloquent model named called `ModelName` use:

    ```
    php artisan make:model ModelName
    php artisan make:model ModelName -c   // Create a new controller for the model
    php artisan make:model ModelName -f   // Create a new factory for the model
    php artisan make:model ModelName -m   // Create a new migration file for the model
    php artisan make:model ModelName -s   // Create a new seeder for the model
    php artisan make:model ModelName -a   // Generate a migration, seeder, factory, policy, and resource controller for the model
    ```

- To create a Controller called `TestController` use `php artisan make:controller TestController`.

- To create a Middleware called `TestMiddleware` `use php artisan make:middleware TestMiddleware`.

- To create a Policy called `ModelPolicy`for a model called `ModelName` use `php artisan make:policy ModelPolicy -m ModelName`.

- To create a Migration called `test_migration` use `php artisan make:migration test_migration`.


## Dealing with Migrations

- To migrate database use `php artisan migrate`.

- To rollback the last database migration use `php artisan migrate:rollback`.

- To rollback all database migrations use `php artisan migrate:reset`.

- To create database migration use `php artisan migrate:refresh`.

- To show a list of migrations up/down use `php artisan migrate:status`.