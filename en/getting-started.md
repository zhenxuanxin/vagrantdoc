# GETTING STARTED #
The Vagrant getting started guide will walk you through your first Vagrant project, and show off the basics of the major features Vagrant has to offer.

If you're curious what benefits Vagrant has to offer, you should also read the ["Why Vagrant?"][why-vagrant] page.

The getting started guide will use Vagrant with [VirtualBox][virtualbox], since it is free, available on every major platform, and built-in to Vagrant. After reading the guide though, don't forget that Vagrant can work with [many other providers][providers].

Before diving into your first project, please [install the latest version of Vagrant][installation]. And because we'll be using [VirtualBox][virtualbox] as our provider for the getting started guide, please install that as well.

> More of a book person? If you prefer to read a physical book, you may be interested in [Vagrant: Up and Running][book] , written by the author of Vagrant and published by O'Reilly.

## UP AND RUNNING ##
```
$ vagrant init hashicorp/precise32
$ vagrant up
```
After running the above two commands, you'll have a fully running virtual machine in [VirtualBox][virtualbox] running Ubuntu 12.04 LTS 32-bit. You can SSH into this machine with `vagrant ssh`, and when you're done playing around, you can remove all traces of it with `vagrant destroy`.

Now imagine every project you've ever worked on being this easy to set up.

With Vagrant, `vagrant up` is all you need to work on any project, to install every dependency that project needs, and to set up any networking and synced folders so you can continue working from the comfort of your own machine.

The rest of this guide will walk you through setting up a more complete project, covering more features of Vagrant.

[why-vagrant]: https://docs.vagrantup.com/v2/why-vagrant/
[virtualbox]: http://www.virtualbox.org/
[providers]: https://docs.vagrantup.com/v2/getting-started/providers.html
[book]: http://www.amazon.com/gp/product/1449335837/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=1449335837&linkCode=as2&tag=vagrant-20
[installation]: https://docs.vagrantup.com/v2/installation/