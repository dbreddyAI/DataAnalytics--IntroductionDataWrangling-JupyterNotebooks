# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  # alternatives to this Ubuntu 18.04 box are "v0rtex/xenial64" with the 16.04 LTS and ubuntu/trusty64 with 14.04 LTS
  config.vm.box = "bento/ubuntu-18.04" 
  # access a port on your host machine (via localhost) and have all data forwarded to a port on the guest machine.
  config.vm.network "forwarded_port", guest: 9092, host: 9192
  config.vm.network "forwarded_port", guest: 4040, host: 5050
  config.vm.network "forwarded_port", guest: 8080, host: 8180
  # Create a private network, which allows host-only access to the machine
  # using a specific IP - I have arbitrarily decided on 192.168.188.144. Feel free to change this
  config.vm.network "private_network", ip: "192.168.188.144"

  # define a larger than default (40GB) disksize
  # note: this requires the Vagrant plugin vagrant-disksize (see https://github.com/sprotheroe/vagrant-disksize) using "vagrant plugin install vagrant-disksize"
  # config.disksize.size = '50GB'
  
  config.vm.provider "virtualbox" do |vb|
    vb.name = 'ubuntu1804-docker-vm'
    vb.memory = 4096
    vb.cpus = 1
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  # set up Docker in the new VM:
  config.vm.provision :docker
  # install docker-compose into the VM 
  # note: this next line requires a plugin to be installed - using "vagrant plugin install vagrant-docker-compose"
  # config.vm.provision :docker_compose
  # install docker-compose into the VM and run the docker-compose.yml file in the local directory - if it exists -  whenever the  VM starts (https://github.com/leighmcculloch/vagrant-docker-compose)
  # config.vm.provision :docker_compose, yml: "/vagrant/docker-compose.yml", run:"always"
	
end