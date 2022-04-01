# Mailables

**Table of Contents:**
* [Making Mail](#making-mail)
* [Sending Mails](#sending-mails)


## Making Mail

To make a mail for a *contact form* for example and let's name it `ConatctFormMail`:

```
php artisan make:mail ContactFormMail --markdown=emails.contactform
```

*markdown option is to make a view (the view will be in `emails` folder and named `contactform`)*.


Initilize passing data in the class constructor:

```php
public data; // Public to be visible at the view

public function __construct($data){
    $this->data = $data;
}
```

## Sending Mails

To send the previous mail `ContactFormMail` to `example@gmail.com` for example:

```php
Mail::to('example@gmail.com')->send(new ContactFormMail($data));
```

*make sure to set mail config `.env` file before sending any messages*