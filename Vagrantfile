# -*- mode: ruby -*-
# vi: set ft=ruby :

$inst_ansible = <<SCRIPT
yum install -y epel-release
yum install -y ansible
yum install -y ruby
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "puphpet/centos65-x64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
  end

  config.vm.provision "shell", inline: $inst_ansible
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/cluster-node.yml"
    ansible.sudo = true
    #ansible.verbose = 'vvv'
  end  
end
