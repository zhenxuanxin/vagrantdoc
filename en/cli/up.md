# UP #
**Command:** `vagrant up`

This command creates and configures guest machines according to your [Vagrantfile][vagrantfile].

This is the single most important command in Vagrant, since it is how any Vagrant machine is created. Anyone using Vagrant must use this command on a day-to-day basis.

## OPTIONS ##

* `--[no-]destroy-on-error` - Destroy the newly created machine if a fatal, unexpected error occurs. This will only happen on the first `vagrant up`. By default this is set.

* `--[no-]parallel` - Bring multiple machines up in parallel if the provider supports it. Please consult the provider documentation to see if this feature is supported.

* `--provider x` - Bring the machine up with the given [provider][providers]. By default this is "virtualbox".

* `--provision` - Force the provisioners to run.

* `--provision-with x,y,z` - This will only run the given provisioners. For example, if you have a `:shell` and `:chef_solo` provisioner and run `vagrant provision --provision-with shell`, only the shell provisioner will be run.

[vagrantfile]: https://docs.vagrantup.com/v2/vagrantfile/
[providers]: https://docs.vagrantup.com/v2/providers/
