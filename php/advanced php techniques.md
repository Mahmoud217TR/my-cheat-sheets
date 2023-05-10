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

- Formatting Table:

| Format Character | Description                                                                                         |
|------------------|-----------------------------------------------------------------------------------------------------|
| `%s`             | String (outputs the argument as a string)                                                           |
| `%d`             | Signed decimal number                                                                               |
| `%f`             | Floating-point number                                                                               |
| `%c`             | Character                                                                                           |
| `%b`             | Binary representation (outputs the argument as a binary number)                                     |
| `%o`             | Octal representation (outputs the argument as an octal number)                                      |
| `%x` or `%X`     | Hexadecimal representation (outputs the argument as a hexadecimal number, lowercase or uppercase)   |
| `%e` or `%E`     | Scientific notation (outputs the argument in scientific notation, lowercase or uppercase)           |
| `%u`             | Unsigned decimal number (outputs the argument as an unsigned integer)                               |
| `%g` or `%G`     | General format (outputs the argument as a floating-point number, using the shorter of `%e` or `%f`) |
| `%%`             | Literal `%` character (outputs a percent sign)    |

    - example

    ```php
    // %s: String
    $name = "John";
    printf("Name: %s\n", $name); // Name: John

    // %d: Signed decimal number
    $age = 25;
    printf("Age: %d\n", $age); // Age: 25

    // %f: Floating-point number
    $score = 85.5;
    printf("Score: %f\n", $score); // Score: 85.500000
    printf("Score: %0.2f\n", $score); // Score: 85.50

    // %c: Character
    $grade = 'A';
    printf("Grade: %c\n", $grade); // Grade: A

    // %b: Binary representation
    $number = 10;
    printf("Binary: %b\n", $number); // Binary: 1010

    // %o: Octal representation
    $octal = 25;
    printf("Octal: %o\n", $octal); // Octal: 31

    // %x or %X: Hexadecimal representation
    $hex = 255;
    printf("Hexadecimal: %x\n", $hex); // Hexadecimal: ff

    // %e or %E: Scientific notation
    $scientific = 1.23e+10;
    printf("Scientific: %e\n", $scientific); // Scientific: 1.230000e+10

    // %u: Unsigned decimal number
    $unsigned = 4294967295;
    printf("Unsigned: %u\n", $unsigned); // Unsigned: 4294967295

    // %g or %G: General format
    $score = 85.5;
    printf("General: %g\n", $score); // General: 85.5

    // %%: Literal % character
    printf("Percent: %%\n"); // Percent: %
    ```


- Padding:

    ```php
    $number = 42;

    // Left padding with spaces using printf
    printf("Left Padding: '%10s'\n", $number); // Left Padding: '        42'

    // Right padding with zeros using printf
    printf("Right Padding: '%-10s'\n", $number); // Right Padding: '42        '
    ```

    