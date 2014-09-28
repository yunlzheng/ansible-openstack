# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.define "controller" do |controller|
    controller.vm.box = "ubuntu/trusty64"

    controller.vm.network "private_network", ip: "10.1.0.11"
    controller.vm.provision "ansible" do |ansible|
      ansible.playbook = "controller.yml"
    end

    controller.vm.provider "virtualbox" do |vbox|
      vbox.memory = 2048
    end

  end

  config.vm.define "network" do |network|
    network.vm.box = "ubuntu/trusty64"
    network.vm.network "private_network", ip: "10.1.0.21"
    network.vm.provision "ansible" do |ansible|
      ansible.playbook = "network.yml"
    end

    network.vm.provider "virtualbox" do |vbox|
      vbox.memory = 512
    end

  end

  config.vm.define "compute1" do |compute1|
    compute1.vm.box = "ubuntu/trusty64"
    compute1.vm.network "private_network", ip: "10.1.0.31"
    compute1.vm.provision "ansible" do |ansible|
      ansible.playbook = "compute.yml"
    end

    compute1.vm.provider "virtualbox" do |vbox|
      vbox.memory = 4096
    end

  end

  config.vm.define "block1" do |compute1|
    compute1.vm.box = "ubuntu/trusty64"
    compute1.vm.network "private_network", ip: "10.1.0.41"
    compute1.vm.provision "ansible" do |ansible|
      ansible.playbook = "block.yml"
    end
    compute1.vm.provider "virtualbox" do |vbox|
      vbox.customize ["createhd",
                        '--filename', "tmp/disk",
                        '--size', "2000" ]
      vbox.customize ['storageattach', :id,
                       '--storagectl', 'SATAController',
                       '--port', 1,
                       '--device', 0,
                       '--type', 'hdd',
                       '--medium', "tmp/disk.vdi"]
    end
  end

end
