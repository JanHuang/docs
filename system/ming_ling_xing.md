# 命令行

框架本身提供命令的方式对程序进行管理，具体参考了 Symfony 的设计与布局方式，因此在开发中也需要注意命令的使用，适当地使用命令可以大大提高开发的便利与健壮，但同时需要文档说明操作流程。

命令目录: `{bundle}/Commands`

###＃系统命令

命令可以通过基础控制台管理进行展示: 

```php
php bin/console 
```

程序展示所有内置的所有命令。

```php
asset:
 ➜ asset:install
bundle:
 ➜ bundle:generate
config:
 ➜ config:cache
db:
 ➜ db:revert
 ➜ db:update
production:
 ➜ production:init
route:
 ➜ route:cache
 ➜ route:dump
```

系统框架命令存在于 `fastd/framework` 中，源代码可以直接通过安装组件进行查看。

### ＃自定义命令行

自定义命令行在每个目录 `Commands` 下，而且命令会自动扫描文件进行添加，因为命令在 cli 模式下执行，所以可以更少考虑扫描文件产生的效率问题，应该把问题都集中在业务代码处理上。

```php
<?php

namespace WelcomeBundle\Commands;

use FastD\Console\Command\Command;
use FastD\Console\IO\Input;
use FastD\Console\IO\Output;

class DemoCommand extends Command
{
    /**
     * @return string
     */
    public function getName()
    {
        return 'welcome:bundle';
    }

    /**
     * @return void
     */
    public function configure()
    {
        // TODO: Implement configure() method.
    }

    /**
     * @param Input $input
     * @param Output $output
     * @return int
     */
    public function execute(Input $input, Output $output)
    {
        $output->write('welcome fastd');
    }
}
```