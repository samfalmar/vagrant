  GNU nano 2.9.3                                                            Vagrantfile                                                                       

# -*- mode: ruby -*-
# vi: set ft=ruby :

#Comenzamos la configuración de la máquina
Vagrant.configure("2") do |config|

#Definimos la máquina que vamos a utilizar
  config.vm.box = "ubuntu/trusty64"

#Declaramos el tipo de conexión y IPs   
  config.vm.network "private_network", ip: "10.0.0.5"

#Creamos las linias que se van a ejecutar, podemos añadir el SW y comandos de configuración que vayamos a utilizar.
#También podemos generar un script con todo a ejecutar dentro y declarar la ruta en inline: app.vm.provision ”shell”, path: ”provision.sh”
  config.vm.provision "shell", inline: <<-SHELL
        sudo apt-get -y update && sudo apt-get -y upgrade
        sudo apt-get -y install apache2
        sudo apt-get -y install php5 php5-curl php5-cli php5-mysql php5-gd mysql-client

#Instalación de MysqlServer
        sudo debconf-set-selections <<< 'mysql-server/root_password password ausias38'
        sudo debconf-set-selections <<< 'mysql-server/root_password_again password ausias38'
        sudo apt-get -y install mysql-server

#Instalación de dependencias de php
        sudo apt-get install php5 php5-curl php5-cli php5-mysql php5-gd mysql-client

#Instalación de adminer
        sudo mkdir /usr/share/adminer
        sudo wget "http://www.adminer.org/latest.php" -O /usr/share/adminer/latest.php
        sudo ln -s /usr/share/adminer/latest.php /usr/share/adminer/adminer.php
        echo "Alias /adminer.php /usr/share/adminer/adminer.php" | sudo tee /etc/apache2/conf-available/adminer.conf
        sudo a2enconf adminer.conf
        sudo service apache2 restart

SHELL
end
