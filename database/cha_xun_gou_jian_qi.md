# 查询构建器

查询构建器就是平时开发框架中的 `from()->select()` 等方法，其具体作用是自动构建 SQL 查询语句，方便开发，提高开发效率，但是构建器不支持复杂查询，具体复杂查询建议使用自己手写 SQL 语句进行查询，因为查询构建器无法保证高复杂度的查询效率。

**注意: 查询构建器是一个独立，不依赖于数据库连接驱动的独立对象，因此生成出来的语句，需要传递到连接驱动中才可以真正发挥作用。**

```php
$queryBuilder = Mysql::singleton();
```

获取 Mysql 查询构建器，其他方法 `createQueryBuilder` 中，原理也是通过 `Mysql::singleton` 获取查询构建器，因此通过 `Mysql::singleton` 即可获取最原始的构建器。

##### ＃通过连接驱动获取查询构建器

```php
/**
 * @Route("/builder", name="database.builder")
 *
 * @return Response|string
 */
public function queryBuilderAction()
{
    $this->getDriver('read')->createQueryBuilder();

    return $this->render('database/drivers.twig', [
        'sql' => $sql,
    ]);
}
```