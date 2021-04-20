# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2004"
  config.ssh.insert_key = false
  config.ssh.username = "vagrant"
  config.vm.network "private_network", ip: "192.168.50.2"
  config.vm.hostname = "wordpress"
  config.vm.synced_folder ".", "/vagrant"
  config.vm.provider "virtualbox" do |vb|
    vb.name = "wordpress"
    vb.gui = false
    vb.memory = 1024
    vb.linked_clone = false
  end

config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "wordpress.yaml"
    #ansible.install_mode = "pip"
    #ansible.pip_install_cmd = "sudo apt-get install -y python3-distutils && curl -s https://bootstrap.pypa.io/get-pip.py | sudo python3"
    #ansible.verbose="v"
    ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3.8" }
 end

end
