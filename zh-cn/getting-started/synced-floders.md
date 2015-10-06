
# 同步目录
如此简单的就能创建好一个虚拟机是很酷的事情，但大多人并不希望仅通过基于终端的SSH使用纯文本编辑器编辑文件。幸运的是，有了Vagrant，你就没必要那样了。使用*同步目录*，Vagrant会自动同步你的文件到客户机。

默认地，Vagrant会共享你的项目目录（记住，是有Vagrantfile文件的那个目录）到客户机的`/vagrant`目录下。重新运行`vagrant up`并通过SSH进入你的主机后，可以看到：
```
$ vagrant up
...
$ vagrant ssh
...
vagrant@precise32:~$ ls /vagrant
Vagrantfile
```
不管你信不信，你在虚拟机里面看到的Vagrantfile文件就是你真实主机上的Vagrantfile。我们继续并创建一个文件来向你证明它：
```
vagrant@precise32:~$ touch /vagrant/foo
vagrant@precise32:~$ exit
$ ls
foo Vagrantfile
```
哇！"foo"现在在你的主机上了。正如你看到的那样，Vagrant会保证目录同步。

通过[同步目录][1]，你可以在你的主机上继续使用你自己的编辑器，并且所欲的文件自动同步到客户机上。

[synced-folders]: http://docs.vagrantup.com/v2/synced-folders/