Cara membuat konfigurasi menu

Untuk membuat menu, anda harus mengetahui user group. Jika anda tidak mempunyai akses user group. Silahkan hubungi Administrator.

Formatnya adalah :
```php
$variable=[ //Multiple Menu
	(string) key=>[
		'icon'=>(string),
		's1'=>(string) uri segment,
		's2'=>(string) uri segment (optional),
		's3'=>(string) uri segment (optional),
		'child'=>[
			(string) key=>[
				'icon'=>(string),
                'route'=>(route name),
                'params'=>(route param) (optional)
			]
		]
	]
];

$variable2=[ //Single Menu
	(string) key=>[
		'icon'=>(string),
		's1'=>(string) uri segment,
		's2'=>(string) uri segment (optional),
		's3'=>(string) uri segment (optional),
		'route'=>(route name),
        'params'=>(route param) (optional)
	]
];
```
Silahkan buat file baru pada ```app\Config\Navigation\grupuser.php``

Contoh penggunaan :
```php
$menu_config=[
    'Configuration'=>[
        's1'=>'core',
        's2'=>'config',
        'icon'=>'fa fa-wrench',
        'child'=>[
            'Application'=>[
                'icon'=>'fa fa-circle-o',
                'route'=>'core.config.general',
                'params'=>['prefix'=>'app']
            ],
            'Company'=>[
                'icon'=>'fa fa-circle-o',
                'route'=>'core.config.general',
                'params'=>['prefix'=>'company']
            ],
            'Logo & Favicon'=>[
                'icon'=>'fa fa-circle-o',
                'route'=>'core.config.logo'
            ],
        ]
    ]
];
return array_merge($menu_config);
```

1. URI Segment. Contohnya ```Domain/public/core/config``` maka segment 1 dihitung dari ```core```.

2. Perbedaan Single Menu dan Multiple Menu adalah Single menu tidak mempunyai child

3. Params adalah return url dari route. Contoh :
```php
Route::get('detail/{id}','ContohController@detail')->name('detail');
```
Maka params diisi
```php
'params`=>['id'=>123]
``` 