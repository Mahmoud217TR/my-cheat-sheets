# Laravel Tips & Tricks

**Table of Contents:**
* [Adding Foreign ID to tables](#adding-foreign-id-to-tables)
* [Making Pivot Tables](#making-pivot-tables)
* [Accessors & Mutators](#accessors--mutators)
* [Flashing data into Session](#flashing-data-into-session)
* [Get Back Route as URL](#get-back-route-as-url)
* [Make a state in factory](#make-a-state-in-factory)


## Adding Foreign ID to tables
Assuming we want to add **User** Model foreign to **Profile** Table There is 2 ways to do this:
1. Using the `User` Model:

    ```php
        // in Profile Migration file
        $table->foreignIdFor(User::class)->constrained()->onDelete('cascade');
        
        // in User Model
        public function profile(){
            return $this->hasOne(Profile::class);
        }

        // in Profile Model
        public function user(){
            return $this->belongsTo(User::class);
        }
    ```

    This will automatically generate a field called `user_id` to the migration file
2. Manuallay:

    ```php
    // in Profile Migration file
    $table->unsignedBigInteger('user_id');
    $table->foreign('user_id')->references('id')->on('users')->onDelete('cascade');
    
    // in User Model
    public function profile(){
        return $this->hasOne(Profile::class);
    }

    // in Profile Model
    public function user(){
            return $this->belongsTo(User::class);
    }
    ```

    With this way you can change foreign key name:

    ```php
    // in Profile Migration file
    $table->unsignedBigInteger('owner_id');
    $table->foreign('owner_id')->references('id')->on('users')->onDelete('cascade');
    
    // in User Model
    public function profile(){
        return $this->hasOne(Profile::class,'owner_id');
    }

    // in Profile Model
    public function user(){
            return $this->belongsTo(User::class,'owner_id');
    }
    ```


## Making Pivot Tables

To make a pivot table between **Post** model and **Tag** model *many to many relationship*
1. make a pivot migration:
    - Create a migration `php artisan make:migration create_post_tag_pivot_table --create post_tag` *models must be in lexicographical order*

	- In the migration file add the foreign keys:

    ```php
    $table->primary(['post_id', 'tag_id']); // To make it unique
	$table->foreignIdFor(Post::class)->constrained()->onDelete('cascade');   // will generate a field called "post_id"
    $table->foreignIdFor(Tag::class)->constrained()->onDelete('cascade');   // will generate a field called "tag_id"
    ```

    - Migrate `php artisan migrate`

2. Define the relationship in the **Post** model:

    ```php
	public function tags(){
		return $this->belongsToMany(Tag::class);
	}
    ```

3. Define the relationship in the **Tag** model:

	```php
    public function posts(){
		return $this->belongsToMany(Post::class);
	}
    ```

* To deal with the models:

	```php
    // From Post Model
    $post->tags()->attach($tag); 
	$post->tags()->detach($tag);
	$post->tags()->toggle($tag);

    // From Tag Model
    $tag->posts()->attach($post);
	$tag->posts()->detach($post);
	$tag->posts()->toggle($post);
    ```


## Accessors & Mutators

* Assume we have 4 states for `User` Model (Active, Inactive, Suspended, Banned):

    ```php
    // In User Migration

    $table->unsignedBigInteger('state'); // assuming the states are (0, 1, 2, 3)


    // In User Model

    // To ease getting states 
    public static function getState(){
        return [
            0 => 'Active',
            1 => 'Inactive',
            2 => 'Suspended',
            3 => 'Banned'
        ];
    }

    // The Accessor & Mutator
    public function getStateAttribute($attribute){
        return self::getState()[$attribute];
    }
    
    // Any where in app
    User::getState()    // returns all User states as text (Active, Inactive, Suspended, Banned)
    $user->state;       // returns the current user state as text
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