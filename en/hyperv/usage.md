
# Usage

The Hyper-V provider is used just like any other provider. Please read the general [basic usage][basic-usage] page for providers.

The value to use for the `--provider` flag is `hyperv`.

Hyper-V also requires that you execute Vagrant with administrative privileges. Creating and managing virtual machines with Hyper-V requires admin rights. Vagrant will show you an error if it doesn't have the proper permissions.

Boxes for Hyper-V can be easily found on [HashiCorp's Atlas][hashicorp]. To get started, you might want to try the `hashicorp/precise64` box.

[basic-usage]: https://docs.vagrantup.com/v2/providers/basic_usage.html
[hashicorp]: https://atlas.hashicorp.com/boxes/search