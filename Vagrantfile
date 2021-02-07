# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
  
  # Box settings
  config.vm.box = "ubuntu/bionic64"

  # # Provider settings
  # config.vm.provider "virtualbox" do |vb|
  #  vb.memory = "2048"
  #  vb.cpus = 2
  # end
  servers=[
    {
      :hostname => "ansible-control",
      :box => "ubuntu/bionic64",
      :ip => "192.168.33.10",
      :ssh_port => '2280'
    },
    { 
      :hostname => "web01",
      :box => "ubuntu/bionic64",
      :ip => "192.168.33.11",
      :ssh_port => '2281'
    },
    {
      :hostname => "db01",
      :box => "ubuntu/bionic64",
      :ip => "192.168.33.12",
      :ssh_port => '2282'
    },
    {  
      :hostname => "loadbalancer",
      :box => "ubuntu/bionic64",
      :ip => "192.168.33.13",
      :ssh_port => '2283'
    },
  ]

  servers.each do |virtualbox|
    config.vm.define virtualbox[:hostname] do |node|
      node.vm.box = virtualbox[:box]
      node.vm.hostname = virtualbox[:hostname]

      node.vm.network :private_network, ip: virtualbox[:ip]
      node.vm.network "forwarded_port", guest: 22, host: virtualbox[:ssh_port], id: "ssh"
    end



  # Network setting
  # config.vm.box_check_update = false
  # config.vm.network "forwarded_port", guest: 80, host: 8080
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  # config.vm.network "private_network", ip: "192.168.33.10"
  # config.vm.network "public_network"

  # Folder settings
  # config.vm.synced_folder "../data", "/vagrant_data", :mount_options => ["dmode=700", "fmode=666"]

  
  # Provision settings
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
  end
end
