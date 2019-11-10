# Installation

- [Installation](#installation)
	- [Requirements](#requirements)
    - [Installing Laraton](#installing-laraton)
    - [Configuration](#configuration)

<a name="installation"></a>
## Installation

<a name="requirements"></a>
### Requirements

- [Laravel 6.2x](https://github.com/laravel/framework)
- PHP 7.2
- MySQL 8.x

<a name="installing-laraton"></a>
### Installing Laraton

- Git Clone https://github.com/herurahmat/laraton.git
- Run `composer install`
- Copy `.env` file from `.env.example` menggunakan command `cp .env.example .env` dan membuat file `.env`
- Set database pada `DB_DATABASE` pada file `.env` dan lakukan command `php artisan migrate`
- Run php artisan db:seed
- Jika migrasi database gagal, jalankan command `composer dump-autoload` lalu hapus table


<a name="configuration"></a>
### Configuration

- Static global config <br/>
Open the file ```app/Config/global.php```
	- session_name
	- asset_url
	- asset_path
	- upload_url
	- upload_path
	- thumbnail_size
- Navigation User Group <br/>
Tambah file pada [User Group](user/group#groupname) in ```app/Config/Navigation``` <br/>
Buat format array : <br/>
```php
$array=[
	'Title of Menu' => [
		's1' => 'Segment One',
		's2' => 'Segment Two', //(Optional)
		's3' => 'Segment Three',//Optional,
		'icon' => 'icon like fontawesome or other',
		'child' => [
			'Sub Menu' => [
				'icon' => 'Icon',
				'route' => 'name of route'
			]
		]
	]
];
```
Menu Single <br/>
```php
$array=[
	'Title of Menu' => [
		's1' => 'Segment One',
		's2' => 'Segment Two', //(Optional)
		's3' => 'Segment Three',//Optional,
		'route' => 'name of route'
	]
];
```

**Note !!**

Route harus diberi nama seperti berikut : <br/>
```php
Route::get('myroute', 'Controller@index')->name('myroute');
```