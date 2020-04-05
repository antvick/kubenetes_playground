# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  BOX = "centos/7"
  MEMORY = "2048"
  CPU = "4"

  config.vm.define "demo-node" do |node|
    node.vm.box = BOX
    node.vm.hostname = "demo-node"
    node.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", MEMORY]
      vb.customize ["modifyvm", :id, "--cpus", CPU]
    end
    node.vm.network "private_network", ip: "192.200.50.5"
  end

  config.vm.define "demo-master" do |master|
    master.vm.box = BOX
    master.vm.hostname = "demo-master"
    master.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", MEMORY]
      vb.customize ["modifyvm", :id, "--cpus", CPU]
    end
    master.vm.network "private_network", ip: "192.200.50.4"
    master.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/site.yml"
      ansible.limit = 'all' 
      ansible.groups = {
        "master" => ["demo-master"],
        "node"  => ["demo-node"]
      }
    end
  end
end
