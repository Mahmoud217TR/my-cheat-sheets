# Laravel Excel

**Table of Contents:**
* [Installation & Setup](#installation--setup)
* [Export](#export)
* [Import](#import)
* [Exporting with Headings](#exporting-with-headings)
* [Styling](#styling)


## Installation & Setup

* To Install the Library use: `composer require maatwebsite/excel`

* Next Export the config file: 

```
php artisan vendor:publish --provider="Maatwebsite\Excel\ExcelServiceProvider" --tag=config
```

> Check the Docs of [Laravel Excel](https://laravel-excel.com).


## Export

* To make an Export class named `UsersExport` for `User` model for example use:

```
php artisan make:export UsersExport --model=User

```

* To Export the excel file assume we have a controller that have the method `export`:

```php
public function export() {
    return Excel::download(new UsersExport, 'users.xlsx');
}
```
> the generated file name will be `users`.



## Import

* To make an Import class to `User` model for example use:

```
php artisan make:import UsersImport --model=User
```

* To Import from a file called `users.xlsx` assume we have a controller that has the method `import`:

```php
public function import(){
    Excel::import(new UsersImport, 'users.xlsx');
    
    // Redirecting with Success message
    return redirect('/')->with('success', 'All good!');
}
```


## Exporting with Headings

Asuming we want to export **only** (id, name, email) attributes from `User` model, and we want to add headings to the columns in the excel sheet, you need to do 2 things:

1. Make the model implements the `WithHeadings` interface.
2. Override the `headings` method.

```php
namespace App\Exports;

use App\Models\User;
use Maatwebsite\Excel\Concerns\FromCollection;
use Maatwebsite\Excel\Concerns\WithHeadings;

class UsersExport implements FromCollection, WithHeadings
{
    /**
    * @return \Illuminate\Support\Collection
    */
    public function collection()
    {
        return User::select('id', 'name', 'email');
    }

    public function headings(): array
    {
        return [
            'ID',
            'Name',
            'Email',
        ];
    }

}
```


## Styling

* To Style the Headings in the previous example:

1. First install PhpSpreadsheet package `composer require phpoffice/phpspreadsheet`.
2. Make the class Implements the `WithStyles` interface.
3. Override the `styles` method *passing an object of `Worksheet`*.

```php
namespace App\Exports;

use App\Models\User;
use Maatwebsite\Excel\Concerns\FromCollection;
use Maatwebsite\Excel\Concerns\WithHeadings;
use Maatwebsite\Excel\Concerns\WithStyles;
use PhpOffice\PhpSpreadsheet\Worksheet\Worksheet;

class UsersExport implements FromCollection, WithHeadings, WithStyles
{
    /**
    * @return \Illuminate\Support\Collection
    */
    public function collection()
    {
        return User::select('id', 'name', 'email');
    }

    public function headings(): array
    {
        return [
            'ID',
            'Name',
            'Email',
        ];
    }

    public function styles(Worksheet $sheet)
    {
        return [
            // Styles the first row as bold text.
            1    => ['font' => ['bold' => true]],
            // Styles the first column as bold text.
            A    => ['font' => ['bold' => true]],
        ];
    }

}
```

> Check [PhpSpreadSheet Docs](https://phpspreadsheet.readthedocs.io/en/latest/).