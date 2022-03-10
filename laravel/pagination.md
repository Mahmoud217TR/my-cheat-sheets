# Pagination

**Table of Contents:**
* [Auto-Magic Pagination](#auto-magic-pagination)
* [Adding Navigators Automatically](#adding-navigators-automatically)
* [Adding Navigators Manually](#adding-navigators-manually)
* [Paginator Methods Table](#pagination)

## Auto-Magic Pagination

To Make an automatic pagination for model called `Model` for example:
    
```php
Model::paginate(10);
Model::all()->paginate(10);
```

> Each page will contain **10** Models.

## Adding Navigators Automatically

- If you want to add the `Next` & `Previous` navigators:

    ```php
    $model = Model::simplePaginate(10);
    ```

- To display the navigators in the view:
    
    ```blade
    {{ $model->links(); }}
    ```

## Adding Navigators Manually

- It's **Recommended** to use the `paginate` method:

    ```php
    $model = Model::paginate(10); 
    ```

- In the view:

    ```blade
        <!-- Previous link -->
        @if($model->currentPage() > 1)
        <a href="$model->previousPageUrl()">Previous</a>
        @endif

        <!-- Current Page Number -->
        <span> {{ $model->currentPage() }} </span>

        <!-- Next link -->
        @if($model->hasMorePages())
        <a href="$model->nextPageUrl()">Next</a>
        @endif
    ```


## Paginator Methods Table

|Method | Description|
--------|-----------
|`$paginator->count()` | Get the number of items for the current page|
|`$paginator->currentPage()` | Get the current page number|
|`$paginator->hasMorePages()` | Determine if there are more items in the data store|
|`$paginator->items()` | Get the items for the current page|
|`$paginator->firstItem()` | Get the result number of the first item in the results|
|`$paginator->lastItem()` | Get the result number of the last item in the results|
|`$paginator->nextPageUrl()` | Get the URL for the next page|
|`$paginator->previousPageUrl()` | Get the URL for the previous page|
|`$paginator->url($page)` | Get the URL for a given page number|