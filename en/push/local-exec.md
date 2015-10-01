
# Vagrant Push
## Local Exec Strategy

The Vagrant Push Local Exec strategy allows the user to invoke an arbitrary shell command or script as part of a push.

> **Warning:** The Vagrant Push Local Exec strategy does not perform any validation on the correctness of the shell script.

The Vagrant Push Local Exec strategy supports the following configuration options:

* `script` - The path to a script on disk (relative to the `Vagrantfile`) to execute. Vagrant will attempt to convert this script to an executable, but an exception will be raised if that fails.
* `inline` - The inline script to execute (as a string).

Please note - only one of the script and inline options may be specified in a single push definition.

## Usage

The Vagrant Push Local Exec strategy is defined in the `Vagrantfile` using the `local-exec` key:

Remote path:
```
config.push.define "local-exec" do |push|
  push.inline = <<-SCRIPT
    scp -r . server:/var/www/website
  SCRIPT
end
```
Local path:
```
config.push.define "local-exec" do |push|
  push.inline = <<-SCRIPT
    cp -r . /var/www/website
  SCRIPT
end
```
For more complicated scripts, you may store them in a separate file and read them from the `Vagrantfile` like so:
```
config.push.define "local-exec" do |push|
  push.script = "my-script.sh"
end
```
And then invoke the push with Vagrant:
```
$ vagrant push
```
