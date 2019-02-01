# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-18.04"

  config.vm.hostname = "magento.localhost"

  config.vm.network "private_network", ip: "192.168.22.65"
  config.vm.network :forwarded_port, guest: 80, host: 8000

  config.vm.provider :virtualbox do |vb|
            vb.name = "magento23"
  end

  config.ssh.forward_agent = true

  config.vm.synced_folder ".", "/vagrant",
    id: "core",
    :nfs => true,
    :mount_options => ['nolock,vers=3,udp,noatime,actimeo=2,fsc']

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end


  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "/vagrant/ansible/development.yml"
    ansible.verbose = true
  end

end
