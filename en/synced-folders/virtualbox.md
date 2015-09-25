
# VirtualBox

If you're using the VirtualBox [provider][providers], then VirtualBox shared folders are the default synced folder type. These synced folders use the VirtualBox shared folder system to sync file changes from the guest to the host and vice versa.
Caveats

There is a [VirtualBox bug][bug] related to `sendfile` which can result in corrupted or non-updating files. You should deactivate `sendfile` in any web servers you may be running.

In Nginx:
```
sendfile off;
```
In Apache:
```
EnableSendfile Off
```

[providers]: https://docs.vagrantup.com/v2/providers/
[bug]: https://github.com/mitchellh/vagrant/issues/351#issuecomment-1339640