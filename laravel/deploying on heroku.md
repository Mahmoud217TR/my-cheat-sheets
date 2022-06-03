# Deploying Laravel project on Heroku

**Table of Contents:**
* [Requirements](#requirements)
* [Deploying](#deploying)
* [Notes](#notes)


## Requirements
* [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli#install-the-heroku-cli)


## Deploying

1. Create a file and name it `Procfile` and write the following in it:

    ```
    web: vendor/bin/heroku-php-apache2 public/
    ```

2. Create a Heroku project, use `heroku create 'project name'`.

3. Add Heroku remote repository `git remote add heroku 'repo url'`.

4. Make a commit and push it to the repository:

    ```
    git add .
    git commit -m 'uploading on heroku'
    git push heroku main
    ```

5. Add Config Vars:

    ```
    APP_DEBUG	: 	true
    APP_ENV		: 	production
    APP_KEY		:	FROM '.env' FILE
    APP_NAME	:	YOUR APP NAME
    ```

6. Add `Heroku Postgres` Plugin for database and get credentials, you can use `pg:credentials:url` to get credentials.

7. Add database credentials to Config Vars:

    ```
    DATABASE_URL	    :   FROM CREDENTIALS
    DB_CONNECTION	    :	pgsql
    DB_DATABASE		:   FROM CREDENTIALS
    DB_HOST			:   FROM CREDENTIALS
    DB_PASSWORD		:   FROM CREDENTIALS
    DB_PORT			:   FROM CREDENTIALS
    DB_USERNAME		:   FROM CREDENTIALS
    ```
	
8. Run migrate command `heroku run php artisan migrate`.


## Notes

- If you don't have SSL yet and want to force HTTPS protocol [check this](/laravel/tips%20%26%20tricks.md#force-https-scheme).