
# Providers
In this getting started guide, your project was always backed with [VirtualBox][virtualbox]. But Vagrant can work with a wide variety of backend providers, such as [VMware][vmware], AWS[aws], and more. Read the page of each provider for more information on how to set them up.

Once you have a provider installed, you don't need to make any modifications to your Vagrantfile, just `vagrant up` with the proper provider and Vagrant will do the rest:
```
$ vagrant up --provider=vmware_fusion
...
```
Ready to move that to the cloud? Take it to AWS:
```
$ vagrant up --provider=aws
...
```
Once you run `vagrant up` with another provider, every other Vagrant command doesn't need to be told what provider to use. Vagrant can automatically figure it out. So when you're ready to SSH or destroy or anything else, just run the commands like normal, such as `vagrant destroy`. No extra flags necessary.

For more information on providers, read the full documentation on [providers][providers].

[virtualbox]: http://www.virtualbox.org/
[vmware]: http://docs.vagrantup.com/v2/vmware/
[aws]: http://github.com/mitchellh/vagrant-aws
[providers]: http://docs.vagrantup.com/v2/providers/