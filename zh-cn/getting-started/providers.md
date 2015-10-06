
# 提供者
在本新手入门指南中，你的项目由[VirtualBox][1]支持。但Vagrant也可以在各种各样的后台支持者中工作。如[VMware][2]，AWS[3]，以及更多。阅读每个提供者的页面获取更多关于如何设置它们的信息。

当你有一个提供者安装好了，你就不需要对你的Vagrantfile进行任何的修改，只需要运行`vagrant up`并加上特定的提供者，然后Vagrant会完成重置工作：
```
$ vagrant up --provider=vmware_fusion
...
```
准备好移到云上了？带它到AWS：
```
$ vagrant up --provider=aws
...
```
当你使用另一个提供者运行`vagrant up`之后，所有其他Vagrant命令都不需要指定使用了哪一个提供者。Vagrant会自动解决它。所以你如果准备执行SSH、销毁或者其他任何操作的时候，只需要像平常那样运行命令就行了。例如`vagrant destroy`。不需要额外的标记。 No extra flags necessary.

要了解更多关于提供者的信息，阅读[提供者][4]完整的文档。

[1]: http://www.virtualbox.org/
[2]: http://docs.vagrantup.com/v2/vmware/
[3]: http://github.com/mitchellh/vagrant-aws
[4]: http://docs.vagrantup.com/v2/providers/