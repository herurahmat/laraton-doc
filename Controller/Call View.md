### Cara mudah memanggil view

Format :
```php
return laraview((string) view, Array Meta, Compact atau Array)
```
Contoh :
```php
$data=array(1,2,3);
return laraview('master.index',['title'=>'My Title'],compact('data'))

return laraview('master.index',['title'=>'My Title','description'=>'My Description'],['data'=>$data])
```
