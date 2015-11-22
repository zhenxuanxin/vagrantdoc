
# 命令行接口
差不多所有的Vangrant交互都是通过命令行接口完成。

可用的接口都是使用`vagrant`命令，并且都是跟随Vagrant安装的时候自动安装好的。`vagrant`命令有许多子命令，例如`vagrant up`，`vagrant destroy`，等等。

如果你运行`vagrant`自己，帮助就会显示，并展示所以可用的子命令。另外，你也可以在运行任何Vagrant命令的时候加上`-h`标志来输出关于这个命令的帮助。例如，尝试运行`vagrant init -h`。帮助会输出一个这个命令的如何工作的一句话简介以及所有的标志和接受的命令。

深入的文档以及各种Vagrant命令的用例可以通过阅读本站左侧导航区域的适当的子节文章获得。

你可能想请教关于用于配置和控制Vagrant的全局环境变量的[文档][1]。

[1]: /other/environmental-variables