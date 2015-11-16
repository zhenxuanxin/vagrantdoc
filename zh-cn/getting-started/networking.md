
# 网络
在这个节点上，我们有了一个Web服务器在运行并且我们可以从我们的主机上修改文件而这些文件自动的同步到客户机上。然而简单地通过终端从客户机里面访问Web页面不是最令人满意的。在这个步骤中，我们会使用Vagrant的网络特性提供给我们附加的选项来从我们自己的主机上访问客户机。

## 端口转发
一个选项是使用*端口转发*。端口转发允许你指定客户机的端口来共享一个主机的端口。这允许你访问你自己主机的一个端口，但实际上所有的网络通信都是转发到客户机指定的端口上的。

让我们配置一个我们可以访问客户机中Apache的转发的端口。你只需要做的就是编辑Vagrantfile，让它看起来像这样：
```
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/precise32"
  config.vm.provision :shell, path: "bootstrap.sh"
  config.vm.network :forwarded_port, guest: 80, host: 4567
end
```
运行`vagrant reload`或`vagrant up`（取决于机器是否在运行）来让这些修改生效。

当机器再次运行起来的时候，在你的浏览器中载入`http://127.0.0.1:4567`。你可以看到一个Web页面，它是从虚拟机中服务出来的。

## 其他网络
Vagrant还有其他的网络选项，允许你给客户机分配静态IP地址，或者是将客户机桥接到现有的网络中。如果你对其他的选项感兴趣，请阅读[网络][1]页面。

[1]: /networking/