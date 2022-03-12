# Blade

**Table of Contents:**
* [Blade Templates](#blade-templates)
* [Including Views](#including-views)
* [Echoing](#echoing)


## Blade Templates

To make app template named `app` make a view called `app.blade.php` and should look like:

```blade
<!-- template contents -->

@yield('content') <!-- here where the other pages should appear -->

<!-- template contents -->
```

The Oher views the uses the previous template should be like:

```blade
@extends('app')
@section('content')

<!-- view contents -->

@section('content')
```

## Including Views

To include a view called `navbar` for example in the current view use:

```blade
@include('navbar')
```

## Echoing

To echo in views:

```blade
{{ $var }}  <!-- Echo content -->

{{{ $var }}}    <!-- Echo escaped content -->

{!! $var !!} <!-- Echo unescaped content -->

{{-- Blade Comment --}} <!-- Blade Comment -->

{{{ $name or 'Default' }}} <!-- Echoing Data After Checking For Existence  -->

@{{ This will not be processed by Blade }} <!-- Displaying Raw Text With Curly Braces -->
```
