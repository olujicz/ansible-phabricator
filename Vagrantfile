# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "debian/jessie64"
  config.vm.network :private_network, ip: "192.168.33.15"
  config.vm.provider :virtualbox do |virtualbox|
      virtualbox.name = "phabricator"
      virtualbox.customize ["modifyvm", :id, "--memory", 512]
  end
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provision/site.yml"
    ansible.host_key_checking = false
    ansible.groups = {
      "vm" => ["default"],
    }
  end
end
