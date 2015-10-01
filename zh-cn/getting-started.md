
# 入门指南

Vagrant 入门指南将指引你开始你的第一个Vagrant项目，并向你展示许多Vagrant提供的主要的基础功能。

如果你好奇Vagrant给你带来的好处，你就需要阅读["Why Vagrant?"][1]章节。

入门指南将和[VirtualBox][2]一起使用Vagrant，它是自由的，并且在主流平台都可用。在阅读指南后，别忘了Vagrant也可以在许多其他[提供者][3]上工作。.

在进入你的第一个项目之前，请[安装Vagrant的最新版][5]。因为在这个入门指南中我们将要使用[VirtualBox][2]作为我们的提供者，若以也请把它也安装好。

> 想要阅读更多的书籍？如果你喜欢阅读实体书本，你可能对[Vagrant: Up and Running][4]感兴趣，它是Vagrant的作者编写的，由O'Reilly出版。

## 启动和运行 ##
```
$ vagrant init hashicorp/precise32
$ vagrant up
```
运行上面两行代码之后，在[VirtualBox][2]中你就有一个完整的虚拟机了，它运行的是Ubuntu 12.04 LTS 32-bit版本的系统。你可以使用`vagrant ssh`通过SSH进入到机器中，如果你玩够了，你可以通过`vagrant destroy`来移除它的所有的信息。

现在想象一下，你曾经工作上的每一个项目都可以像这样简单的设置。

任何项目中，只要有了Vagrant，你的工作是`vagrant up`，安装项目需要的依赖，设置网络和同步目录，所以你可以在你自己的机器上舒服的继续工作了。

本指南的其余部分将引导你设置一个更完整的项目，涵盖Vagrant的更多功能。

[1]: https://docs.vagrantup.com/v2/why-vagrant/
[2]: http://www.virtualbox.org/
[3]: https://docs.vagrantup.com/v2/getting-started/providers.html
[4]: http://www.amazon.com/gp/product/1449335837/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=1449335837&linkCode=as2&tag=vagrant-20
[5]: https://docs.vagrantup.com/v2/installation/