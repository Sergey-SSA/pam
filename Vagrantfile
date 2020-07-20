# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip: "192.168.9.2"
  config.vm.box_check_update = false

  config.vm.provision "shell", inline: <<-Shell
    sudo cp /vagrant/time.conf /etc/security/time.conf
    sudo cp /vagrant/login /etc/pam.d/login
  Shell
end
