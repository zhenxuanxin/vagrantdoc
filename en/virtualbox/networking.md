
# Networking
## VirtualBox Internal Network

The VirtualBox provider supports using the private network as a VirtualBox internal network. By default, private networks are host-only networks, because those are the easiest to work with. However, internal networks can be enabled as well.

To specify a private network as an [internal network][network-internal] for VirtualBox use the `virtualbox__intnet` option with the network. The `virtualbox__` (double underscore) prefix tells Vagrant that this option is only for the VirtualBox provider.
```
Vagrant.configure("2") do |config|
  config.vm.network "private_network", ip: "192.168.50.4",
    virtualbox__intnet: true
end
```
Additionally, if you want to specify that the VirtualBox provider join a specific internal network, specify the name of the internal network:
```
Vagrant.configure("2") do |config|
  config.vm.network "private_network", ip: "192.168.50.4",
    virtualbox__intnet: "mynetwork"
end
```

## VirtualBox NIC Type

You can specify a specific nictype for the created network interface by using the `nictype` parameter. This isn't prefixed by `virtualbox__` for legacy reasons, but is VirtualBox-specific.

This is an advanced option and should only be used if you know what you're using, since it can cause the network device to not work at all.

Example:
```
Vagrant.configure("2") do |config|
  config.vm.network "private_network", ip: "192.168.50.4",
    nictype: "virtio"
end
```

[network-internal]: https://www.virtualbox.org/manual/ch06.html#network_internal