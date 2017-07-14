# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

    #config.vm.box = "ubuntu/xenial64"

    config.vm.box = "bento/ubuntu-16.04"
    config.ssh.insert_key = false
#    config.vbguest.auto_update = true
    config.vm.box_check_update = true

    config.vm.define :"docker-registry" do |server|
        server.vm.network :private_network, ip: "172.20.30.12"
        server.vm.network "forwarded_port", guest: 80, host: 4321
        server.vm.provider :virtualbox do |v|
            v.name = "docker-registry"
            v.memory = "4096"
        end
    end

    config.vm.provision :ansible do |ansible|
        ansible.playbook = "provision/main.yml"
#        ansible.inventory_file = "provision/hosts"
        ansible.sudo = true
    end

end