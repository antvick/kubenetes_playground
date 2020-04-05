# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
     vb.memory = "1024"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/site.yml"
  end
end
