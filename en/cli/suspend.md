# SUSPEND #
**Command:** `vagrant suspend`

This suspends the guest machine Vagrant is managing, rather than fully [shutting it down][halt] or [destroying][destory] it.

A suspend effectively saves the exact point-in-time state of the machine, so that when you resume it later, it begins running immediately from that point, rather than doing a full boot.

This generally requires extra disk space to store all the contents of the RAM within your guest machine, but the machine no longer consumes the RAM of your host machine or CPU cycles while it is suspended.

[halt]: https://docs.vagrantup.com/v2/cli/halt.html
[destory]: https://docs.vagrantup.com/v2/cli/destroy.html