<h1 align="center">FastD 中文文档</h1>

<p align="center">:rocket: A high performance PHP API framework.</p>

<p align="center">
<a href="https://travis-ci.org/JanHuang/fastD"><img src="https://travis-ci.org/JanHuang/fastD.svg?branch=master" /></a>
<a href="https://scrutinizer-ci.com/g/JanHuang/fastD/?branch=master"><img src="https://scrutinizer-ci.com/g/JanHuang/fastD/badges/quality-score.png?b=master" title="Scrutinizer Code Quality"></a>
<a href="https://scrutinizer-ci.com/g/JanHuang/fastD/?branch=master"><img src="https://scrutinizer-ci.com/g/JanHuang/fastD/badges/coverage.png?b=master" alt="Code Coverage"></a>
<a href="https://styleci.io/repos/35930132"><img src="https://styleci.io/repos/35930132/shield?branch=3.1" alt="StyleCI"></a>
<a href="https://fastdlabs.com/"><img src="https://poser.pugx.org/fastd/fastd/v/stable" /></a>
<a href="http://www.php.net/"><img src="https://img.shields.io/badge/php-%3E%3D5.6-8892BF.svg" /></a>
<a href="http://www.swoole.com/"><img src="https://img.shields.io/badge/swoole-%3E%3D1.9.6-8892BF.svg" /></a>
<a href="https://fastdlabs.com/"><img src="https://poser.pugx.org/fastd/fastd/license" /></a>
</p>

框架中集成了部分使用率较高的工具，提高开发效率，不必担心的是，框架并不会因为依赖的东西多了而造成速度的变慢，程序中，仅会对使用到的文件代码进行操作。

框架执行模式: 

1. 普通模式
2. 命令行模式
3. Swoole 模式

针对不同模式，加载的对象不大相同，所以针对不同的执行环境，会有不同的操作流程来加速框架的调度效率。

### 修改日志

- [修改日志](zh-cn/3.1/change-log.md)
- [升级指南](zh-cn/3.1/upgrade.md)

### 安装与配置

- [关于 FastD](zh-cn/3.1/1-1-about-fastd.md)
- [安装 FastD](zh-cn/3.1/1-2-installing.md)
- [目录结构](zh-cn/3.1/1-3-directory-structure.md)
- [框架执行流程图](zh-cn/3.1/1-4-flow.md)

### 基础入门

- [路由与控制器](zh-cn/3.1/2-1-routing-and-controllers.md)
- [请求处理](zh-cn/3.1/2-2-request-handling.md)
- [响应处理](zh-cn/3.1/2-3-response-handling.md)
- [认证授权](zh-cn/3.1/2-4-authorization.md)
- [异常与日志处理](zh-cn/3.1/2-5-exception-logger-handling.md)
- [ ] ~~[API文档](zh-cn/3.1/2-6-docuemnt.md)~~

### 高级

- [配置](zh-cn/3.1/3-1-configuration.md)
- [中间件](zh-cn/3.1/3-2-middleware.md)
- [数据库medoo](zh-cn/3.1/3-3-database.md)
- [缓存](zh-cn/3.1/3-4-cache.md)
- [命令行](zh-cn/3.1/3-5-console.md)
- [单元测试](zh-cn/3.1/3-6-testcase.md)
- [辅助函数](zh-cn/3.1/3-7-helpers.md)
- [服务提供器](zh-cn/3.1/3-8-service-provider.md)
- [Swoole服务器](zh-cn/3.1/3-9-swoole-server.md)
- [连接池](zh-cn/3.1/3-10-connection-pool.md)
- [扩展](zh-cn/3.1/3-11-extend.md)

### 架构

- [生命周期](zh-cn/3.1/4-1-lifecycle.md)
- [ ] ~~[RPC服务](zh-cn/3.1/4-2-microservice.md)~~
- [ ] [FastD 与 LogStash](zh-cn/3.1/4-3-fastd-logstash.md) (未开放)
- [ ] [FastD 与 QConf](zh-cn/3.1/4-4-fastd-qconf.md) (未开放)
- [ ] [FastD 与 LogViewer](zh-cn/3.1/4-5-fastd-log-viewer.md) (未开放)

### Support

如果你在使用中遇到问题，请联系: [bboyjanhuang@gmail.com](mailto:bboyjanhuang@gmail.com). 微博: [编码侠](http://weibo.com/ecbboyjan)

## License MIT