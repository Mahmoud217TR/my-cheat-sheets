# Queuing Jobs

**Table of Contents:**
* [Making class a Queueable Job](#making-class-a-queueable-job)
* [Setting Queue Connection](#setting-queue-connection)
* [Chosing Queue Drivers](#chosing-queue-drivers)
* [Using database Driver](#using-database-driver)
* [Processing Jobs](#processing-jobs)
* [Dealing with workers in command line](#dealing-with-workers-in-command-line)


## Making class a Queueable Job

To make a Job Queueable implement the interface `ShouldQueue`.


## Setting Queue Connection

To set a queue connection go to your `.env` file and change the value of `QUEUE_CONNECTION` from `sync` to your driver.


## Chosing Queue Drivers

To check avalible queue drivers open `app\config\queue.php` file, you will see them listed in a comment like this:

```php
/*
|--------------------------------------------------------------------------
| Queue Connections
|--------------------------------------------------------------------------
|
| Here you may configure the connection information for each server that
| is used by your application. A default configuration has been added
| for each back-end shipped with Laravel. You are free to add more.
|
| Drivers: "sync", "database", "beanstalkd", "sqs", "redis", "null"
|
*/
```

As a recommendation for queue driver use:
- `database` driver for **Development**.
- `redis` driver for **Production**.


As a recommendation for queue worker use:
- `queue:work` for **Development**.
- `Supervisor` for **Production**.


## Using database Driver

1. Open `.env` file and change the value of `QUEUE_CONNECTION` from `sync` to `database`.
2. Make a queue migration by using `php artisan queue:table` and migrate the database.


## Processing Jobs

To Start processing jobs on the queue as a daemon:

```
php artisan queue:work
```

## Dealing with workers in command line

* To run Laravel worker in the background just add `&` at the end of the command:

    ```
    php artisan queue work &
    ```

* To close Laravel Worker in the background use the command `kill <worker_pid>`.

* To display workers use the command `jobs`.

* To display workers with there PID use the command `jobs -l`.

* To log the worker output to a file while running in the background use:

    ```
    php artisan queue:work > file.log &
    ```