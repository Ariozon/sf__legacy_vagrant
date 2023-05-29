# B10.5 Using Vagrant to run old code

# -*- mode: ruby -*-
# vi: set ft=ruby :
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
	config.vm.box = "ubuntu/bionic64"
  config.vm.provision "shell", inline: <<-SHELL
    # Update the package list
    apt-get update
    # Install PostgreSQL 8.4
    apt-get install -y postgresql-8.4
  SHELL
end
