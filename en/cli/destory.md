
# Destroy
**Command:** `vagrant destroy`

This command stops the running machine Vagrant is managing and destroys all resources that were created during the machine creation process. After running this command, your computer should be left at a clean state, as if you never created the guest machine in the first place.

This command usually asks for confirmation before destroying. This confirmation can be skipped by passing in the `-f` or `--force` flag.

### Options
* `-f` or `--force` - Don't ask for confirmation before destroying.
> The `vagrant destroy` command does not remove a box that may have been installed on your computer during `vagrant up`. Thus, even if you run `vagrant destroy`, the box installed in the system will still be present on the hard drive. To return your computer to the state as it was before `vagrant up` command, you need to use `vagrant box remove`. For more information, read about the [vagrant box remove](/v2/cli/box.html) command.