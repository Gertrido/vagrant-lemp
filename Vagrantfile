# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "ubuntu"

  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.synced_folder "../development", "/app", type: "nfs"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "advertising"
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt install software-properties-common
    apt-add-repository ppa:ansible/ansible
    apt update
    apt install ansible -y
  SHELL
end
