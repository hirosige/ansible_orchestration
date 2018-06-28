# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.3"
    # Ansible Server
    config.vm.define "ansible_srv" do |ansible|
       ansible.vm.hostname = "ansible.arms-asia.com"
       ansible.vm.synced_folder ".", "/vagrant"
       ansible.vm.network "private_network", ip: "192.168.33.10"

       ansible.vbguest.auto_update = false
    end

    # MHMT Server1
    config.vm.define "mhmt_srv" do |mhmt1|
       mhmt1.vm.hostname = "mhmt1.arms-asia.com"
       mhmt1.vm.synced_folder ".", "/vagrant", disabled: true
       mhmt1.vm.network "private_network", ip: "192.168.33.101"

       mhmt1.vbguest.auto_update = false
    end

    # MHMT Server2 (dont need on production)
    config.vm.define "mhmt_srv2" do |mhmt2|
       mhmt2.vm.hostname = "mhmt2.arms-asia.com"
       mhmt2.vm.synced_folder ".", "/vagrant", disabled: true
       mhmt2.vm.network "private_network", ip: "192.168.33.102"

       mhmt2.vbguest.auto_update = false
    end
end
