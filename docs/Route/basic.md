## Basic Route ##

If you controller must login first. You can create route in `routes\web.php` and create after comment

```php
/* SET ROUTE WITH AUTHENTICATION BACKEND HERE */
Route::get('myroute', 'MyController@index')->name('routename');
```