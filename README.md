# Debian 7.6.0 [Packer](http://www.packer.io/) template

This template buils a VirtualBox image based on Debian Wheezy 7.6.0. The VM is
configured to use 512 MB of RAM and 1 CPU. Those settings, as many others, can
be changed in the `debian-7.6.0-wheezy.json` file.

## Usage
1. Be sure you have Packer and [VirtualBox](https://www.virtualbox.org/)
installed in your system.
2. Clone this repository and go into it.
    * `git clone git@github.com:jose-lpa/packer-debian_7.6.0.git`
    * `cd packer-debian_7.6.0.git`
3. Run Packer to build the VM.
    * `packer build debian-7.6.0-wheezy.json`

A VM box file should be created in the working directory under the name
`packer_virtualbox-iso_virtualbox.box`.

### Running the built VM
You can now use [Vagrant](https://www.vagrantup.com/) to run it by creating a
`Vagrantfile` with this content:

```ruby
# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "debian-7.6.0"
  config.vm.box_url = "file://packer_virtualbox-iso_virtualbox.box"
end
```

And leverage and access the VM as usual with Vagrant:
    `vagrant up`
    `vagrant ssh`

## Credits
Based in the nice template written by [Tech-Angels](https://github.com/tech-angels/packer-templates).
