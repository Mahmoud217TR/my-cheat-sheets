# Installation & Setup

## Installaion

To install jquery use `npm install jquery`


## Setup Jquery

To setup jquery add this to script for requests:

* Make sure this is present in blade head:
```blade
<meta name="csrf-token" content="{{ csrf_token() }}">
```
* Then add this:

```javascript
$.ajaxSetup({
    headers:{
        'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
    }
});
```