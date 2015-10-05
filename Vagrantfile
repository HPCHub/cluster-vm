# -*- mode: ruby -*-
# vi: set ft=ruby :

$bootstrap = <<SCRIPT
yum install -y epel-release
yum install -y ansible
yum install -y ruby
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "puphpet/centos65-x64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
  end
  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.provision "shell", inline: $bootstrap
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/cluster-node.yml"
    ansible.sudo = true
    #ansible.verbose = 'vvv'
    #ansible.tags = 'jsub'
  end  
end
