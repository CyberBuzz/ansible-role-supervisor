# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "bento/centos-7.1"
  config.vm.network "private_network", type: "dhcp"
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--paravirtprovider", "kvm"]
    v.linked_clone = true if Vagrant::VERSION =~ /^1.8/
  end
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "tests/playbook.yml"
    ansible.sudo = true
    ansible.extra_vars = {
    }
  end
end
