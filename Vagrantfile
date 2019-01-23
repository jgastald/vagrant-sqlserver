# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrant virtual environments for SQL Server 2017 on Ubuntu Linux

Vagrant.configure(2) do |config|
  
  config.vm.box = "ubuntu/bionic64"
  
  config.vm.box_check_update = false

  config.vm.provider "virtualbox" do |vb, override|
#    vb.name = "vagrant-mssql"
    vb.memory = "1924"
    vb.cpus = 2
    # Do not use official Ubuntu box, broken in many ways https://bugs.launchpad.net/cloud-images/+bug/1569237
#    override.vm.box = "bento/ubuntu-16.04"
    override.vm.network "private_network", type: "dhcp"
    override.vm.network :forwarded_port, host: 2433, guest: 1433  # SQLServer
  end

  scripts = [ "bootstrap.sh" ]
  scripts.each { |script|
    config.vm.provision :shell, privileged: false, :path => "./" << script
  }
01
