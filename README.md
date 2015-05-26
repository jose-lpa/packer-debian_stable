# Debian 8.0 Jessie [Packer](http://www.packer.io/) template

This template builds a VirtualBox image based on Debian Jessie 8.0. The VM is
configured to use 512 MB of RAM and 1 CPU. Those settings, as many others, can
be changed in the `debian-8.0-jessie.json` file.

## Usage
1. Be sure you have Packer and [VirtualBox](https://www.virtualbox.org/)
installed in your system.
2. Clone this repository and go into it.
    * `git clone git@github.com:jose-lpa/packer-debian_stable.git`
    * `cd packer-debian_stable`
3. Run Packer to build the VM.
    * `packer build debian-8.0-jessie.json`

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
  config.vm.box = "debian-8.0"
  config.vm.box_url = "file://packer_virtualbox-iso_virtualbox.box"
end
```

And leverage and access the VM as usual with Vagrant:
    `vagrant up`
    `vagrant ssh`

## Credits
Based on the nice template written by [Tech-Angels](https://github.com/tech-angels/packer-templates).
