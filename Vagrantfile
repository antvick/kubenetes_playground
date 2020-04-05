# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  BOX = "centos/7"
  MEMORY = "1024"

  config.vm.define "master" do |master|
    master.vm.box = BOX
    master.vm.hostname = "master"
    master.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", MEMORY]
      vb.customize ["modifyvm", :id, "--cpus", "1"]
    end
  end

  config.vm.define "node" do |node|
    node.vm.box = BOX
    node.vm.hostname = "node"
    node.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", MEMORY]
      vb.customize ["modifyvm", :id, "--cpus", "1"]
    end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/site.yml"
  end
end
