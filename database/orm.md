# ORM

ORM 是框架 2.x 版本新增的一个特性，其中 ORM 实现对象模型映射，模型间的关系映射暂时并不支持，并且会考虑到性能方面的问题，未来也不一定会加入的新特性当中，因此目前版本 ORM 是仅对简单操作进行一个封装，并不支持完善复杂的关系模型映射，敬请原谅。

### ＃基本用法

ORM 的生成建议依赖于命令行，当然如果手动建立也是可以的，但是这样子重复性的工作就会比较多，所以我一般建议，如果可以自动化处理的，那就直接自动化处理，然后再经过自己又话就好了，省掉多余的时间。

此处 ORM 有个好处就是，可以根据已有的数据库声称对应的对象文件，省掉大部分不必要浪费的时间。

##### ＃ORM 命令

系统中默认提供两个操作命令

```php
php bin/console
```

输出: 

```php
...
orm:
 ➜ orm:revert
 ➜ orm:update
...
```

`orm:revert` 是通过已存在的数据库反射出关系对象。

`orm:update` 是通过自己定义的数据表，进行自动生成表结构和数据表关系对象。

因此两者仅是一个流程顺序的关系。

**数据库操作命令不应该在生产环境之行**

##### ＃orm:update

`orm:update` 前提需要建立数据库 `yml` 配置文件，命令通过已经存在的配置文件，创建数据表已经关系对象，每一个配置文件代表一个数据表。

建立数据表配置文件: 

```yml
table: demo
prefix: fd_
suffix: ''
engine: innodb
charset: utf8
fields:
    id:
        name: id
        type: int
        length: 10
        default: 0
        comment: ''
        unsigned: false
        key: ''
        nullable: false
```

目前数据表配置仅支持 `yml` 格式，因为 `yml` 格式文件直观，可以一目了然，所以在配置文件上是一个绝佳的选择，但是要考虑性能的问题，不能滥用，因为命令执行在 CLI 模式下，因此不需要考虑性能问题。

字段解释: 

表名(必填): 

```yml
table: demo
```

前缀: 

```yml
prefix: fd_ # 默认留空
```

后缀: 

```yml
suffix: # 默认留空
```

存储引擎:

```yml
engine: innodb # 默认是 InnoDB
```

存储编码:

```yml
charset: utf8 # 默认是 utf8
```

##### ＃orm:revert