## Advance Route Middleware for Authentication ##

1. Create file Middleware in `app\Http\Middleware` with format : 

```php
<?php

namespace App\Http\Middleware;

use Closure;
use Session;
use App\Libraries\Core\AuthLoader;

class MyGroupMiddleware
{
    public function handle($request, Closure $next)
    {
        $auth=new AuthLoader();
        if ($auth->has_login()) {
            $session_name=laraconfig('global','session_name');
            $group_name=session($session_name)['group_name'];
            if($group_name=='routegroup')
            {
                return $next($request);
            }else{
                return redirect()->route('dashboard')->with('error', 'Not Authentication');
            }
        }else{
            return redirect()->route('login')->with('error', 'You must login first!');
        }
        
    }
}

```

In code 
```php
if($group_name=='routegroup')
```
You can pass route group from super administrator user group name


2. Register Middleware to `app\Http\Kernel.php` in array `routeMiddleware`

```php
protected $routeMiddleware = [
        
        'check.group' => \App\Http\Middleware\MyGroupMiddleware::class,
];
```

3. Add to Route `routes\web.php` in group middleware `check.authentication`

```php
Route::group(['middleware' => 'check.authentication'], function () {

	Route::group(['middleware'=>'check.group'],function(){
	
	// Your Route
	
	});
});
```

