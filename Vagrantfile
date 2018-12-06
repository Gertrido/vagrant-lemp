# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "ubuntu"

  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 8000, host: 8081

  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.synced_folder "../development", "/app", type: "nfs"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "socialcalendar"
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt install software-properties-common
    apt-add-repository ppa:ansible/ansible
    apt update
    apt install ansible -y
    cd /vagrant
    ansible-playbook install-components.yml
  SHELL
end
