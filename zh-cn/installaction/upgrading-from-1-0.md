
# 从Vagrant 1.0.x升级
从1.0.x到1.x的升级是直截了当的。Vagrant 1.0.x中的Vagrant是很[向后兼容][1]的，所以你可以简单的在你前一次安装之上重新安装下载的最新的包。并使用你操作系统标准的流程来安装它。

就像[向后兼容][1]页面说的那样，**Vagrant 1.0.x的插件不能再Vagrant1.1+上工作**。许多插件已经得到更新以适用于新版的Vagrant。所以你可以看到如果它们是被更新了的，否则，你可以在升级前移除它们。

建议你在升级前移除所有的插件。然后少少的把插件加回来。这通常会得到一个平滑的升级过程。

**然而**，如果你的Vagrant是通过RubyGems安装的，你必须在安装最新版Vagrant之前使用`gem uninstall`卸载老版本。基于RubyGems的安装方式已经被移除了。

[1]: https://docs.vagrantup.com/v2/installation/backwards-compatibility.html