# Laravel Installation

## Requirements
* [php](https://www.php.net/downloads.php)
* [composer](https://getcomposer.org)
* [node.js](https://nodejs.org/en/) *(for npm not necessary)*

## Installation Guide

1. Install PHP
* Extract the files at path `(C:\php)`
* Rename `(C:\php\php.ini-development)` to `(C:\php\php.ini)`
* Add `(C:\php)` to the path environment variable
* Enable the following extensions :
    ```
    extension=curl
    extension=gd2
    extension=mbstring
    extension=mysql
    extension=pdo_mysql
    extension=xmlrpc
    extension=sqlite3
    extension=fileinfo
    ```

2. Install Composer

3. Install Node

4. Install Laravel using Composer
* Run this command on CMD `composer global require laravel/installer`