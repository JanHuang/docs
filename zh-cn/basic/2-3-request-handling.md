# 请求处理

FastD 默认内置 HTTP、TCP、UDP、WebSocket 协议，由 [Swoole](http://www.swoole.com/) 强力驱动。

### HTTP

Http 请求处理来源于 [Http](https://github.com/JanHuang/http) 组件，由其提供强大的 Http 解析预处理，支持 Swoole.

当用户发起一个 Http 请求的时候，[Http](https://github.com/JanHuang/http) 组件会将请求封装成一个 ServerRequestInterface 实现类，实现 [PSR7](http://www.php-fig.org/psr/psr-7/) 标准，并且将对象传递到控制器中。

> 由于 Http 解析是通过 parse_url 进行解析的，因此您需要配置好你的虚拟域名(virtual-host)进行访问，否则会提示 route 404 not found

由于 Http 组件实现 PSR7，所以用法是保持 PSR7 一致，操作可以根据 [Http](https://github.com/JanHuang/http) 进行查看

```php
<?php

namespace Controller;


use FastD\Http\ServerRequest;

class IndexController
{
    public function sayHello(ServerRequest $serverRequest)
    {
        if (!empty($serverRequest->getQueryParams())) {
            abort(400);
        }
        return json($serverRequest->getQueryParams());
    }
}
```

### TCP

TCP 解析协议为 `JSON`，因此在进行参数传递的时候，需要对上传参数进行 json 编码，即将扩展的是自定义协议封装。

内置默认的数据格式为: 

```json
{
  "method": "get",
  "path": "/",
  "args": {
    "foo": "bar"
  }
}
```

### WebSocket

WebSocket 中也是使用 JSON 作为数据传输格式，和 TCP 参数格式保持一样。

详细服务器配置可以点击: [Swoole 服务器](zh-cn/3-9-swoole-server.md)

内置服务器协议最终会转换成 HTTP 协议解析，因此可以兼容各种不同的内置服务器，平滑过渡。

下一节: [响应处理](zh-cn/2-3-response-handling.md)