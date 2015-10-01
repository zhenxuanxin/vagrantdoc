
# Plugin Development: Host Capabilities

This page documents how to add new capabilities for [hosts][hosts] to Vagrant, allowing Vagrant to perform new actions on specific host operating systems. Prior to reading this, you should be familiar with the [plugin development basics][development-basics].

> **Warning: Advanced Topic!** Developing plugins is an advanced topic that only experienced Vagrant users who are reasonably comfortable with Ruby should approach.

Host capabilities augment [hosts][hosts] by attaching specific "capabilities" to the host, which are actions that can be performed in the context of that host operating system.

The power of capabilities is that plugins can add new capabilities to existing host operating systems without modifying the core of Vagrant. In earlier versions of Vagrant, all the host logic was contained in the core of Vagrant and wasn't easily augmented.

## Definition and Implementation

The definition and implementation of host capabilities is identical to [guest capabilities][guest-capabilities].

The main difference from guest capabilities, however, is that instead of taking a machine as the first argument, all host capabilities take an instance of `Vagrant::Environment` as their first argument.

Access to the environment allows host capabilities to access global state, specific machines, and also allows them to call other host capabilities.

## Calling Capabilities

Since you have access to the environment in every capability, capabilities can also call other host capabilities. This is useful for using the inheritance mechanism of capabilities to potentially ask helpers for more information. For example, the "linux" guest has a "nfs_check_command" capability that returns the command to use to check if NFS is running.

Capabilities on child guests of Linux such as RedHat or Arch use this capability to mostly inherit the Linux behavior, except for this minor detail.

Capabilities can be called like so:
```
environment.host.capability(:capability_name)
```
Any additional arguments given to the method will be passed on to the capability, and the capability will return the value that the actual capability returned.

[hosts]: https://docs.vagrantup.com/v2/plugins/hosts.html
[development-basics]: https://docs.vagrantup.com/v2/plugins/development-basics.html
[guest-capabilities]: https://docs.vagrantup.com/v2/plugins/guest-capabilities.html