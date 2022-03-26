# Laravel Cheat Sheets

**Table of Contents:**
* [Installation](/laravel/installation.md)
    * [Requirements](/laravel/installation.md#requirements)
    * [Installation Guide](/laravel/installation.md#installation-guide)
    
* [Starting a new Project](/laravel/starting%20a%20new%20project.md)
    * [Create Laravel Project](/laravel/starting%20a%20new%20project.md#create-laravel-project)
    * [Preset Front-End (Vue & Bootstrap)](/laravel/starting%20a%20new%20project.md#preset-front-end-vue--bootstrap)

* [Tips & Tricks](/laravel/tips%20%26%20tricks.md)
    * [Accessors & Mutators](/laravel/tips%20%26%20tricks.md#accessors--mutators)
    * [Flashing data into Session](/laravel/tips%20%26%20tricks.md#flashing-data-into-session)
    * [Get Back Route as URL](/laravel/tips%20%26%20tricks.md#get-back-route-as-url)
    * [Make a state in factory](/laravel/tips%20%26%20tricks.md#make-a-state-in-factory)
    * [Force HTTPS Scheme](/laravel/tips%20%26%20tricks.md#force-https-scheme)
    * [Dynamic Page Titles](/laravel/tips%20%26%20tricks.md#dynamic-page-titles)
    * [Sending Requests using GuzzleHttp](/laravel/tips%20%26%20tricks.md#sending-requests-using-guzzlehttp)
    * [Getting Values from environment file](/laravel/tips%20%26%20tricks.md#getting-values-from-environment-file)
    * [Adding a fav icon](/laravel/tips%20%26%20tricks.md#adding-a-fav-icon)
    * [Activating Verification](/laravel/tips%20%26%20tricks.md#activating-verification)

* [Database Tricks](/laravel/database%20tricks.md)
    * [Adding Foreign ID to tables](/laravel/database%20tricks.md#adding-foreign-id-to-tables)
    * [Making Pivot Tables](/laravel/database%20tricks.md#making-pivot-tables)
    * [Many To Many with data](/laravel/database%20tricks.md#many-to-many-with-data)

* [Intervention-Image](/laravel/intervention-image.md)
    * [Installation](/laravel/intervention-image.md#installation)
    * [Usage](/laravel/intervention-image.md#usage)
    
* [Dealing with Policies](/laravel/dealing%20with%20policies.md)
    * [Creating a Policy](/laravel/dealing%20with%20policies.md#creating-a-policy)
    * [Dealing with Policy](/laravel/dealing%20with%20policies.md#dealing-with-policy)
    * [Guest Approach (Null User) in Policies](/laravel/dealing%20with%20policies.md#guest-approach-null-user-in-policies)

* [Events & Listeners](/laravel/events%20%26%20listners.md)
    * [Events](/laravel/events%20%26%20listners.md#events)
    * [Listners](/laravel/events%20%26%20listners.md#listners)
    * [Attaching Event to Listners](/laravel/events%20%26%20listners.md#attaching-event-to-listners)
    * [Generating Events & Listeners](/laravel/events%20%26%20listners.md#generating-events--listeners)

* [Blade](/laravel/blade.md)
    * [Blade Templates](/laravel/blade.md#blade-templates)
    * [Including Views](/laravel/blade.md#including-views)
    * [Echoing](/laravel/blade.md#echoing)

* [Pagination](/laravel/pagination.md)
    * [Auto-Magic Pagination](/laravel/pagination.md#auto-magic-pagination)
    * [Adding Navigators Automatically](/laravel/pagination.md#adding-navigators-automatically)
    * [Adding Navigators Manually](/laravel/pagination.md#adding-navigators-manually)
    * [Paginator Methods Table](/laravel/pagination.md#pagination)

* [Deploying on Heroku](/laravel/deploying%20on%20heroku.md)
    * [Requirements](/laravel/deploying%20on%20heroku.md#requirements)
    * [Deploying](/laravel/deploying%20on%20heroku.md#deploying)
    * [Notes](/laravel/deploying%20on%20heroku.md#notes)

* [Queuing Jobs](/laravel/queuing%20jobs.md)
    * [Making class a Queueable Job](/laravel/queuing%20jobs.md#making-class-a-queueable-job)
    * [Setting Queue Connection](/laravel/queuing%20jobs.md#setting-queue-connection)
    * [Chosing Queue Drivers](/laravel/queuing%20jobs.md#chosing-queue-drivers)
    * [Using database Driver](/laravel/queuing%20jobs.md#using-database-driver)
    * [Processing Jobs](/laravel/queuing%20jobs.md#processing-jobs)
    * [Dealing with workers in command line](/laravel/queuing%20jobs.md#dealing-with-workers-in-command-line)

* [Meilisearch](/laravel/meilisearch.md)
    * [Installing Meilisearch to project](/laravel/meilisearch.md#installing-meilisearch-to-project)
    * [Dealing with Meilisearch](/laravel/meilisearch.md#dealing-with-meilisearch)

* [Laravel Telescope](/laravel/telescope.md)
    * [Installation](/laravel/telescope.md#insatallation)
    * [Dashboard Authorization](/laravel/telescope.md#dashboard-authorization)

* [Artisan Commands](/laravel/artisan%20commands.md)
    * [Generate Application Key](/laravel/artisan%20commands.md#generate-application-key)
    * [Dealing with Routes in Artisan](/laravel/artisan%20commands.md#dealing-with-routes-in-artisan)
    * [Artisan serve command](/laravel/artisan%20commands.md#artisan-serve-command)
    * [Artisan tinker command](/laravel/artisan%20commands.md#artisan-tinker-command)
    * [Maintenance Mode](/laravel/artisan%20commands.md#maintenance-mode)
    * [Creating Objects](/laravel/artisan%20commands.md#creating-objects)
    * [Dealing with Migrations](/laravel/artisan%20commands.md#dealing-with-migrations)
    * [Making new artisan command](/laravel/artisan%20commands.md#making-new-artisan-command)

* [Cookies](/laravel/cookies.md)
    * [Creating cookies](/laravel/cookies.md#creating-cookies)
    * [Getting Cookie value](/laravel/cookies.md#getting-cookie-value)
    * [Removing a cookie](/laravel/cookies.md#removing-a-cookie)

* [Redirecting - Requests & Responses](/laravel/redirecting%20-%20requests%20%26%20responses.md)
    * [Redirecting](/laravel/redirecting%20-%20requests%20%26%20responses.md#redirecting)
    * [Requests](/laravel/redirecting%20-%20requests%20%26%20responses.md#requsets)
    * [Responses](/laravel/redirecting%20-%20requests%20%26%20responses.md#responses)

* [Hashing & Encryption](/laravel/hashing%20%26%20encryption.md)
    * [Hashing](/laravel/hashing%20%26%20encryption.md#hashing)
    * [Encryption](/laravel/hashing%20%26%20encryption.md#encryption)

* [Authentication](/laravel/authentication.md)
    * [Dealing with Authenticated user](/laravel/authentication.md#dealing-with-authenticated-user)
    * [Login & Logut](/laravel/authentication.md#login--logut)