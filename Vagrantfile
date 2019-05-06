# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "private_network", ip: "10.0.0.1"
  config.vm.provision "shell", inline: <<-SHELL	
	sudo apt-get update
	sudo apt-get install -y nginx
SHELL
end
