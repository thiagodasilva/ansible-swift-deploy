# -*- mode: ruby -*-
# vi: set ft=ruby :
#

PROXY_NODES = 1
STORAGE_NODES = 4
DISKS = 8

Vagrant.configure("2") do |config|
    config.vm.box = "chef/centos-7.1"
    config.ssh.insert_key = false

    # Make the proxy nodes
    (0..PROXY_NODES-1).each do |i|
        config.vm.define "proxy#{i}" do |proxy|
            proxy.vm.host_name = "proxy"
            proxy.vm.host_name = "proxy#{i}"
            proxy.vm.network :private_network, ip: "192.168.10.90"
            proxy.vm.provider :virtualbox do |vb|
                vb.memory = 1024
                vb.cpus = 2
            end
        end
    end

    # Make the storage nodes, each with DISKS number of drives
    (0..STORAGE_NODES-1).each do |i|
        config.vm.define "storage#{i}" do |storage|
            storage.vm.hostname = "storage#{i}"
            storage.vm.network :private_network, ip: "192.168.10.10#{i}"
            (0..DISKS-1).each do |d|
                storage.vm.provider :virtualbox do |vb|
                    vb.customize [ "createhd", "--filename", "disk-#{i}-#{d}.vdi", "--size", 500*1024 ]
                    vb.customize [ "storageattach", :id, "--storagectl", "SATA Controller", "--port", 3+d, "--device", 0, "--type", "hdd", "--medium", "disk-#{i}-#{d}.vdi" ]
                    vb.memory = 1024
                    vb.cpus = 2
                end
            end

            if i == (STORAGE_NODES-1)
                # View the documentation for the provider you're using for more
                # information on available options.
                storage.vm.provision :ansible do |ansible|
                    ansible.limit = "all"
                    ansible.playbook = "site.yml"
                    ansible.extra_vars = { username: 'vagrant', group: 'vagrant' }
                    ansible.groups = {
                        "swift_storage" => (0..STORAGE_NODES-1).map {|j| "storage#{j}"},
                        "swift_proxy" => (0..PROXY_NODES-1).map {|j| "proxy#{j}"},
                    }
                end
            end
        end

    end
end

