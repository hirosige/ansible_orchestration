# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.3"
    # Ansible Server
    config.vm.define "ansible_srv" do |atomic|
       atomic.vm.hostname = "ansible.arms-asia.com"
       atomic.vm.synced_folder ".", "/vagrant", disabled: true
       atomic.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2222
       atomic.vm.network "private_network", ip: "192.168.33.10", virtualbox__intnet: "intra"
    end

    # MHMT Server1
    config.vm.define "mhmt_srv" do |atomic|
       atomic.vm.hostname = "mhmt1.arms-asia.com"
       atomic.vm.synced_folder ".", "/vagrant", disabled: true
       atomic.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2223
       atomic.vm.network "private_network", ip: "192.168.33.101", virtualbox__intnet: "intra"
    end

    # MHMT Server2 (dont need on production)
    config.vm.define "mhmt_srv" do |atomic|
       atomic.vm.hostname = "mhmt2.arms-asia.com"
       atomic.vm.synced_folder ".", "/vagrant", disabled: true
       atomic.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2224
       atomic.vm.network "private_network", ip: "192.168.33.102", virtualbox__intnet: "intra"
    end
end
