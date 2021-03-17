# Dokuementation M300 LB02 Plex Meda Server 
## M300 TBZ


>Vagrant File
>

    Vagrant.configure("2") do |config|
  
        # Box Settings
        config.vm.box = "generic/ubuntu2004"
  
    # Provider Settings
        config.vm.provider "virtualbox" do |vb|
        vb.name = "Plex-VM-M300-LB02"
        vb.gui = true
        vb.memory = "4096"
     
    end
  
    config.vm.network "forwarded_port", guest: 32400, host: 32400
    config.vm.network "forwarded_port", guest: 80, host: 8080

    # Folder Settings
    # config.vm.synced_folder "../data", "/vagrant_data"

    #Provision Settings
   
        config.vm.provision "shell", inline: <<-SHELL
        apt-get update
        apt-get upgrade -y
     
        wget https://downloads.plex.tv/plex-media-server-new/1.22.0.4163-d8c4875dd/debian/plexmediaserver_1.22.0.4163-d8c4875dd_amd64.deb
     
        sudo dpkg -i plexmediaserver_1.22.0.4163-d8c4875dd_amd64.deb
     
        sudo systemctl enable plexmediaserver.service
        sudo systemctl start plexmediaserver.service
        sudo systemctl status plexmediaserver.service
     
     
        SHELL
    
    end





>Code Dokumentation:

> <span style="color:blue">config.vm.box = "generic/ubuntu2004"</span>
>> Hier wird definiert, welches Image für die VM verwendet werden soll.
>
> <span style="color:blue">config.vm.provider "virtualbox" do |vb|</span>
>> Es wird definiert, welcher Provider verwendet wird.In diesem Fall wird Virtualbox definiert
>
> <span style="color:blue">vb.name = "Plex-VM-M300-LB02"</span>
>> Der Name der VM wird hier definiert
>> * <span style="color:red">Es sollte darauf geachtet werden, dass es nicht schon eine VM mit diesem Namen gibt</span>
>
> <span style="color:blue">vb.gui = true"</span>
>> Hier kann man definieren, ob die VM ein GUI haben soll. Wenn man kein GUI möchte sollte man es auf "false" setzen
>
> <span style="color:blue">vb.memory = "4096"</span>
>> Hier wird definiert, wie viel Arbeitsspeicher die VM haben soll
>> * <span style="color:red">Man kann auch noch zusätzliche Dinge definieren, wie z.B. die Anzahl an Prozessorkernen</span>
>
> <span style="color:blue">config.vm.network "forwarded_port", guest: 32400, host: 32400</span>
> 
> <span style="color:blue">config.vm.network "forwarded_port", guest: 80, host: 8080</span>
>>Damit man später auf die VM zugreifen kann, muss man Ports definieren, welche offen sind. Da man auf den Plex Server über 32400 zugreifft, muss man diesen öffnen
>
> <span style="color:blue">config.vm.provision "shell", inline: <<-SHELL</span>
>>Nach dieser Zeile wird angegeben, was nach dem Start der VM ausgeführt werden soll
>> * <span style="color:red">Mann kann die Befehle auch direkt in ein Script schreiben, welches dann nach dem Starten ausgeführt wird</span>
## Installation vom Plex-Media Server
            apt-get update
            apt-get upgrade -y
     
            wget https://downloads.plex.tv/plex-media-server-new/1.22.0.4163-d8c4875dd/debian/plexmediaserver_1.22.0.4163-d8c4875dd_amd64.deb
     
            sudo dpkg -i plexmediaserver_1.22.0.4163-d8c4875dd_amd64.deb
     
            sudo systemctl enable plexmediaserver.service
            sudo systemctl start plexmediaserver.service
            sudo systemctl status plexmediaserver.service
### Installation vom plex-Media Server 
>Als erstes werden Updates gemacht, damit die VM aktuell ist
>
>Anschliessend wird das .deb File welches für die Installation benötig wird heruntergeladen und anschliessend installiert
>
>Anschliessend wird der Service "Plexmediaserver" aktiviert und gestartet
>
>Mit dem Befehl "Status plexmediaserver.service" wird dann noch getestet, ob der Service am laufen ist.