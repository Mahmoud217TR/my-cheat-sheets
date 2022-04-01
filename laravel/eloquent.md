# Eloquent

**Table of Contents:**
* [One-to-One](#one-to-one)
* [One-to-Many](#one-to-many)
* [Many-to-Many](#many-to-many)
* [Many-to-Many with data](#many-to-many-with-data)
* [Adding Foreign ID to tables](#adding-foreign-id-to-tables)


## One-to-One

To make a One-to-One Relation between a `User` model and `Profile` model for example:

1. Decide how owns how (in this case User Owns Profile):

2. Put a foreign key in the owned object migration referse to the owner:

    ```php
    $table->foreignIdFor(User::class)->constrained()->onDelete('cascade');
    ```

3. Define the relationships in models:
    
    ```php
    // in User Model
    public function profile(){
        return $this->hasOne(Profile::class);
    }

    // in Profile Model
    public function user(){
        return $this->belongsTo(User::class);
    }
    ```

4. Working with models:

    ```php
    // save
    $user->profile()->save($user);

    // create
    $user->profile()->create($data);
    ```

## One-to-Many

To make One-to-Many relation between `User` model and `Post` model for example:

1. Add a foreign key to the many model migration:

    ```php
    $table->foreignIdFor(User::class)->constrained()->onDelete('cascade');
    ```

2. Define the relationships in models:

    ```php
    // in User model
    public function posts(){
        return $this->hasMany(Post::class);
    }

    // in Post model
    public function user(){
        return $this->belongsTo(User::class);
    }
    ```

3. Working with the models:

    ```php
    // save
    $user->posts()->saveMany($profile);

    // create
    $user->posts()->create($data);

    // associate
    $post->user()->associate($post);
    $post->save();

    // dissociate
    $post->user()->dissociate(); // set the foreign key null
    $post->save();
    ```


## Many-to-Many

To make a Many-to-Many table between `Post` model and `Tag` model:

1. make a pivot migration:
    - Create a migration `php artisan make:migration create_post_tag_pivot_table --create post_tag` *models must be in lexicographical order*

	- In the migration file add the foreign keys:

    ```php
    $table->primary(['post_id', 'tag_id']); // To make it unique ((on database level))
	$table->foreignIdFor(Post::class)->constrained()->onDelete('cascade');   // will generate a field called "post_id"
    $table->foreignIdFor(Tag::class)->constrained()->onDelete('cascade');   // will generate a field called "tag_id"
    ```

    - Migrate `php artisan migrate`

2. Define the relationships in models:

    ```php
    // in Post model
	public function tags(){
		return $this->belongsToMany(Tag::class);
	}

    // in Tag model
    public function posts(){
		return $this->belongsToMany(Post::class);
	}
    ```

3. Working with the models:

	```php
    // From Post Model
    $post->tags()->attach($tag); 
	$post->tags()->detach($tag);
	$post->tags()->toggle($tag);
	$post->tags()->sync($tag); // for unique
	$post->tags()->syncWithoutDetaching($tag); // for unique

    // From Tag Model
    $tag->posts()->attach($post);
	$tag->posts()->detach($post);
	$tag->posts()->toggle($post);
	$tag->posts()->sync($post); // for unique
	$tag->posts()->syncWithoutDetaching($post); // for unique
    ```


## Many-to-Many with data

To make Many-to-Many relation with data for `User` model and `Post` model *user can vote up or vote down a post*:

1. Make the migration and let's call the table `post_user`:

    ```
    php artisan make:migration create_post_user_table --create post_user
    ```

2. Set the table columns:

    ```php
    $table->primary(['post_id', 'user_id']);
    $table->foreignIdFor(Post::class)->constrained()->onDelete('cascade');
    $table->foreignIdFor(User::class)->constrained()->onDelete('cascade');
    $table->boolean('upvote'); // is up vote or down vote
    ```

3. Define the relationships in models:

    ```php
    // in User Model
    public function posts(){
        return $this->belongsToMany(Post::class)->withPivot('upvote'); // get the column with result
    }

    // in Post Model
    public function users(){
        return $this->belongsToMany(User::class)->withPivot('upvote'); // get the column with result
    }

    ```

4. Working with the models:

    ```php
    // Attaching
    $user->posts()->attach($post,['upvote'=>$value]);
    $post->users()->attach($user,['upvote'=>$value]);

    // Detaching
    $user->posts()->detach($post);
    $post->users()->detach($user);

    // Toggle
    $user->posts()->toggle($post);
    $post->users()->toggle($user);

    // Sync
	$user->posts()->sync($post); // for unique
	$post->users()->sync($user); // for unique

    // Sync without detaching
	$user->posts()->syncWithoutDetaching($post); // for unique
	$post->users()->syncWithoutDetaching($user); // for unique

    // To just update the pivot data
    $user->posts()->updateExistingPivot($post, [
        'key' => 'value',
    ]);
    ```

5. Some extra Functions:

    ```php
    // for User Model
    public function postUpvotes(){
        return $this->posts->where('pivot.upvote',true);
    }

    public function postDownvotes(){
        return $this->posts->where('pivot.upvote',false);
    }

    // for Post Model
    public function userUpvotes(){
        return $this->user->where('pivot.upvote',true);
    }

    public function userDownvotes(){
        return $this->user->where('pivot.upvote',false);
    }
    ```


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

    This will automatically generate a field called `user_id` to the migration file.

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