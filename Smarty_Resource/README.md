## smarty resource

smarty根据文件的不同类型有不同的resource类去处理它。
比如；

    php -> Smarty_Internal_Resource_PHP
    tpl -> Smarty_Internal_Resource_File

**smarty是如何知道访问的资源是什么资源？**

    $smarty->display('file:xxxx.tpl');

如上，使用某一个文件时指定其资源类型`<resource type>:<resource path>`
如果是file类型的默认就不用写了。

    $smarty->display('xxxx.tpl');

这样，就可以自定义资源了。

比如`Smarty_Resource_Fis`就是利用这个特性。

**为什么实现一个FIS资源类？**

1. 解决页面tpl资源定位问题，可以使用map.json查询tpl路径。

    ```smarty
    $smarty->display('fis:ns:page/index.tpl'); //fis:<ID>
    ```

2. 在模板渲染开始初始化ResourceApi，给环境注册国际化资源。
