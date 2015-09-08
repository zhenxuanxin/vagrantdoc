# PACKAGE 
**Command:** `vagrant package`

This packages a currently running VirtualBox environment into a re-usable [box][box]. This command cannot be used with any other [provider][provider]. A future version of Vagrant will address packaging boxes for other providers. Until then, they must be made by hand.

## OPTIONS ##

* `--base NAME` - Instead of packaging a VirtualBox machine that Vagrant manages, this will package a VirtualBox machine that VirtualBox manages. `NAME` should be the name or UUID of the machine from the VirtualBox GUI.

* `--output NAME` - The resulting package will be saved as `NAME`. By default, it will be saved as `package.box`.

* `--include x,y,z` - Additional files will be packaged with the box. These can be used by a packaged Vagrantfile (documented below) to perform additional tasks.

* `--vagrantfile FILE` - Packages a Vagrantfile with the box, that is loaded as part of the [Vagrantfile load order][load-order] when the resulting box is used.

> **A common misconception** is that the `--vagrantfile` option will package a Vagrantfile that is used when `vagrant init` is used with this box. This is not the case. Instead, a Vagrantfile is loaded and read as part of the Vagrant load process when the box is used. For more information, read about the [Vagrantfile load order][load-order].

[box]: https://docs.vagrantup.com/v2/boxes.html
[provider]: https://docs.vagrantup.com/v2/providers/
[load-order]: https://docs.vagrantup.com/v2/vagrantfile/#load-order