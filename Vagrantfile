# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  
  # Box Settings
  config.vm.box = "ubuntu/bionic64"
  
  
  # Provider Settings
   config.vm.provider "virtualbox" do |vb|
     vb.name = "Plex-VM"
     vb.gui = true
     vb.memory = "4096"
     config.vm.network "public_network", ip: "192.168.1.101", guest:80, host:8080, auto_correct: true
     
  end
  


  
  # Folder Settings
  # config.vm.synced_folder "../data", "/vagrant_data"


   #Provision Settings
   
     config.vm.provision "shell", inline: <<-SHELL
       apt-get update 
       apt-get upgrade -y
       wget https://downloads.plex.tv/plex-media-server-new/1.19.3.2843-e3c1f7bcd/debian/plexmediaserver_1.19.3.2843-e3c1f7bcd_amd64.deb
       sudo dpkg -i plexmediaserver_1.19.3.2843-e3c1f7bcd_amd64.deb 
       systemctl enable plexmediaserver.service
       systemctl restart plexmediaserver.service
       systemctl start plexmediaserver.service
       systemctl status plexmediaserver.service
       sudo ufw allow 32400/tcp
       sudo ufw allow ssh
       sudo ufw status  
       sudo ufw enable 
       

      
     SHELL
  
      
    #	Startup-Script
    #	config.vm.provision :shell, path: "bootstrap.sh"
    #	end
    
  end