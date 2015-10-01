
# Uninstalling Vagrant
Uninstalling Vagrant is easy and straightforward. You can either uninstall the Vagrant binary, the user data, or both. The sections below cover how to do this on every platform.

## Removing The Vagrant Program
Removing the Vagrant program will remove the `vagrant` binary and all dependencies from your machine. After uninstalling the program, you can always [reinstall][reinstall] again using standard methods.

On **Windows**, uninstall using the add/remove programs section of the control panel.

On **Mac OS X**, remove the `/Applications/Vagrant` directory and the `/usr/bin/vagrant` file. Also execute `sudo pkgutil --forget com.vagrant.vagrant` to have OS X forget that Vagrant was ever installed.

On **Linux**, remove the `/opt/vagrant` directory and the `/usr/bin/vagrant` file.

## Removing User Data
Removing the user data will remove all [boxes][boxes], [plugins][plugins], and any stored state that may be used by Vagrant. Removing the user data effectively makes Vagrant think it is once again a fresh install.

On every platform, remove the `~/.vagrant.d` directory to delete the user data.

Running Vagrant will automatically regenerate any data necessary to run, so it is safe to remove the user data at any time.

[reinstall]: https://docs.vagrantup.com/v2/installation/
[boxes]: https://docs.vagrantup.com/v2/boxes.html
[plugins]: https://docs.vagrantup.com/v2/plugins/