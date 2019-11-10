Secara default, role user pada Controller dapat diakses oleh semua user group.
Untuk function pada controller yang spesifik untuk menentukan siapa yang bisa mengakses. Contoh kode pada function :

```php

class MyClass extends Controller
{

	function add()
	{
		access_page(array('role1','role2'));
	}

}

```

atau anda juga menggunakan alias ```add_role```

```role1 atau role2 adalah user group key```

Jika anda adalah staff programmer, silahkan minta ke Administrator terkait user role yang dapat digunakan