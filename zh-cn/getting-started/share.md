
# 共享
现在我们有一个Web服务器在运行并且可以从你自己的机器上访问到它，这样我们就有了一个功能相当的开发环境了。但为了提供一个开发环境，Vagrant也让共享和在这些环境上协作很容易。实现这些最主要的特性叫做[Vagrant 共享][1].

Vagrant共享让你共享你的Vagrant环境给世界上的任何人。它会给你一个URL，而这个URL会直接地将世界上任何连接到互联网的设备路由到你的Vagrant环境。

## 登录到Hashicorp's Atlas
在可以共享你的Vagrant环境之前，你需要一个[HashiCorp's Atlas][2]账户，别担心，免费的。

等你有了一个账户之后，使用`vagrant login`进行登录：
```
$ vagrant login
Username or Email: mitchellh
Password (will be hidden):
You're now logged in!
```

## 共享
等你登录之后，运行`vagrant share`：
```
$ vagrant share
...
==> default: Your Vagrant Share is running!
==> default: URL: http://frosty-weasel-0857.vagrantshare.com
...
```
别尝试上面的URL，你的URL应该是不一样的。取而代之的是，复制`vagrant share`输出的URL，在一个Web浏览器中访问它。它会加载我们之前设置的Apache页面。

如果你修改了你共享目录中的文件并刷新URL，你会看到它更新了！URL是直接路由到你的Vagrant环境的，并且世界上任何连接到互联网的设备都能看到。

要结束共享会话，在终端中按住`Ctrl+C`。你可以再刷新URL来验证你的环境，可以看到已经不是共享的了。

Vagrant共享比简单的HTTP共享强大得多。要了解更多详情，查阅[完整的Vagrant共享文档][1].

[1]: http://docs.vagrantup.com/v2/share/
[2]: https://atlas.hashicorp.com/
