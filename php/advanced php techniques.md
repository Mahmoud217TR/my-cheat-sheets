# Advanced PHP Techniques

**Table of Contents:**
* [Creating your own Sort Function](#creating-your-own-sort-function)
* [Printing with PHP](#printing-with-php)



## Creating your own Sort Function

- First: We define a sorting function, For example `mySortFunction`, that returns a value will be used to sort items:
    - if the value is `false` or Negative value this means **The First element becomes before the Second**.
    - if the value is `true` or Positive value this means **The Second element becomes before the First**.
    - if the value is `0` this means **The to elements are the Same**.

- For Example:

```php
// Sorting elements in Ascending order
function mySortFunction($first, $second)
{
    if ($first > $second) {
        return true;
    } elseif ($second > $first) {
        return false;
    } else {
        return 0;
    }
}

// The same function in a Better way
function mySortFunction($first, $second)
{
    return $first - $second;
}


// Sorting strings Alphabetically
function myStringSortFunction($first, $second)
{
    return strcasecmp($first, $second);
}

// Sorting strings Alphabetically (case-sensitive)
function myStringSortFunction($first, $second)
{
    return strcmp($first, $second);
}
```


- Second: We use one of `usort`, `uasort`, or `uksort` passing our sort function:

```php
$array =  [5,2,3,1,4];
usort($array, "mySortFunction"); // [1, 2, 3, 4, 5]

// You can use an anonymouse function
usort($array, function ($first, $second) {
    return $first - $second;
})
```


## Printing with PHP

- There is several ways to print in php:
    - `echo`: used to output one or more strings.
    
    ```php
    echo "Hello, World!"; // Outputs "Hello, World!"
    ```


    - `print`: similar to echo, but it returns a value indicating success or failure.

    ```php
    $result = print "Hello, World!"; // Prints "Hello, World!" & $result = 1
    ```


    - `printf`: used for formatted output. It allows you to specify a format string with placeholders that are replaced by the corresponding values.

    ```php
    $name = "John";
    $age = 25;

    $result = printf("My name is %s and I am %d years old.", $name, $age); // Prints "My name is John and I am 25 years old." & $result = 38
    ```


    - `print_r` used to display the contents of an array in a human-readable format. It is mainly used for debugging purposes, it returns a value indicating success or failure.

    ```php
    $array = array("apple", "banana", "cherry");
    $result = print_r($array); // Prints "Array ( [0] => apple [1] => banana [2] => cherry )" & $result = 1
    ```


    - `var_dump` used for debugging and displays detailed information about one or more variables, including their type and value.

    ```php
    $number = 42;
    var_dump($number); // Prints "int(42)"
    ```

