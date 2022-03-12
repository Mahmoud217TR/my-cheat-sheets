# Cookies

**Table of Contents:**
* [Creating cookies](#creating-cookies)
* [Getting Cookie value](#getting-cookie-value)
* [Removing a cookie](#removing-a-cookie)


## Creating cookies

To create a cookie:

```php
Cookie::forever('key', 'value');
Cookie::make('key', 'value', 'minutes');
```

## Getting cookie value

To get a cookie value:

```php
Cookie::get('key');
Cookie::get('key', 'default');
```

## Removing a cookie:

To forget (remove) a cookie:

```php
Cookie::forget('key');
```