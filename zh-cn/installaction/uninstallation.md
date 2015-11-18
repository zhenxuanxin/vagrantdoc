
# 卸载 Vagrant
卸载Vagrant是简单和直截了当的。你可以卸载Vagrant二进制文件，用户数据中的任何一个，后者所有。这节文章的下面覆盖了在所有平台上如何执行这个操作。

## 移除Vagrant程序
移除Vagrant程序会移除`vagrant`二进制文件以及你机器的所有依赖。卸载完程序之后，你也可以使用标砖的方式来[重新安装][1]。

在**Windows**上，使用控制面板中的添加/移除程序来卸载。

在**Mac OS X**上，移除`/Applications/Vagrant`目录以及`/usr/bin/vagrant`文件。并执行`sudo pkgutil --forget com.vagrant.vagrant`来让OS X忘记Vagrant之前安装过。

在**Linux**上，移除`/opt/vagrant`和`/usr/bin/vagrant`文件。

## 移除用户数据
移除用户数据会移除所有的[盒子][2]，[插件][3]，以及其他已存储状态的但可能继续使用的Vagrant。移除用户数据的效果会让下次的Vagrant认为它是一次全新的安装。

在每种平台上，移除`~/.vagrant.d`目录以删除用户数据。

运行着的Vagrant会自动重新生成一些必要的数据以保持运行，所以任何时候移除用户数据都是安全的。

[1]: /installation/
[2]: /boxes/
[3]: /plugins/