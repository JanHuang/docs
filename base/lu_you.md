# 路由

路由是一个框架必备的东西，配置的方式参考了 Laravel 和 Symfony 两个框架。

路由配置文件在 `{bundle}/Resources/config/routes.php`

## 基础路由配置

### GET

该路由地址只能通过 Get 访问

```
Routes::get('base', '/base', \WelcomeBundle\Controllers\Index::class.'@indexAction');
```

**Action**

```php
public function indexAction()
{
    return $this->response('hello world');
}
```

只需要用户访问 `/base` 路由的时候，`\WelcomeBundle\Controllers\Index` 下的 `indexAction` 将会被执行，会出现 `hello world` 字样，证明已经配置成功了。路由这里的第一个参数，是路由的名字，在其他地方进行调用的时候可以通过该名字直接进行调用

而 `indexAction` 即是控制器方法，具体请求处理的方法主体。

### POST

```
Routes::post('base_post', '/base', \WelcomeBundle\Controllers\Index::class.'@postAction');
```

**Action**

```php
public function postAction()
{
    return $this->response('That is POST request method.');
}
```

路由配置支持:

* get
* post
* put
* delete
* patch
* any (意指允许所有请求方法到达路由)

## 动态路由

```
Routes::get('dynamic', '/{name}', \WelcomeBundle\Controllers\Index::class.'@dynamicAction');
```

**Action**

```php
 public function dynamicAction($name)
{
    return $this->response('This variable is ' . $name);
}
```

访问地址: `/janhuang` 即可出现 `This variable is janhuang` 等字样，动态路由配置成功。

而动态路由中的参数 `{name}` 会作为控制器方法动态传递到方法中 `dynamicAction($name)` 。


## 路由组

路由组可以说是一系列路由的前缀。

```php
Routes::group('/user', function () {
    Routes::get('user_profile', '/profile', \WelcomeBundle\Controllers\Index::class.'@profileAction');
});
```

`/user` 就是匿名函数中所有路由的前缀，凡是在匿名函数中定义的路由，都会带上此前缀，路由组支持多层嵌套。

## 注释路由

注释路由仅在非生产环境下才会发挥作用，因为需要解析大量的注释，如果在生产环境下启用这种功能会造成大量的资源浪费，但可以通过命令对其进行缓存，该思路参考 Symfony 框架进行开发。

注释路由仅在控制器方法中才会生效，并且方法名要是 `Action` 结尾才能生效。

展开文件 `WelcomeBundle/Controllers/Index.php`

```php
namespace WelcomeBundle\Controllers;

use FastD\Framework\Bundle\Controllers\Controller;

/**
 * @Route("/welcomebundle")
 */
class Index extends Controller
{
    /**
     * @Route("/")
     */
    public function indexAction()
    {
        return $this->response('hello world');
    }
    // ...... some codes.
}
```

类名之上的注释就相当是路由组的功能，而方法上的注释则是具体的路由地址。参数与路由文件配置一样。

配置路由请求方法需要另加注释: `@Method("GET")` 里面参数是控制路由请求方法的值。

完整配置: 

```php
/**
 * @Route("/", name="route.name", defaults={}, requirements={})
 * @Method("GET")
 */
```

**注释中字符串必须用双引号`"`，单引号无法解析，default、requirements 参数值必须是 json**

## 路由命令

如果这么多的路由不配套命令管理，那将是非常难以管理的。

### 路由列表命令

```
php bin/console route:dump
```


