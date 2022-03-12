# Hashing & Encryption

**Table of Contents:**
* [Hashing](#hashing)
* [Encryption](#encryption)


# Hashing

To Hash a word or check the hashing for example the word `password`:

```php
$hashed = Hash::make('password'); // Hashing the word

Hash::check('password', $hashed); // checks if the hashing of the word is the same as the hashed result
```


# Encryption

To Encrypt & Decrypt some string for example `string`:

```php
$encrypted = Crypt::encrypt('string'); // returns an encrypted string
Crypt::decrypt($encrypted); // returns the original string
```

To change the Mode or the Cipher of Encryption & Decryption:

```php
Crypt::setMode('ctr');
Crypt::setCipher($cipher);
```