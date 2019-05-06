# -*- mode: ruby -*-
# vi: set ft=ruby :

#Comenzamos la configuración de la máquina
Vagrant.configure("2") do |config|
#Definimos la máquina que vamos a utilizar
  config.vm.box = "ubuntu/trusty64"
#Declaramos el tipo de conexión y IPs	
  config.vm.network "private_network", ip: "10.0.0.1"
#Creamos las linias que se van a ejecutar, podemos añadir el SW 
#y comandos de configuración que vayamos a utilizar.
#También podemos generar un script con todo a ejecutar dentro y declarar la ruta en inline:
#app.vm.provision ”shell”, path: ”provision.sh”
  config.vm.provision "shell", inline: <<-SHELL	
	sudo apt-get update
	sudo apt-get install -y nginx
SHELL
end
