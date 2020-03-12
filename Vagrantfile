# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

Vagrant.configure("2") do |config|
  
  config.vm.provision "shell", inline: "echo Master VM"

  config.vm.define "masternode" do |masternode|
    masternode.vm.box = "centos/7"
    masternode.vm.hostname = "masternode.example.com"
    masternode.vm.network "private_network", ip: "172.20.20.100"
    masternode.vm.provider "virtualbox" do |v|
      v.name = "masternode"
      v.memory = 2048
      v.cpus = 2
    end
  end
  
  # Specify how many nodes you wish.
  NodeCount = 2

  (1..NodeCount).each do |i|  
    config.vm.define "node#{i}" do |node|
      node.vm.box = "centos/7"
      node.vm.hostname = "node#{i}.example.com"
      node.vm.network "private_network", ip: "172.20.20.10#{i}"
      node.vm.provider "virtualbox" do |v|
        v.name = "node#{i}"
        v.memory = 1024
        v.cpus = 1
      end
    end
  end
end
