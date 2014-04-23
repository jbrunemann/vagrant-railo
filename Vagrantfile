# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version ">= 1.3.5"

Vagrant.configure("2") do |config|

  # for github clones
  config.ssh.forward_agent = true


  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
    v.cpus = 4
  end

  config.vm.box = "hashicorp/precise64"

  config.vm.box_url = "https://vagrantcloud.com/hashicorp/precise64"

 
  config.vm.network "forwarded_port", guest: 80, host: 8880
  config.vm.network "forwarded_port", guest: 8080, host: 8765
  config.vm.network "forwarded_port", guest: 8500, host: 8520

  config.vm.synced_folder "codebase/", "/codebase", group: "www-data"

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "manifests"
    puppet.manifest_file  = "hashicorp/precise64.pp"
  end

end
