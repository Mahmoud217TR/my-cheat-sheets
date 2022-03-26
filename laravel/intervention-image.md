# Intervention-Image

[Check the API](https://image.intervention.io/v2/api)

**Table of Content:**
* [Installation](#installation)
* [Usage](#usage)


## Installation

First Make sure you enabled `extension=gd` in `php.ini` file.

To Install the Package use `composer require intervention/image`.

Now in `config/app.php`:

- To `'providers'` add this line:

    ```php
    'Intervention\Image\ImageServiceProvider',
    ```

- To `aliases` add this line:
    ```php
    'Image' => 'Intervention\Image\Facades\Image',
    ```

Now it's ready to use all You have to do is add `use Image` in the top of the file.

## Usage

Let's assume we have an image in the path `public/image.jpg`:

```php 
// Get the Image Object
$img = Image::make('public/image.jpg');

// To Fit the image in 500*300 ratio
$img->fit(500, 300)->save();

// To crop an image
$img->crop(300, 300);

// To apply slight blur filter
$img->blur();
```