# Dealing with Policies in Laravel

**Table of Contents:**
* [Creating a Policy](#creating-a-policy)
* [Dealing with Policy](#dealing-with-policy)
* [Guest Approach (Null User) in Policies](#guest-approach-null-user-in-policies)
* [Combining Multiple cans](#combining-multiple-cans)


## Creating a Policy

To crate a policy for `Profile` Model as example use the command `php artisan make:policy ProfilePolicy -m Profile`.


## Dealing with Policy

To make sure that only the owner of the profile modifies using policy:

```php
// in ProfilePolicy file
public function update(User $user, Profile $profile){
    return $user->id == $profile->user_id; // check if the profile user is the owner
}
```

To use this on controller or in the app:

```php
$this->authorize('update',$user->profile); // pass the profile
```

To use this on blade using blade diretive `@can`:

```blade
@can('update',$user->profile);
```

## Guest Approach (Null User) in Policies

If you have some method that could accept null `User` or a guest put `?` before the user model.
for example:

```php
public function view(?User $user, Profile $profile){
    // do some stuff
}
```


## Combining Multiple cans

I you have multiple can statements such as any one who can update **or** delete a `Post` for example use `canany`:

```blade
    @canany(['update','delete'],$post)
        {{-- what do you wanna do here --}}
    @endcan
```