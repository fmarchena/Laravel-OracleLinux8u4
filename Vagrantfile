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
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "oraclelinux/8"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "https://oracle.github.io/vagrant-projects/boxes/oraclelinux/8.json"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
   config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
   #config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.C:\Francisco\MaquinasV\Paquetes
   
   config.vm.synced_folder "Paquetes", "/home/vagrant/Paquetes" 

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
    config.vm.provision "shell", inline: <<-SHELL
        dnf install httpd -y
	    systemctl enable --now httpd.service
		cd /home/vagrant/Paquetes
	 
		sudo   	yum -y install curl 
		yum install -y  zip unzip
		sudo dnf install -y php-common-7.4.6-4.module+el8.3.0+7685+72d70b58.x86_64.rpm
		udo dnf install -y  php-7.4.6-4.module+el8.3.0+7685+72d70b58.x86_64.rpm
		
		sudo dnf install -y php-gd-7.4.6-4.module+el8.3.0+7685+72d70b58.x86_64.rpm
		
		sudo dnf install -y php-mbstring-7.4.6-4.module+el8.3.0+7685+72d70b58.x86_64.rpm
		
	sudo dnf install -y 	php-pecl-zip-1.18.2-1.module+el8.3.0+7685+72d70b58.x86_64.rpm
sudo dnf install -y php-pdo-7.4.6-4.module+el8.3.0+7685+72d70b58.x86_64.rpm

sudo dnf install -y php-cli-7.4.6-4.module+el8.3.0+7685+72d70b58.x86_64.rpm
sudo dnf install -y php-json-7.4.6-4.module+el8.3.0+7685+72d70b58.x86_64.rpm
sudo dnf install -y php-xml-7.4.6-4.module+el8.3.0+7685+72d70b58.x86_64.rpm
 sudo dnf install -y libzip-1.5.1-2.module+el8.1.0+5433+f869f572.x86_64.rpm
 
		sudo systemctl restart httpd.service
		curl -sS https://getcomposer.org/installer | php
		sudo mv composer.phar /usr/bin/composer
		chmod +x /usr/bin/composer
		cd /var/www
		composer create-project --prefer-dist laravel/laravel blog "5.5.*"
	 
	   

   SHELL
 

end
