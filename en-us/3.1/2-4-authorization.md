# Authorized

Authorized to belong to one of the middleware unit, by the middleware scheduler distribution processing. Can be customized to achieve their own authorization function.

Middleware Implementation: [Middleware] (en-us / 3.1 / 3-2-middleware.md)

The completed middleware is configured through the `middleware` configuration item of the application configuration file and can be used to nest multidimensional data and finally obtain` withAddMiddleware` through `withMiddleware`.

Authorization authentication mainly relies on: [basic-auth] (https://github.com/JanHuang/basic-authenticate) Components

##### Application Configuration:

`` `php
<? php
return [
    'middleware' => [
        'basic.auth' => new FastD \ BasicAuthenticate \ HttpBasicAuthentication ([
            'authenticator' => [
                'class' => \ FastD \ BasicAuthenticate \ PhpAuthenticator :: class,
                'params' => [
                    'foo' => 'bar'
                ]
            ],
            'response' => [
                'class' => \ FastD \ Http \ JsonResponse :: class,
                'data' => [
                    'msg' => 'not allow access',
                    'code' => 401
                ]
            ]
        ])
    ],
];
`` `

Authentication and authorization initialization need to receive user provider, or can not determine whether the source user is valid, and finally, by checking the legitimacy of users to check and support PDO processing.

##### Routing Configuration:

`` `php
route () -> get ("/", "IndexController @ sayHello") -> withAddMiddleware ('basic.auth');
`` `

Support configuration group middleware, the configuration simply convert the configuration into a two-digit array, the format remains unchanged.

##### Application Configuration

`` `php
<? php
return [
    'middleware' => [
        'basic' => [
            // middleware
            // middleware 2
        ]
    ],
];
`` `

##### Routing configuration

`` `php
route () -> get ("/", "IndexController @ sayHello") -> withAddMiddleware ('basic.auth');
`` `

Next Section: [Exception Handling] (en-us / 3.1 / 2-5-exception-logger-handling.md)