# Database Tricks

**Table of Contents:**
* [Adding Foreign ID to tables](#adding-foreign-id-to-tables)
* [Making Pivot Tables](#making-pivot-tables)
* [Many To Many with data](#many-to-many-with-data)


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


## Many To Many with data

Let's say that we hava a `User` Model which can vote up or vote down a `Post` Model to make such a relationship:

1. Make the migration and let's call the table `post_votes`:

```
php artisan make:migration create_post_votes_table --create post_votes
```

2. Set the table columns:

```php
$table->primary(['post_id', 'user_id']);
$table->foreignIdFor(Post::class)->constrained()->onDelete('cascade');
$table->foreignIdFor(User::class)->constrained()->onDelete('cascade');
$table->boolean('upvote'); // is up vote or down vote
```

3. Define the relationships in Models:

```php
// in User Model
public function postVotes(){
    return $this->belongsToMany(Post::class,'post_user','user_id')->withPivot('upvote'); // get the column with result
}

// in Post Model
public function userVotes(){
    return $this->belongsToMany(User::class,'post_user','post_id')->withPivot('upvote'); // get the column with result
}

```

4. To attach or detach models:

```php
// Attaching
$user->postVotes()->attach($post,['upvote'=>$value]);
$post->userVotes()->attach($user,['upvote'=>$value]);

// Detaching
$user->postVotes()->detach($post);
$post->userVotes()->detach($user);
```

5. Some extra Functions:

```php

// in User Model
public function postUpvotes(){
    return $this->postVotes->where('pivot.upvote',true);
}

public function postDownvotes(){
    return $this->postVotes->where('pivot.upvote',false);
}

// in Post Model
public function userUpvotes(){
    return $this->UserVotes->where('pivot.upvote',true);
}

public function userDownvotes(){
    return $this->UserVotes->where('pivot.upvote',false);
}
```
