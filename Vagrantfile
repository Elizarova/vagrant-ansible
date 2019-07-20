# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "node" do |node|
	  node.vm.box = "ubuntu/xenial64"
	  
	  node.vm.hostname = "dev-node"
	  node.vm.network "private_network", ip: "192.168.10.101"
	  
	  # for windows
    # node.vm.synced_folder ".", "/vagrant", type: "nfs"
   
	  node.vm.provision "ansible_local" do |ansible|
	    ansible.galaxy_roles_path = 'tmp/galaxy_roles'
		  ansible.galaxy_role_file = 'ansible/requirements.yml'
		  ansible.playbook = "ansible/playbook.yml"
		  ansible.verbose = "v"			
	  end
  
	  node.vm.provider "virtualbox" do |vb|
		  vb.memory = 2048
		  vb.cpus = 2
	  end  	  
	end
end
