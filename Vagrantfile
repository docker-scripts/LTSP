# -*- mode: ruby -*-
# vi: set ft=ruby :
load "settings.sh"

Vagrant.configure("2") do |config|
  
  config.vm.box = "ubuntu/bionic64"
	
  config.vm.network "public_network", ip: LAN_IP, netmask: "255.255.255.0", bridge: LAN_IF
  
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
    config.vm.network :private_network, ip: "10.0.2.52"
    config.cache.synced_folder_opts = {
      type: :nfs,
      mount_options: ['rw', 'vers=3', 'tcp', 'nolock']
    }
   end
  
  config.vm.provider "virtualbox" do |virtualbox|
	  # Enable promiscuous mode
  	  virtualbox.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
   end
  
  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.memory = "1024"
   end

  config.vm.provision "shell", path: "install.sh"

end

