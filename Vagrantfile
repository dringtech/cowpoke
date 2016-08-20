# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"

  # Was getting repeated "Warning: Authentication failure. Retrying..."
  config.ssh.insert_key = false # Workaround?

  config.vm.provider "virtualbox" do |v|
    v.linked_clone = true if Vagrant::VERSION =~ /^1.8/
    v.cpus = 2
    v.memory = 2048
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.provision "docker" do |d|
    d.pull_images "rancher/server:latest"
    d.pull_images "rancher/agent:latest"
    d.run "rancher/server", args: "-p 8080:8080"
  end
end
