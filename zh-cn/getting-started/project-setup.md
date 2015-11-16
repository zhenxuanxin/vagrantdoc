
# 配置项目
配置Vagrant项目的第一步是创建一个[Vagrantfile][1]。Vagrantfile的用途是如下二者：

1. 标记你项目的根目录。许多Vagrant的配置都是相对于这个根目录的。

2. 描述你的机器的性质和你的项目运行所需要的资源。当然也包括安装软件以及你想要访问的东西。

Vagrant有内置的命令来初始化一个目录，那就是：`vagrant init`。基于这个新手入门指南的目的，请在你的终端中运行：
```
$ mkdir vagrant_getting_started
$ cd vagrant_getting_started
$ vagrant init
```
这会在你当前的目录创建一个`Vagrantfile`。如果你喜欢你可以看看这个文件长什么样，它里面包含有注释和例子，如果它有点intimidating不要感到害怕，我们马上就会修改它了。

在已存在的目录中你也可以运行`vagrant init`来配置已有项目使用Vagrant。

如果你使用了版本控制，那意味着你得把Vagrantfile也提交到你项目的版本控制中。这样做了之后，其他参与这个项目的人就能得到一点好处，那就是不需要那些upfront工作。

[1]: /vagrantfile/