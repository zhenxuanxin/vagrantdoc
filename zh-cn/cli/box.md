
# Box
**命令:** `vagrant box`

用于管理（添加，移除，等等）[盒子][1]的命令。

这个命令的主要功能是通过更多的自命令的：

* add
* list
* outdated
* remove
* repackage
* update

## Box Add
**命令:** `vagrant box add ADDRESS`

这会将指定地址处的盒子添加到Vagrant。地址可以是如下三种之一：

* 来自[公共目录][2]的镜像速记名，例如“hashicorp/precise64”。

* 文件路径或者[hashicorp目录][2]的HTTP URL。若是HTTP URL，基础是支持`http_proxy`环境变量的。当然了HTTPS也是支持的。

* 一个盒子文件的直接URL。这种情况，你必须指定一个`name`标记（如下所示）并且版本控制和更新是不能工作的。

如果在下载或者使用Ctrl-C中断了下载的时候产生了错误，在下次请求的时候Vagrant会尝试恢复下载。Vagrant会只尝试下载那些初始下载六小时内的下载。

### 选项
* `--box-version VALUE` - 指定你想添加的盒子的版本。默认的，罪行版本会被添加。值可以为准确的版本号，如“1.2.3”或者一个条件的版本集合。版本条件可以像这样“>= 1.0, < 2.0”。

* `--cacert CERTFILE` - 指定CA用于验证连接的证书。可用于远程端点没使用标准根CA的情况。

* `--capath CERTDIR` - 指定CA用于验证连接的证书的目录。可用于远点没有使用标准跟CA的情况。

* `--cert CERTFILE` - 当下载盒子的时候如果需要，指定客户端证书。

* `--clean` - 如果有此参数，Vagrant会移除任何之前相同URL下载的旧的缓存文件。这主要用于当你不想从上次下载点恢复，可能内容变更了的情况。

* `--force` - 当提出此参数，盒子会被下载下来覆盖掉任何存在的相同名字的盒子。

* `--insecure` - 当提出此参数，即使URL是HTTPS的URL，SSL证书也不会被验证。

* `--provider` PROVIDER - 如果给出此参数，Vagrant会用给出的提供者验证你准备添加的盒子。默认的，Vagrant会自动命中使用合适的提供者。

### 直接盒子文件的选项
下列选项在你添加直接盒子的时候（当你没有使用目录的时候）可用。

* `--checksum VALUE` - 指明下载的盒子校验和。如果指定了，Vagrant会将实际下载的盒子的校验和与给出值进行比较的，如果校验和不符合，会给出一个错误。非常建议盒子文件是非常大的情况。如果你是从目录下载的，校验和是包含在目录入口中的。

* `--checksum-type TYPE` - 如果指定了`--checksum`，就是校验和的类型。目前支持的值由“md5”，“sha1”和“sha256”。

* `--name VALUE` - 盒子的逻辑名称。这个名字是你想放在你的Vagrantfile中`config.vm.box`的值。当从目录添加一个盒子的时候，名字是包含在目录入口中的，不必指定。

> **来自HashiCorp's Atlas的盒子和版本控制的盒子的校验和：** 来自的盒子，校验和是嵌在盒子的元数据中的。元数据自己是通过TLS服务并且它的格式是有效的。

## Box List
**命令:** `vagrant box list`

这个命令会列出所有已经安装到Vagrant的盒子。

## Box Outdated
**命令:** vagrant box outdated

这个命令会告诉你当前使用的Vagrant环境是不是已经过期了的。如果输入了`--global`标志，所有已安装的盒子都会被检查更新。

检查更新牵涉到刷新关联到盒子的元数据。这通常需要互联网连接。

### 选项
* `--global` - 检查更新所有已安装盒子。而不仅只是当前的Vagrant环境。

## Box Remove
**命令:** `vagrant box remove NAME`

这个命令会从Vagrant移除符合给出名字的盒子。

如果盒子是多个提供者的。必须通过`--provider`标志指定准确的提供者。如果一个盒子有多个版本，你可以通过`--box-version`标志选中一个版本。

### 选项
* `--box-version VALUE` - 指定需要移除的盒子的版本条件。查阅文档中`box add`命令关于此标志的详细信息。

* `--force` - 强制移除活动的Vagrant环境正在使用的盒子。

* `--provider VALUE` - 使用给出的名字指定要移除的盒子的提供者。仅在该盒子后面是多个提供者的时候使用这个标志。如果只是单提供者，Vagrant会默认的移除它。

## Box Repackage
**命令:** `vagrant box repackage NAME PROVIDER VERSION`

这个命令会对给定的盒子进行重新打包，并把它丢到当前目录，所以你可以再分发它。名字，提供者和版本可以通过使用`vagrant box list`获得。

如果你添加一个盒子，Vagrant会在内部对它进行解包并保存。原始的`*.box`文件不会被保存。这个命令在从已安装Vagrant盒子中再生一个`*.box`文件时候非常有用。

## Box Update
**命令:** `vagrant box update`

这个命令会在当前Vagrant环境有可用更新的时候将其更新。这个命令只需要指定`--box`标志就也可以更新一个特殊的盒子（在活跃Vagrant环境之外的）。

注意，更新盒子不会更新正在运行的Vagrant机器。要反射盒子的更新，你不得不销毁掉再恢复Vagrant机器。

如果你只想检查它有没有可用更新，使用`vagrant box outdated`命令。

### 选项
* `--box VALUE` - 指定需要更新的盒子的名字。如果这个标志没有指定，Vagrant会更新活跃的Vagrant环境的盒子。

* `--provider VALUE` - 当有`--box`的时候，这会控制指定的提供者的盒子进行更新。只有当盒子是有多提供者的时候着才是必须的。没有`--box`标志，这是没效的。

[1]: /boxes
[2]: https://atlas.hashicorp.com/boxes/search

