# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian-7.5.0-x86_64"
  config.vm.box_url = "ftp://ftp.lugons.org/vagrant/debian-7.5.0-x86_64.box"

  config.vm.define :phabricator, primary: true do |phabricator|
    phabricator.vm.network :private_network, ip: "192.168.33.15"

    phabricator.vm.provider :virtualbox do |v|
    v.name = "phabricator"
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--memory", 512]
    v.customize ["modifyvm", :id, "--cpus", 1]
    v.customize ["modifyvm", :id, "--name", "Phabricator"]
    end

    phabricator.vm.provision :ansible do |ansible|
      ansible.inventory_path = "debian/hosts"
      ansible.playbook = "debian/site.yml"
    end
  end
end
