
# Plugin Development: Packaging & Distribution

This page documents how to organize the file structure of your plugin and distribute it so that it is installable using [standard installation methods][usage]. Prior to reading this, you should be familiar with the [plugin development basics][development-basics].

> **Warning: Advanced Topic!** Developing plugins is an advanced topic that only experienced Vagrant users who are reasonably comfortable with Ruby should approach.

## Example Plugin

The best way to describe packaging and distribution is to look at how another plugin does it. The best example plugin available for this is [vagrant-aws][vagrant-aws].

By using [Bundler][bundler] and Rake, building a new vagrant-aws package is easy. By simply calling `rake package`, a `gem` file is dropped into the directory. By calling `rake release`, the gem is built and it is uploaded to the central [RubyGems][rubygems] repository so that it can be installed using `vagrant plugin install`.

Your plugin can and should be this easy, too, since you basically get this for free by using Bundler.

## Setting Up Your Project

To setup your project, run `bundle gem vagrant-my-plugin`. This will create a `vagrant-my-plugin` directory that has the initial layout to be a RubyGem.

You should modify the `vagrant-my-plugin.gemspec` file to add any dependencies and change any metadata. View the [vagrant-aws.gemspec][vagrant-aws.gemspec] for a good example.

> **Do not depend on Vagrant** for your gem. Vagrant is no longer distributed as a gem, and you can assume that it will always be available when your plugin is installed.

Once the directory structure for a RubyGem is setup, you'll want to modify your Gemfile. Here is the basic structure of a Gemfile for Vagrant plugin development:
```
source "https://rubygems.org"

group :development do
  gem "vagrant", git: "https://github.com/mitchellh/vagrant.git"
end

group :plugins do
  gem "my-vagrant-plugin", path: "."
end
```
This Gemfile gets "vagrant" for development. This allows you to `bundle exec vagrant` to run Vagrant with your plugin already loaded, so that you can test it manually that way.

The only thing about this Gemfile that may stand out as odd is the "plugins" group and putting your plugin in that group. Because `vagrant plugin` commands don't work in development, this is how you "install" your plugin into Vagrant. Vagrant will automatically load any gems listed in the "plugins" group. Note that this also allows you to add multiple plugins to Vagrant for development, if your plugin works with another plugin.

Next, create a `Rakefile` that has at the very least, the following contents:
```
require 'rubygems'
require 'bundler/setup'
Bundler::GemHelper.install_tasks
```
If you run `rake -T` now, which lists all the available rake tasks, you should see that you have the `package` and `release` tasks. You can now develop your plugin and build it!

You can view the [vagrant-aws Rakefile][rakefile] for a more comprehensive example that includes testing.

## Testing Your Plugin

To manually test your plugin during development, use `bundle exec vagrant` to execute Vagrant with your plugin loaded (thanks to the Gemfile setup we did earlier).

For automated testing, the [vagrant-spec][vagrant-spec] project provides helpers for both unit and acceptance testing plugins. See the giant README for that project for a detailed description of how to integrate vagrant-spec into your project. Vagrant itself (and all of its core plugins) use vagrant-spec for automated testing.

[usage]: https://docs.vagrantup.com/v2/plugins/usage.html
[development-basics]: https://docs.vagrantup.com/v2/plugins/development-basics.html
[vagrant-aws]: https://docs.vagrantup.com/v2/plugins/development-basics.html
[bundler]: http://gembundler.com/
[rubygems]: http://rubygems.org/
[vagrant-aws.gemspec]: https://github.com/mitchellh/vagrant-aws/blob/master/vagrant-aws.gemspec
[rakefile]: https://github.com/mitchellh/vagrant-aws/blob/master/Rakefile
[vagrant-spec]: https://github.com/mitchellh/vagrant-spec
