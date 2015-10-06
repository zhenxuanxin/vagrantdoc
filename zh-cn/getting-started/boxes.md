
# 盒子
不像通过scratch构建虚拟机那样慢和沉闷，Vagrant使用一个基础镜像来快速的克隆一个虚拟机。基础镜像就是Vagrant中的盒子，而在创建了新的Vagrantfile文件之后指定你Vagrant环境使用的盒子就是你的首要任务了。

## 安装一个盒子
如果你参照[新手入门概览][1]页面运行了那些命令，那你就已经安装好了一个盒子，不需要再运行下面这些命令了。不论怎样，最好也认真阅读这一节，这样你可以了解到更多关于如何管理盒子的内容。

使用`vagrant box add`就会把盒子添加到Vagrant。这会使用指定的名字来保存盒子，所以多个Vagrant环境也可以很好的复用。如果你还没有添加盒子，那现在敲下面这行命令吧。
```
$ vagrant box add hashicorp/precise32
```
这会从[HashiCorp's Atlas box catalog][2]下载名为"hashicorp/precise32"的盒子，它是一个你可以查找和托管盒子的地方。This will download the box named  from , a place where you can find and host boxes. 虽然可以从HashiCorp's Atlas轻松的下载盒子，你也可以从本地文件，自定义URL或者其他的地方添加盒子。

添加好的盒子可以在多个项目中重复使用。每个项目都将盒子作为一个初始镜像进行克隆，并不会修改实际的基础镜像。这意味着如果你有两个项目都使用我们之前添加的`hashicorp/precise32`盒子，在一个客户机中添加文件并不会影响到其他的机器。

## 使用盒子Using A Box
现在盒子已经添加到Vagrant中了，我们要开始配置我们的项目使用它作为一个基础。打开并`Vagrantfile`修改内容为如下所示：
```
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/precise32"
end
```
在这个实例中，"hashicorp/precise32"必须和你之前添加盒子时使用的名字保持一致。这样才知道使用哪一个盒子。如果还没有添加盒子，在运行的时候Vagrant会自动下载并添加它。

在下一个环节中，我们将启动Vagrant环境，并有一点和它的交互。

## 查找更多的盒子
这个新手入门指南剩余的部分，我们都只使用我们之前添加的"hashicorp/precise32"盒子。但一会儿完成这个新手入门指南后，你第一个可能的问题就是“我该去哪儿找更多的盒子呢？”

查找更多盒子的最好的地方就是[HashiCorp's Atlas box catalog][2]. HashiCorp's Atlas有一个公共的目录含有大量的可以在各种各样的平台和技术下运行的盒子。HashiCorp's Atlas也有一个很棒的搜索功能可以满足你查找你关心的盒子。

为了可以查找免费的盒子，HashiCorp's Atlas允许你托管你自己的盒子，同样的，如果你计划为你们的组织创建盒子也是允许的。

[1]: http://docs.vagrantup.com/v2/getting-started/
[2]: https://atlas.hashicorp.com/boxes/search