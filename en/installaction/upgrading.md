
# Upgrading Vagrant
If you're upgrading from Vagrant 1.0.x, please read the specific page dedicated to that. This page covers upgrading Vagrant in general during the 1.x series.

Upgrades of Vagrant during the 1.x release series are straightforward: download the new package, install it over the existing package. The installers will properly remove old files, and Linux package managers should do the same thing.

Note that Vagrantfile stability for the new Vagrantfile syntax is not promised until 2.0 final. So while Vagrantfiles made for 1.0.x will continue to work, newer Vagrantfiles may have backwards incompatible changes until 2.0 final.

> Run into troubles upgrading? Please report an issue if you run into problems upgrading. Upgrades are meant to be a smooth process and we consider it a bug if it wasn't.