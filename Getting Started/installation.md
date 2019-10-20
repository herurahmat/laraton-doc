# Installation

- [Installation](#installation)
	- [Requirements](#requirements)
    - [Installing Laravel-DataTables](#installing-laraton)
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
- Copy `.env` file from `.env.example` using command `cp .env.example .env` then make some configs in `.env` file (please check `Config .env` Section)
- Make sure `DB_DATABASE` is set correctly in `.env` file then run `php artisan migrate`
- Run php artisan db:seed
- If migration is failed, please run `composer dump-autoload` first and remove any table(s) in database before execute migrate again


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
Add the file for [User Group](user/group#groupname) in ```app/Config/Navigation``` <br/>
Create format array : <br/>
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
For Single Menu <br/>
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

All route must add route name like : <br/>
```php
Route::get('myroute', 'Controller@index')->name('myroute');
```