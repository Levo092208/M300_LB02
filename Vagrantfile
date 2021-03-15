# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  
    # Box Settings
    config.vm.box = "ubuntu/bionic64"
    
    
    # Provider Settings
     config.vm.provider "virtualbox" do |vb|
       vb.name = "Vargant-VM-01"
       vb.gui = true
       vb.memory = "4096"
       config.vm.network "public_network"
       
    end
    
  
  
    
    # Folder Settings
    # config.vm.synced_folder "../data", "/vagrant_data"
  
  
     #Provision Settings
     config.vm.provision "shell", inline: <<-SHELL
       apt-get update
       apt-get install -y apache2
       ip addr show
     SHELL
  
      
    #	Startup-Script
    #	config.vm.provision :shell, path: "bootstrap.sh"
    #	end
    
  end