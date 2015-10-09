#数据库入门

##获取数据库连接

数据库配置参考[数据库配置](shu_ju_ku_pei_zhi.md)。

上述配置了 `read` 和 `write` 两个链接的配置。

获取 `read` 链接: 

```php

use FastD\Http\Request;

class Demo extends BaseEvent
{
    public function demoAction(){
        $request = Request::createRequestHandle;
        return $request->query->hasGet('name', 'janhuang');
    }
}

Routes::get('/', 'Demo@demoAction');
```