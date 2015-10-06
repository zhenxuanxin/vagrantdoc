
# 准备
好了，我们已经有一个运行着Ubuntu的虚拟机并且我们可以在自己的主机上编辑文件，而这些文件会同步到虚拟机中去。让我们通过Web服务器让这些文件开始工作吧。

我们可以仅仅通过SSH进入主机然后安装一个Web服务器作为我们的办法，但那样做的话，每个使用Vagrant的人都必须做相同的事情。代替的办法是，Vagrant内置了*自动准备*的支持。使用这个特性，Vagrant可以在你`vagrant up`的时候自动安装软件，所以客户机可以重复的创建并ready-to-use。

## 安装 Apache
在我们的基础项目中我们仅使用一个Shell脚本来安装[Apache][1]。创建如下的Shell脚本把它保存为`bootstrap.sh`并放入到和Vagrantfile相同的目录中：
```
#!/usr/bin/env bash

apt-get update
apt-get install -y apache2
if ! [ -L /var/www ]; then
  rm -rf /var/www
  ln -fs /vagrant /var/www
fi
```
接下来，我们配置Vagrant在配置我们机器的时候运行这个Shell脚本。我们将通过编辑Vagrantfile来实现，你的文件应该看起来像这样：
```
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/precise32"
  config.vm.provision :shell, path: "bootstrap.sh"
end
```
"provision"行是新的，它告诉Vagrant使用`shell`准备者和`bootstrap.sh`文件来设置这台机器。文件的路径是相对于项目的根目录（就是Vagrantfile文件所在的那个目录）。

## 准备! 
做好所有的配置之后，就运行`vagrant up`来创建你的机器吧，Vagrant会自动的准备它.你应该会从终端中看到Shell脚本的输出。如果客户机是已经运行过之前的配置的，那就运行`vagrant reload --provision`，这回快速的重启你的虚拟机，并跳过初始导入的步骤。provision标记在重载命令中会通知Vagrant去运行它的准备者，通常Vagrant只会在第一次运行`vagrant up`的时候执行这个操作。

等到Vagrant运行完了之后，Web服务器就安装好并开始运行了。但你暂时还不能从你自己的浏览器中看到你的站点，但你可以通过SSH中执行如下命令来验证上述的装备工作是正常的：
```
$ vagrant ssh
...
vagrant@precise32:~$ wget -qO- 127.0.0.1
```
这是正常工作的因为在上述Shell脚本中我们安装了Apache并设置它的默认的`DocumentRoot`指向我们的`/vagrant`目录（就是Vagrant默认同步的那个）。

你可以在终端中尽情的玩耍了，例如创建更多的文件和查看他们之类的，但在接下来的步骤中，我们将涉及到网络选项这样你就可以使用你自己的浏览器去访问客户机了。

[1]: http://httpd.apache.org/