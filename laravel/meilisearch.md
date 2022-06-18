# Meilisearch

**Table of Contents:**
* [Installing Meilisearch to project](#installing-meilisearch-to-project)
* [Dealing with Meilisearch](#dealing-with-meilisearch)
	* [To Search a Model](#to-search-a-model)
	* [To Import a Model](#to-import-a-model)
	* [To Flush a Model](#to-flush-a-model)
	* [To chose what to search with](#to-chose-what-to-search-with)
	* [To allow search only on some status with](#to-allow-search-only-on-some-status-with)

## Installing Meilisearch to project
1. Install Laravel Scout `composer require laravel/scout`
		
2. Install MeiliSearch PHP Driver `composer require meilisearch/meilisearch-php http-interop/http-factory-guzzle`
		
3. Publish Scout Configuration `php artisan vendor:publish --provider="Laravel\Scout\ScoutServiceProvider"`
		
4. Update `.env` Configuration File:
	```
	SCOUT_DRIVER=meilisearch
	MEILISEARCH_HOST=http://127.0.0.1:7700
	MEILISEARCH_KEY=
	```

5. Add Searchable Trait to Your Model `use Laravel\Scout\Searchable;`.
	
6. Import Data to MeiliSearch `php artisan scout:import "App\Models\Post"`

## Dealing with Meilisearch	

### To Search a Model
	```php
	$query = "Learn Laravel";
	$posts = Post::search($query)->take(10)->get();
	```

### To Import a Model 
- use the command: `php artisan scout:import "App\Models\Post"` *Post Model for example*

### To Flush a Model
- use the command: `php artisan scout:flush "App\Models\Post"` *Post Model for example*
	
### To chose what to search with
	```php
	#[SearchUsingPrefix(['id'])]	// Search using Prefix
    #[SearchUsingFullText(['title','content','author'])]	// Search using Full Text (Default)

    public function toSearchableArray(){
        return [
            'id' => $this->id, 
            'title' => $this->title, 
            'content' => $this->content,
            'author' => $this->user->name,
        ];
    }
	```

### To allow search only on some status with
	```php
	public function shouldBeSearchable(){
        return $this->isPublished();
    }
	```
