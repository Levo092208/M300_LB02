# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  
    # Box Settings
    config.vm.box = "ubuntu/bionic64"
    
    
    # Provider Settings
     config.vm.provider "virtualbox" do |vb|
       vb.name = "Vargant-Plex-VM-01"
       vb.gui = true
       vb.memory = "4096"
    end
  
  
    # Network Settings
    # config.vm.network "forwarded_port", guest: 80, host: 8080
    # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
    # config.vm.network "private_network", ip: "192.168.33.10"
    # config.vm.network "public_network"
  
    
    # Folder Settings
    # config.vm.synced_folder "../data", "/vagrant_data"
  
  
    # Provision Settings
    # config.vm.provision "shell", inline: <<-SHELL
    #   apt-get update
    #   apt-get install -y apache2
    # SHELL
  
      
    #	Startup-Script
    #	config.vm.provision :shell, path: "bootstrap.sh"
    #	end
    
  end