# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/xenial64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Forward ports to minecraft
  config.vm.network "forwarded_port", guest: 25565, host: 25565
  config.vm.network "forwarded_port", guest: 25570, host: 25570
  config.vm.network "forwarded_port", guest: 25571, host: 25571
  config.vm.network "forwarded_port", guest: 25572, host: 25572
  config.vm.network "forwarded_port", guest: 25573, host: 25573
  config.vm.network "forwarded_port", guest: 25574, host: 25574

  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true
 
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
    vb.cpus = "2"
  end

  # Start docker containers
  config.vm.provision "docker" do |d|
    d.pull_images "rehf27/bungeecord"
    d.pull_images "nimmis/spigot"
    d.run "rehf27/bungeecord",
      args: "-ti -p 25565:25565 -e EULA=true -v '/vagrant/bungeecord:/bungeecord'"
  end
end
